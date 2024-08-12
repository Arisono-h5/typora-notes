Android消息处理机制(Handler+Looper+Message+MessageQueue)



Android 消息处理机制估计都被写烂了，但是依然还是要写一下，因为Android应用程序是通过消息来驱动的，Android某种意义上也可以说成是一个以消息驱动的系统，UI、事件、生命周期都和消息处理机制息息相关，并且消息处理机制在整个Android知识体系中也是尤其重要，在太多的源码分析的文章讲得比较繁琐，很多人对整个消息处理机制依然是懵懵懂懂，这篇文章通过一些问答的模式结合Android主线程（UI线程）的工作原理来讲解，源码注释很全，还有结合流程图，如果你对Android 消息处理机制还不是很理解，我相信只要你静下心来耐心的看，肯定会有不少的收获的。

# 概述#

------

**1、我们先说下什么是Android消息处理机制？**

消息处理机制本质：**一个线程开启循环模式持续监听并依次处理其他线程给它发的消息。**

简单的说：一个线程开启一个无限循环模式，不断遍历自己的消息列表，如果有消息就挨个拿出来做处理，如果列表没消息，自己就堵塞（相当于wait，让出cpu资源给其他线程），其他线程如果想让该线程做什么事，就往该线程的消息队列插入消息，该线程会不断从队列里拿出消息做处理。

**2、Android消息处理机制的工作原理？**

打个比方：公司类比App

- PM 的主要工作是设计产品，写需求文档，改需求,中途改需求，提测前改需求...
- UI  主要工作是UI设计，交互等。
- RD 工作我就不说了
- CEO 不解释。

公司开创之后（App启动），那么CEO开始干活了（主线程【UI线程】启动），这时候CEO开启了无限循环工作狂模式，自己的公司没办法啊（相当于UI主线程转成`Looper`线程【源码里面有】）CEO招了一名RD（`new Handler 实例`）并把告诉PM和UI,如果你们有什么任务和需求就让RD（`Handler实例`）转告给我（CEO）。RD会把PM和UI的需求（`Message`）一条条记到CEO的备忘录里（`MessageQueue`）。CEO 无限循环的工作就是不断查看备忘录，看有什么任务要做，有任务就从备忘录一条一条拿出任务来，然后交给这一名RD（`Handler 实例`）去处理（毕竟CEO 不会写代码 囧...）。当然如果备忘录都做完了，这时候CEO就会去睡觉（线程堵塞【简单理解成线程wait】，让出CPU资源，让其他线程去执行）。但是这个备忘录有个特殊的功能就是没有任务的时候突然插入第一条任务（从无到有）就会有闹钟功能叫醒CEO起床继续处理备忘录。 整个消息处理机制的工作原理基本就是这样的。后面会有源码分析，你再来结合这个场景，会更好理解一些。

这里先给一张Android消息处理机制流程图和具体执行动画，如果看不懂没事，接着往下看（后面会结合Android UI主线程来讲解），然后结合着图和动画一块看更能理解整个机制的实现原理。

![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202408011009496.webp)



![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202408011009926.webp)

**3、**`Looper`、`Handler`、`MessageQueue`,`Message`**作用和存在的意义？**

- **Looper **
   我们知道一个线程是一段可执行的代码，当可执行代码执行完成后，线程生命周期便会终止，线程就会退出，那么做为App的主线程，如果代码段执行完了会怎样？，那么就会出现App启动后执行一段代码后就自动退出了，这是很不合理的。所以为了防止代码段被执行完，只能在代码中插入一个死循环，那么代码就不会被执行完，然后自动退出，怎么在在代码中插入一个死循环呢？那么`Looper`出现了，在主线程中调用`Looper.prepare()...Looper.loop()`就会变当前线程变成Looper线程（可以先简单理解：无限循环不退出的线程），`Looper.loop()`方法里面有一段死循环的代码，所以主线程会进入`while(true){...}`的代码段跳不出来，但是主线程也不能什么都不做吧？其实所有做的事情都在`while(true){...}`里面做了，主线程会在死循环中不断等其他线程给它发消息（消息包括：Activity启动，生命周期，更新UI，控件事件等），一有消息就根据消息做相应的处理，Looper的另外一部分工作就是在循环代码中会不断从消息队列挨个拿出消息给主线程处理。
- **MessageQueue **
   MessageQueue 存在的原因很简单，就是同一线程在同一时间只能处理一个消息，同一线程代码执行是不具有并发性，所以需要队列来保存消息和安排每个消息的处理顺序。多个其他线程往UI线程发送消息，UI线程必须把这些消息保持到一个列表（它同一时间不能处理那么多任务),然后挨个拿出来处理，这种设计很简单，我们平时写代码其实也经常这么做。每一个Looper线程都会维护这样一个队列，而且仅此一个，这个队列的消息只能由该线程处理。
- **Handler \**
   简单说Handler用于同一个进程的线程间通信。`Looper`让主线程无限循环地从自己的`MessageQueue`拿出消息处理，既然这样我们就知道**处理消息肯定是在主线程中处理的**，那么怎样在其他的线程往主线程的队列里放入消息呢？其实很简单，我们知道在同一进程中线程和线程之间资源是共享的，也就是对于任何变量在任何线程都是可以访问和修改的，只要考虑并发性做好同步就行了，那么只要拿到MessageQueue 的实例，就可以往主线程的MessageQueue放入消息，主线程在轮询的时候就会**在主线程**处理这个消息。那么怎么拿到主线程 MessageQueue的实例，是可以拿到的(在主线程下`mLooper = Looper.myLooper();mQueue = mLooper.mQueue;`),但是Google 为了统一添加消息和消息的回调处理，又专门构建了Handler类，你只要在主线程构建Handler类，那么这个Handler实例就获取主线程MessageQueue实例的引用（获取方式`mLooper = Looper.myLooper();mQueue = mLooper.mQueue;`），Handler 在sendMessage的时候就通过这个引用往消息队列里插入新消息。Handler 的另外一个作用，就是能统一处理消息的回调。这样一个Handler发出消息又确保消息处理也是自己来做，这样的设计非常的赞。具体做法就是在队列里面的Message持有Handler的引用（哪个handler 把它放到队列里，message就持有了这个handler的引用），然后等到主线程轮询到这个message的时候，就来回调我们经常重写的Handler的`handleMessage(Message msg)`方法。
- **Message **
   Message 很简单了，你想让主线程做什么事，总要告诉它吧，总要传递点数据给它吧，Message就是这个载体。

# 源码分析#

------

接下来我们会结合App主线程（UI线程）来讲解，从App启动后一步一步往下走分析整个Android的消息处理机制，首先在ActivityThread类有我们熟悉的main的函数，App启动的代码的入口就在这里，UI线程本来只是一个普通线程，在这里会把UI线程转换成Looper线程，什么是Looper线程，不急往下看就知道了。



```java
public final class ActivityThread {
    public static final void main(String[] args) {
        ......
        Looper.prepareMainLooper();
        ......
        ActivityThread thread = new ActivityThread();
        thread.attach(false);

        if (sMainThreadHandler == null) {    
            sMainThreadHandler = thread.getHandler();
        }
        ......
        Looper.loop();
        ......
    }
}
```

首先执行的是   `Looper.prepareMainLooper()` 我们来看下`Looper`里面的这个方法做了什么？

> 注:看之前先稍微了解下ThreadLocal是什么？
>  **ThreadLocal**： 线程本地存储区（Thread Local Storage，简称为TLS），每个线程都有自己的私有的本地存储区域，不同线程之间彼此不能访问对方的TLS区域。这里线程自己的本地存储区域存放是线程自己的Looper。具体看下ThreadLocal.java 的源码！



```java
public final class Looper {
    // sThreadLocal 是static的变量，可以先简单理解它相当于map，key是线程，value是Looper，
    //那么你只要用当前的线程就能通过sThreadLocal获取当前线程所属的Looper。
    static final ThreadLocal<Looper> sThreadLocal = new ThreadLocal<Looper>();
    //主线程（UI线程）的Looper 单独处理，是static类型的，通过下面的方法getMainLooper() 
    //可以方便的获取主线程的Looper。
    private static Looper sMainLooper; 

    //Looper 所属的线程的消息队列
    final MessageQueue mQueue;
    //Looper 所属的线程
    final Thread mThread;

    public static void prepare() {
        prepare(true);
    }

    private static void prepare(boolean quitAllowed) {
         //如果线程的TLS已有数据，则会抛出异常，一个线程只能有一个Looper，prepare不能重复调用。
        if (sThreadLocal.get() != null) {
            throw new RuntimeException("Only one Looper may be created per thread");
        }
        //往线程的TLS插入数据，简单理解相当于map.put(Thread.currentThread(),new Looper(quitAllowed));
        sThreadLocal.set(new Looper(quitAllowed));
    }

    //实际上是调用  prepare(false)，并然后给sMainLooper赋值。
    public static void prepareMainLooper() {
        prepare(false);
        synchronized (Looper.class) {
            if (sMainLooper != null) {
                throw new IllegalStateException("The main Looper has already been prepared.");
            }
            sMainLooper = myLooper();
        }
    }
    //static 方法，方便获取主线程的Looper.
    public static Looper getMainLooper() {
        synchronized (Looper.class) {
            return sMainLooper;
        }
    }
    
    public static @Nullable Looper myLooper() {
        //具体看ThreadLocal类的源码的get方法，
        //简单理解相当于map.get(Thread.currentThread()) 获取当前线程的Looper
        return sThreadLocal.get();
    }
}
```

看了上面的代码（仔细看下注释），我们发现 `Looper.prepareMainLooper()`做的事件就是new了一个`Looper`实例并放入Looper类下面一个static的`ThreadLocal<Looper> sThreadLocal`静态变量中，同时给sMainLooper赋值,给`sMainLooper`赋值是为了方便通过`Looper.getMainLooper()`快速获取主线程的Looper，`sMainLooper`是主线程的Looper可能获取会比较频繁，避免每次都到 sThreadLocal 去查找获取。

接下来重点是看下`Looper`的构造函数，看看在new Looper的时候做了什么事？



```java
private Looper(boolean quitAllowed) {
        mQueue = new MessageQueue(quitAllowed);
        mThread = Thread.currentThread();
}
```

看到没有，这时候给当前线程创建了消息队列MessageQueue，并且让**Looper持有MessageQueue的引用**。执行完`Looper.prepareMainLooper()` 之后，主线程从普通线程转成一个Looper线程。目前的主线程线程已经有一个Looper对象和一个消息队列mQueue,引用关系如下图：（主线程可以轻松获取它的Looper，主线程的Looper持有主线程消息队列的引用）

![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202408011010902.webp)

具体如何获取主线程的Looper对象和消息列表呢？



```java
//在主线程中执行
mLooper = Looper.myLooper();
mQueue = mLooper.mQueue
//或者
mLooper=Looper.getMainLooper()
```

接下来回到ActivityThread 的main函数，执行完`Looper.prepareMainLooper()` 之后下一句代码是`ActivityThread thread = new ActivityThread();`这句话就是创建一下ActivityThread对象，这边需要注意的时候`ActivityThread`并不是一个线程，它并没有继承Thread，而只是一个普通的类`public final class ActivityThread{...}`ActivityThread的构造函数并没有做什么事只是初始化了资源管理器。



```java
 ActivityThread() {
     mResourcesManager = ResourcesManager.getInstance();
 }
```

接着往下看下一行代码



```java
ActivityThread thread = new ActivityThread();
//建立Binder通道 (创建新线程)
thread.attach(false);
```

`thread.attach(false);`便会创建一个Binder线程（具体是指`ApplicationThread`，该Binder线程会通过想 `Handler`将`Message`发送给主线程，之后讲)。我们之前提到主线程最后会进入无限循环当中，如果没有在进入死循环之前创建其他线程，那么待会谁会给主线程发消息呢？，没错就是在这里创建了这个线程，这个线程会接收来自系统服务发送来的一些事件封装了`Message`并发送给主线程，主线程在无限循环中从队列里拿到这些消息并处理这些消息。（Binder线程发生的消息包括`LAUNCH_ACTIVITY`，`PAUSE_ACTIVITY` 等等）

继续回到mian 函数的下一句代码`Looper.loop()` 那么重点来了，我们来看下`Looper.loop()`的源码：



```java
public static void loop() {
    final Looper me = myLooper();  //获取TLS存储的Looper对象,获取当前线程的Looper 
    if (me == null) {
        throw new RuntimeException("No Looper; Looper.prepare() wasn't called on this thread.");
    }
 
    final MessageQueue queue = me.mQueue;  //获取Looper对象中的消息队列
    ....

    for (;;) { //主线程开启无限循环模式
        Message msg = queue.next(); //获取队列中的下一条消息，可能会线程阻塞
        if (msg == null) { //没有消息，则退出循环，退出消息循环，那么你的程序也就可以退出了
            return;
        }
        ....
        //分发Message，msg.target 是一个Handler对象，哪个Handler把这个Message发到队列里，
        //这个Message会持有这个Handler的引用，并放到自己的target变量中,这样就可以回调我们重写
        //的handler的handleMessage方法。
        msg.target.dispatchMessage(msg);
        ....
        ....
        msg.recycleUnchecked();  //将Message回收到消息池,下次要用的时候不需要重新创建，obtain()就可以了。
    }
}
```

上面的代码，大家具体看下注释，这时候主线程（UI线程）执行到这一步就进入了死循环，不断地去拿消息队列里面的消息出来处理？那么问题来了
 1、UI线程一直在这个循环里跳不出来，主线程不会因为Looper.loop()里的死循环卡死吗，那还怎么执行其他的操作呢？

- 在looper启动后，主线程上执行的任何代码都是被looper从消息队列里取出来执行的。也就是说主线程之后都是通过其他线程给它发消息来实现执行其他操作的。生命周期的回调也是如此的，系统服务ActivityManagerService通过Binder发送IPC调用给APP进程，App进程接到到调用后，通过App进程的Binder线程给主线程的消息队列插入一条消息来实现的。

2、主线程是UI线程和用户交互的线程，优先级应该很高，主线程的死循环一直运行是不是会特别消耗CPU资源吗？App进程的其他线程怎么办？

- 这基本是一个类似生产者消费者的模型，简单说如果在主线程的MessageQueue没有消息时，就会阻塞在loop的queue.next()方法里，这时候主线程会释放CPU资源进入休眠状态，直到有下个消息进来时候就会唤醒主线程，在2.2 版本以前，这套机制是用我们熟悉的线程的wait和notify 来实现的，之后的版本涉及到**Linux pipe/epoll机制**，通过往pipe管道写端写入数据来唤醒主线程工作。原理类似于I/O,读写是堵塞的，不占用CPU资源。

所以上面代码的重点是`queue.next()` 的函数，其他的我们就不多说了，我们来看下`queue.next()`的源码（主要还是看注释）：



```java
Message next() 
       
        final long ptr = mPtr;
        if (ptr == 0) {
            return null;
        }
        int pendingIdleHandlerCount = -1; // -1 only during first iteration

        //nextPollTimeoutMillis 表示nativePollOnce方法需要等待nextPollTimeoutMillis 
        //才会返回
        int nextPollTimeoutMillis = 0;
        for (;;) {
            if (nextPollTimeoutMillis != 0) {
                Binder.flushPendingCommands();
            }
            //读取消息，队里里没有消息有可能会堵塞，两种情况该方法才会返回(代码才能往下执行)
            //一种是等到有消息产生就会返回,
            //另一种是当等了nextPollTimeoutMillis时长后，nativePollOnce也会返回
            nativePollOnce(ptr, nextPollTimeoutMillis);
            //nativePollOnce 返回之后才能往下执行
            synchronized (this) {
                // Try to retrieve the next message.  Return if found.
                final long now = SystemClock.uptimeMillis();
                Message prevMsg = null;
                Message msg = mMessages;
                if (msg != null && msg.target == null) {
                    // 循环找到一条不是异步而且msg.target不为空的message
                    do {
                        prevMsg = msg;
                        msg = msg.next;
                    } while (msg != null && !msg.isAsynchronous());
                }
                if (msg != null) {
                    if (now < msg.when) {
                       // 虽然有消息，但是还没有到运行的时候，像我们经常用的postDelay,
                       //计算出离执行时间还有多久赋值给nextPollTimeoutMillis，
                       //表示nativePollOnce方法要等待nextPollTimeoutMillis时长后返回
                        nextPollTimeoutMillis = (int) Math.min(msg.when - now, Integer.MAX_VALUE);
                    } else {
                        // 获取到消息
                        mBlocked = false;
                       //链表一些操作，获取msg并且删除该节点 
                        if (prevMsg != null) 
                            prevMsg.next = msg.next;
                        } else {
                            mMessages = msg.next;
                        }
                        msg.next = null；
                        msg.markInUse();
                        //返回拿到的消息
                        return msg;
                    }
                } else {
                    //没有消息，nextPollTimeoutMillis复位
                    nextPollTimeoutMillis = -1;
                }
                .....
                .....
              
    }
```

nativePollOnce()很重要，是一个native的函数，在native做了大量的工作，主要涉及到epoll机制的处理（在没有消息处理时阻塞在管道的读端），具体关于native相关的源码本篇文章不涉及，感兴趣的同学可以网上找找，有不少分析得比较深。

分析到这里，从应用启动创建Looper，创建消息队列，到进入loop方法执行无限循环中，那么这一块就告一段落了，主线程已经在死循环里轮询等待消息了，接下来我们就要再看看，系统是怎么发消息给主线程的，主线程是怎么处理这些个消息的？

在准备启动一个Activity的时候，系统服务进程下的`ActivityManagerService`（简称AMS）线程会通过Binder发送IPC调用给APP进程，App进程接到到调用后，通过App进程下的Binder线程最终调用`ActivityThread`类下面的`scheduleLaunchActivity`方法来准备启动Activity，看下scheduleLaunchActivity方法:

> 注：Binder线程：具体是指ApplicationThread，在App进程中接受系统进程传递过来的信息的线程（在主线程进入死循环之前创建了这个线程）。



```java
  //这个方法不是在主线程调用，是Binder线程下调用的
  public final void scheduleLaunchActivity(Intent intent, IBinder token, int ident,
                ActivityInfo info, Configuration curConfig, Configuration overrideConfig,
                CompatibilityInfo compatInfo, String referrer, IVoiceInteractor voiceInteractor,
                int procState, Bundle state, PersistableBundle persistentState,
                List<ResultInfo> pendingResults, List<ReferrerIntent> pendingNewIntents,
                boolean notResumed, boolean isForward, ProfilerInfo profilerInfo) {

            updateProcessState(procState, false);

            ActivityClientRecord r = new ActivityClientRecord();

            r.token = token;
            r.ident = ident;
            r.intent = intent;
            r.referrer = referrer;
            r.voiceInteractor = voiceInteractor;
            r.activityInfo = info;
            r.compatInfo = compatInfo;
            r.state = state;
            r.persistentState = persistentState;

            r.pendingResults = pendingResults;
            r.pendingIntents = pendingNewIntents;

            r.startsNotResumed = notResumed;
            r.isForward = isForward;

            r.profilerInfo = profilerInfo;

            r.overrideConfig = overrideConfig;
            updatePendingConfiguration(curConfig);

            sendMessage(H.LAUNCH_ACTIVITY, r);
  }
```

把启动一些信息封装成`ActivityClientRecord`之后，最后一句调用`sendMessage(H.LAUNCH_ACTIVITY, r);`我们接着往下看:



```java
private void sendMessage(int what, Object obj) {
        sendMessage(what, obj, 0, 0, false);
    }
private void sendMessage(int what, Object obj, int arg1, int arg2, boolean async) {
         Message msg = Message.obtain();
        msg.what = what;
        msg.obj = obj;
        msg.arg1 = arg1;
        msg.arg2 = arg2;
        if (async) {
            msg.setAsynchronous(true);
        }
        mH.sendMessage(msg);
    }
```

看到没有，最后启动Activity的信息都封装一个Message，但是这里有个问题了，之前在分析main函数的时候，完全没给出往主线程消息队列插入消息的方式，这里有了消息，但是怎么发到主线程的消息队列呢？最后一句又是重点`mH.sendMessage(msg);` mH 是什么呢？难道是Handler，我们来看下它是什么东西？
 我们看了下ActivityThread 的成员变量，发现一句初始化的代码



```dart
final H mH = new H();
```

继续往下看H是什么？



```java
public final class ActivityThread{
     ....
     final H mH = new H();
     ....
     private class H extends Handler {
     ....
     ....
     public void handleMessage(Message msg) {
            if (DEBUG_MESSAGES) Slog.v(TAG, ">>> handling: " + codeToString(msg.what));
            switch (msg.what) {
                case LAUNCH_ACTIVITY: {
                    Trace.traceBegin(Trace.TRACE_TAG_ACTIVITY_MANAGER, "activityStart");
                    final ActivityClientRecord r = (ActivityClientRecord) msg.obj;

                    r.packageInfo = getPackageInfoNoCheck(
                            r.activityInfo.applicationInfo, r.compatInfo);
                    handleLaunchActivity(r, null);
                    Trace.traceEnd(Trace.TRACE_TAG_ACTIVITY_MANAGER);
                } break;
                case RELAUNCH_ACTIVITY: {
                    Trace.traceBegin(Trace.TRACE_TAG_ACTIVITY_MANAGER, "activityRestart");
                    ActivityClientRecord r = (ActivityClientRecord)msg.obj;
                    handleRelaunchActivity(r);
                    Trace.traceEnd(Trace.TRACE_TAG_ACTIVITY_MANAGER);
                } break;
                case PAUSE_ACTIVITY:
                    Trace.traceBegin(Trace.TRACE_TAG_ACTIVITY_MANAGER, "activityPause");
                    handlePauseActivity((IBinder)msg.obj, false, (msg.arg1&1) != 0, msg.arg2,
                            (msg.arg1&2) != 0);
                    maybeSnapshot();
                    Trace.traceEnd(Trace.TRACE_TAG_ACTIVITY_MANAGER);
                    break;
                   .....
         }
         .....
         .....
     }
}
```

H 果不出其然是Handler，而且是ActivityThread的内部类，看了一下它的`handleMessage` 方法，`LAUNCH_ACTIVITY`、`PAUSE_ACTIVITY`、`RESUME_ACTIVITY`...好多好多，H 类帮我们处理了好多声明周期的事情。那么再回到`mH.sendMessage(msg)`这句代码上，在Binder线程执行`mH.sendMessage(msg);`，由主线程创建的Handler mH实例发送消息到主线程的消息队列里，消息队列从无到有，主线程堵塞被唤醒，主线程loop拿到消息，并回调`mH`的`handleMessage` 方法处理LAUNCH_ACTIVITY 等消息。从而实现Activity的启动。

讲到这里，基本一个启动流程分析完了，大家可能比较想知道的是 `mH.sendMessage(msg);` 关于Hanlder是怎么把消息发到主线程的消息队列的？我们接下来就讲解下Handler，首先看下Handler的源码！我们先来看看我们经常用的`Handler`的无参构造函数，实际调用的是`Handler(Callback callback, boolean async)`构造函数（看注释）



```java
 public Handler() {
        this(null, false);
 }
 public Handler(Callback callback, boolean async) {
        //不是static 发出可能内存泄露的警告！
        if (FIND_POTENTIAL_LEAKS) {
            final Class<? extends Handler> klass = getClass();
            if ((klass.isAnonymousClass() || klass.isMemberClass() || klass.isLocalClass()) &&
                    (klass.getModifiers() & Modifier.STATIC) == 0) {
                Log.w(TAG, "The following Handler class should be static or leaks might occur: " +
                    klass.getCanonicalName());
            }
        }
        //获取当前线程的Looper，还记得前面讲过 Looper.myLooper()方法了吗？
        //Looper.myLooper()内部实现可以先简单理解成：map.get(Thread.currentThread()) 
        //获取当前线程的Looper
        mLooper = Looper.myLooper();
        if (mLooper == null) {
            //当前线程不是Looper 线程，没有调用Looper.prepare()给线程创建Looper对象
            throw new RuntimeException(
                "Can't create handler inside thread that has not called Looper.prepare()");
        }
        //让Handler 持有当前线程消息队列的引用
        mQueue = mLooper.mQueue;
        //这些callback先不管，主要用于handler的消息发送的回调，优先级是比handlerMessage高，但是不常用
        mCallback = callback;
        mAsynchronous = async;
    }
```

上面的代码说明了下面几个问题：
 1、Handler 对象在哪个线程下构建（Handler的构造函数在哪个线程下调用），那么Handler 就会持有这个线程的Looper引用和这个线程的消息队列的引用。因为持有这个线程的消息队列的引用，意味着这个Handler对象可以在任意其他线程给该线程的消息队列添加消息，也意味着Handler的handlerMessage 肯定也是在该线程执行的。
 2、如果该线程不是Looper线程，在这个线程new Handler 就会报错！
 3、上面两点综合说明了下面一段很常见的代码：把普通线程转成Looper线程的代码，为什么在`Looper.prepare()`和`Looper.loop()`中间要创建`Handler`:



```java
 class LooperThread extends Thread {
       //其他线程可以通过mHandler这个引用给该线程的消息队列添加消息
       public Handler mHandler;
       public void run() {
            Looper.prepare();
            //需要在线程进入死循环之前，创建一个Handler实例供外界线程给自己发消息
            mHandler = new Handler() {
                public void handleMessage(Message msg) {
                    //Handler 对象在这个线程构建，那么handleMessage的方法就在这个线程执行
                }
            };
            Looper.loop();
        }
    }
```

那么接下来，我们接着往下看Handler的`sendMessage(msg)`方法，这个方法也是比较重要的，也比较常用，Handler 有很多sendXXXX开头的方法`sendMessageAtTime`、`sendEmptyMessageDelayed`、`sendEmptyMessage`等等，都是用来给消息队列添加消息的，那么这些方法最终都会调用`enqueueMessage`来实现消息进入队列：



```java
 private boolean enqueueMessage(MessageQueue queue, Message msg, long uptimeMillis) {
        //这句话很重要，让消息持有当前Handler的引用，在消息被Looper线程轮询到的时候
        //回调handler的handleMessage方法
        msg.target = this;
        if (mAsynchronous) {
            msg.setAsynchronous(true);
        }
        //调用MessageQueue 的enqueueMessage 方法把消息放入队列
        return queue.MessageQueue(msg, uptimeMillis);
    }
```

我们再来看下MessageQueue 的`enqueueMessage(msg, uptimeMillis)`方法：



```java
    boolean enqueueMessage(Message msg, long when) {
        // msg 必须有target也就是必须有handler
        if (msg.target == null) {
            throw new IllegalArgumentException("Message must have a target.");
        }
        if (msg.isInUse()) {
            throw new IllegalStateException(msg + " This message is already in use.");
        }
        //插入消息队列的时候需要做同步，因为会有多个线程同时做往这个队列插入消息
        synchronized (this) {
            if (mQuitting) {
                IllegalStateException e = new IllegalStateException(
                        msg.target + " sending message to a Handler on a dead thread");
                Log.w(TAG, e.getMessage(), e);
                msg.recycle();
                return false;
            }

            msg.markInUse();
            //when 表示这个消息执行的时间，队列是按照消息执行时间排序的
            //如果handler 调用的是postDelay 那么when=SystemClock.uptimeMillis()+delayMillis
            msg.when = when;
            Message p = mMessages;
            boolean needWake;
            if (p == null || when == 0 || when < p.when) {
                // p==null 表示当前消息队列没有消息
                msg.next = p;
                mMessages = msg;
                //需要唤醒主线程，如果队列没有元素，主线程会堵塞在管道的读端，这时
                //候队列突然有消息了，就会往管道写入字符，唤醒主线程
                needWake = mBlocked;
            } else {
                // Inserted within the middle of the queue.  Usually we don't have to wake
                // up the event queue unless there is a barrier at the head of the queue
                // and the message is the earliest asynchronous message in the queue.
                needWake = mBlocked && p.target == null && msg.isAsynchronous();
                Message prev;
                //将消息放到队列的确切位置，队列是按照msg的when 排序的，链表操作自己看咯
                for (;;) {
                    prev = p;
                    p = p.next;
                    if (p == null || when < p.when) {
                        break;
                    }
                    if (needWake && p.isAsynchronous()) {
                        needWake = false;
                    }
                }
                msg.next = p; // invariant: p == prev.next
                prev.next = msg;
            }

            // 如果需要唤醒Looper线程，这里调用native的方法实现epoll机制唤醒线程，我们就不在深入探讨了
            if (needWake) {
                nativeWake(mPtr);
            }
        }
        return true;
    }
```

最后我们再看下Handler 的`dispatchMessage`方法,这个方法在Looper线程从消息队列拿出来的时候，通过`msg.target.dispatchMessage(msg)`调用的。



```java
 /**
     * Handle system messages here.
     */
    public void dispatchMessage(Message msg) {
        //优先调用callback方法
        if (msg.callback != null) {
            handleCallback(msg);
        } else {
            if (mCallback != null) {
                if (mCallback.handleMessage(msg)) {
                    return;
                }
            }
            //最后会回调我们重写的handleMessage 方法
            handleMessage(msg);
        }
    }
```

到这里，整个Android的消息处理机制Java层内容基本讲解完毕了

