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

Kotlin教程笔记(57) - 改良设计模式 - 单例模式



在Kotlin中，单例模式是一种常见且实用的设计模式，用于确保一个类只有一个实例，并提供全局访问点。本文将介绍几种常见的Kotlin单例实现方式，以及它们的原理和具体使用方法。



## 饿汉式单例



java实现

```
public class PlainOldSingleton {
    private static PlainOldSingleton INSTANCE = new PlainOldSingleton();

    private PlainOldSingleton(){
        System.out.println("PlainOldSingleton");
    }

    public static PlainOldSingleton getInstance(){
        return INSTANCE;
    }
}
```



kotlin实现

```
object PlainOldSingleton {

}
```



## 非线程安全的懒汉式单例



java实现

```
public class LazyNotThreadSafe {
    private static LazyNotThreadSafe INSTANCE;

    private LazyNotThreadSafe(){}

    public static LazyNotThreadSafe getInstance(){
        if(INSTANCE == null){
            INSTANCE = new LazyNotThreadSafe();
        }
        return INSTANCE;
    }
}
```



kotlin实现

```
class LazyNotThreadSafe {

    companion object{
        val instance by lazy(LazyThreadSafetyMode.NONE) {
            LazyNotThreadSafe()
        }

        //下面是另一种等价的写法, 获取单例使用 get 方法
        private var instance2: LazyNotThreadSafe? = null

        fun get() : LazyNotThreadSafe {
            if(instance2 == null){
                instance2 = LazyNotThreadSafe()
            }
            return instance2!!
        }
    }
}
```



## 线程安全的懒汉式单例



java实现

```
public class LazyThreadSafeSynchronized {
    private static LazyThreadSafeSynchronized INSTANCE;

    private LazyThreadSafeSynchronized(){}

    public static synchronized LazyThreadSafeSynchronized getInstance(){
        if(INSTANCE == null){
            INSTANCE = new LazyThreadSafeSynchronized();
        }
        return INSTANCE;
    }
}
```



kotlin实现

```
class LazyThreadSafeSynchronized private constructor() {
    companion object {
       private var instance: LazyThreadSafeSynchronized? = null

        @Synchronized
        fun get(): LazyThreadSafeSynchronized{
            if(instance == null) instance = LazyThreadSafeSynchronized()
            return instance!!
        }
    }
}
```



## DoubleCheck



java实现

```
public class LazyThreadSafeDoubleCheck {
    private static volatile LazyThreadSafeDoubleCheck INSTANCE;

    private LazyThreadSafeDoubleCheck(){}

    public static LazyThreadSafeDoubleCheck getInstance(){
        if(INSTANCE == null){
            synchronized (LazyThreadSafeDoubleCheck.class){
                if(INSTANCE == null) {
                    //初始化时分为实例化和赋值两步, 尽管我们把这一步写成下面的语句,
                    // 但Java虚拟机并不保证其他线程『眼中』这两步的顺序究竟是怎么样的
                    INSTANCE = new LazyThreadSafeDoubleCheck();
                }
            }
        }
        return INSTANCE;
    }
}
```



kotlin实现

```
class LazyThreadSafeDoubleCheck private constructor(){
    companion object{
        val instance by lazy(mode = LazyThreadSafetyMode.SYNCHRONIZED){
            LazyThreadSafeDoubleCheck()
        }

        private @Volatile var instance2: LazyThreadSafeDoubleCheck? = null

        fun get(): LazyThreadSafeDoubleCheck {
            if(instance2 == null){
                synchronized(this){
                    if(instance2 == null)
                        instance2 = LazyThreadSafeDoubleCheck()
                }
            }
            return instance2!!
        }
    }
}
```



## 静态内部类单例



java实现

```
public class LazyThreadSafeStaticInnerClass {

    private static class Holder{
        private static LazyThreadSafeStaticInnerClass INSTANCE = new LazyThreadSafeStaticInnerClass();
    }

    private LazyThreadSafeStaticInnerClass(){}

    public static LazyThreadSafeStaticInnerClass getInstance(){
        return Holder.INSTANCE;
    }
}
```



kotlin实现

```
class LazyThreadSafeStaticInnerObject private constructor(){
    companion object{
        fun getInstance() = Holder.instance
    }

    private object Holder{
        val instance = LazyThreadSafeStaticInnerObject()
    }
}
```







## 懒汉式单例

懒汉式单例在第一次使用时才会创建实例，适用于实例创建开销较大的情况。

```kotlin
class Singleton private constructor() {
    companion object {
        private var instance: Singleton? = null
        @Synchronized fun getInstance(): Singleton {
            if (instance == null) {
                instance = Singleton()
            }
            return instance!!
        }
    }
}
```

**原理说明**

- 使用`private constructor()`私有化构造函数，防止外部直接实例化对象。
- 通过`companion object`声明单例对象，并使用`getInstance()`方法获取单例实例。
- 在`getInstance()`方法中进行实例化，确保只有在需要时才会创建对象。
- 使用`Synchronized`关键字，保证线程安全。

## 饿汉式单例

饿汉式单例在类加载时就创建实例，保证了线程安全，但可能会造成资源浪费。

```kotlin
object Singleton {
    // 单例对象
}
```

**原理说明**

- 使用`object`关键字声明单例对象，该对象在类加载时立即被实例化。
- JVM会保证在任何线程访问该对象之前，该对象已经被初始化完毕，确保线程安全。

## 双重检查锁

双重检查锁机制在懒汉式的基础上增加了线程安全性和性能。

```kotlin
class Singleton private constructor() {
    companion object {
        @Volatile private var instance: Singleton? = null
        fun getInstance(): Singleton {
            return instance ?: synchronized(this) {
                instance ?: Singleton().also { instance = it }
            }
        }
    }
}
```

**原理说明**

- 使用`@Volatile`关键字确保instance字段的可见性，防止多线程环境下出现指令重排序导致的问题。
- 通过双重检查（Double-Checked）机制，在第一次调用`getInstance()`时进行加锁，确保只有一个线程能够创建实例。

## 静态内部类

使用静态内部类来实现单例模式，利用类加载机制保证线程安全。

```kotlin
class Singleton private constructor() {
    companion object {
        val instance = Holder.INSTANCE
    }

    private object Holder {
        val INSTANCE = Singleton()
    }
}
```

**原理说明**

- 将单例类的构造函数私有化，避免外部直接实例化。
- 通过一个静态内部类来持有单例实例，利用类加载机制保证了线程安全和延迟加载的效果。

## 枚举类

利用枚举类的特性，保证了单例的实现。

```kotlin
enum class Singleton {
    INSTANCE
}
```

**原理说明**

- 枚举类在Java和Kotlin中都是线程安全的，并且只会被装载一次。
- 利用枚举类的单例特性，可以直接通过`Singleton.INSTANCE`获取单例实例，保证了线程安全和延迟加载。
- 保证序列化与反序列化安全
- 避免反射问题

## 结语

Kotlin提供了多种实现单例模式的方式，每种方式都有其自身的优缺点，大家可以根据实际需求选择合适的方式。无论是懒汉式、饿汉式还是双重检查锁等等，都能够确保在应用程序中只有一个实例存在。







