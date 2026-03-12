

本系列学习教程笔记属于详细讲解Kotlin语法的教程，需要快速学习Kotlin语法的小伙伴可以查看“简洁” 系列的教程

**快速入门请阅读如下简洁教程：**
[Kotlin学习教程(一)](https://developer.aliyun.com/article/1618222?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(二)](https://developer.aliyun.com/article/1618225?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(三)](https://developer.aliyun.com/article/1618227?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(四)](https://developer.aliyun.com/article/1618229?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(五)](https://developer.aliyun.com/article/1618573?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(六)](https://developer.aliyun.com/article/1618575?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(七)](https://developer.aliyun.com/article/1618580?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(八)](https://developer.aliyun.com/article/1618834?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(九)](https://developer.aliyun.com/article/1618841?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(十)](https://developer.aliyun.com/article/1618844?source=5176.11533457&userCode=ywqc0ubl)



Kotlin31 协程如何与 Java 进行混编？



## 问题

在 Java 与 Kotlin 混编项目中大概率是会遇到 Kotlin 线程的使用问题。协程的混编相对于其他特性的使用上会相对麻烦而且比较容易踩坑。我们以获取 token 来举例，比如有一个获取 token 的 suspend 函数：

```kotlin
kotlin 代码解读复制代码// 常规的 suspend 函数，可以供 Kotlin 使用，Java 无法直接使用
suspend fun getTokenSuspend(): String {
    // do something too long
    return "Token"
}
```

想要在 Java 中直接调用则会产出如下错误：

![image.png](https://s2.loli.net/2024/11/26/PdqyOhZC8Go7ncV.webp)

了解 Kotlin 协程机制的同学应该知道 suspend 修饰符在 Kotlin 编译器期会被处理成对应的 Continuation 类，这里不展开讨论。

这个问题也可以使用简单的方式进行解决，那就是使用 runBlocking 进行简单包装一下即可。

## 使用 runBlocking 解决

一般情况下我们可能会使用以下代码解决上述问题。定义的 Kotlin 协程代码如下：

```kotlin
kotlin 代码解读复制代码// 提供给 Java 使用的封装函数，Java 代码可以直接使用
fun getTokenBlocking(): String =runBlocking{// invoke suspend fun
    getTokenSuspend()
}
```

在 Java 层代码的使用方式大致如下：

```typescript
typescript 代码解读复制代码public void funInJava() {
    String token = TokenKt.getTokenBlocking();
}
```

看上去方案比较简单，但是直接使用 runBlocking 也会存在一些隐患。 runBlocking 会阻塞当前调用者的线程，如果是在主线程进行调用的话，会导致 App 卡顿，严重的会导致 ANR 问题。那有没有比 runBlocking 更合理的解决方案呐？

回答这个问题之前，先梳理下 Java 与 Kotlin 两种语言在处理耗时函数的一般做法。

## Java & Kotlin 耗时函数的一般定义

**Java**

- **靠语义约束**。比如定义的函数名中 sync 修饰，表明他可能是一个耗时的函数，更好的还会添加 `@WorkerThread` 注解，让 lint 帮助使用者去做一些检查，确保不会在主线程中去调用一些耗时函数导致页面卡顿。
- **靠语法约束，定义 Callback**。将耗时的函数执行放到一个单独的线程中执行，然后将回调的结果通过 Callback 的形式返回。这种方式无论调用者是什么水平，代码质量都不会有问题；

**Kotlin**

- **靠语义约束，同 Java**。
- **添加 suspend 修饰，靠语法约束**。内部耗时函数切到子线程中执行。外部调用者使用同步的方式调用耗时函数却不会阻塞主线程（这也是 Kotlin 协程主要宣传的点）。

在 Java 与 Kotlin 混编的项目中，上述情况的复杂度将会上升。

## 使用 CompletableFuture 解决

在审视一下 runBlocking 的使用问题，这种做法是将 Kotlin 中的语法约束**退化**到语义约束层面了，有的可能连语义层面的约束都没有，这种情况只能**祈求**调用者的使用是正确的 -- **在子线程调用，而不是在主线程调用**。那应该如何怎么处理，就是采用回调的方式，让语法能够规避的问题就不要采用语义来处理。

```kotlin
kotlin 代码解读复制代码suspend fun getToken(): String {
    // do something too long
    return "Token"
}

fun getTokenFuture(): CompletableFuture<String>  {
    returnCoroutineScope(Dispatchers.IO).future{getToken()}
}
```

注意：future 是 `org.jetbrains.kotlinx:kotlinx-coroutines-jdk8` 包中提供的工具类，基于 `CoroutineScope` 定义的扩展函数，使用时需要导入依赖包。

Java 中的使用方式如下：

```csharp
csharp 代码解读复制代码public void funInJava() {
    try {
        // 通过 Future get() 显示调用 getTokenFuture 函数
        TestKt.getTokenFuture().get();
    } catch (ExecutionException e) {
        e.printStackTrace();
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
}
```

可能会问这里看上去和直接在函数内部使用 runBlocking 没有太大的区别，反而使用上会更麻烦些。的确是这样的，这样的目的是**把选择权交给调用者**，或者说让调用者**显示**的知道这不是一个简单的函数，从而提高其在使用 API 时的警惕度，也就是之前提到的从语法层面对 API 进行约束。

退一步说，上述的内容是针对的仅仅是“不得不”这么做的场景，但是对于大部分场景都是可以通过合理的设计来避免出现上述情况：

- 底层定义的 suspend 函数可以在上层的 ViewModel 中的 `viewModelScope` 中调用解决；
- 统一对外暴露的 API 是 Java 类的话，新增的 API 提供可以使用 suspend 类型的扩展函数，使用 suspend 类型对外暴露；
- 如果明确知道调用者是 Java 代码，那么请提供 Callback 的 API 定义；

## 总结

尽量使用合理的设计来尽量规避 Kotlin 协程与 Java 混用的情况，**在 API 的定义上语法约束优先与语义约束，语义约束优于没有任何约束**。当然在特殊的情况下也可以使用 `CompletableFuture` API 来封装协程相关 API。

下面对几种常见场景推荐的一些写法：

1. 在单元测试中可以直接使用 `runBlocking` ；
2. 耗时函数可以直接定义为 suspend 函数或者使用 Callback 形式返回；
3. 对于 Java 类中调用协程函数的场景应使用显示的声明告知调用者，严格一点的可以判断线程，对于在主线程调用的可以抛出异常或者记录下来统一处理；

