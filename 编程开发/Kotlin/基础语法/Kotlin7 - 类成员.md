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



  Kotlin教程笔记(7) - 类成员

# Kotlin - 类成员



## [#](https://fullstackaction.github.io/pages/a8e073/#类成员)类成员

类成员包括 `成员方法` 和 `成员属性`：

```kotlin
class Artist(var name: String) {　// 成员属性 name

    var age = 18 // 成员属性 age

    fun dance(danceName: String) { // 成员方法 dance
        println("$name 正在跳 $danceName")
    }

    fun sing(singName: String) { // 成员方法 sing
        println("$name 正在唱 $singName")
    }
}
```

类中的 dance 和 sing 是成员方法，age 是成员属性，使用 `var` 或 `val` 声明的构造器参数 name 也会成为类成员属性。

## [#](https://fullstackaction.github.io/pages/a8e073/#函数与方法)函数与方法

函数与方法形式一致，区别是方法在类中，函数则不是，因此，方法需要通过类名或对象来调用，而函数则是直接使用。

> 函数强调功能本身，不考虑从属。

```kotlin
// 函数
fun sayHello() {
    println("hello")
}

fun main(args: Array<String>) {
    val artist = Artist("lqr")
    artist.dance("恰恰")　// 调用对象 artist 的 dance 方法
    artist.sing("龙卷风")　// 调用对象 artist 的 sing 方法
    sayHello() // 调用函数
}
```

## [#](https://fullstackaction.github.io/pages/a8e073/#属性访问控制)属性访问控制

先来看个访问对象属性的例子：

```kotlin
class AClass {
    var b = 0
}
fun main() {
    val a = AClass()
    a.b = 666
    println(a.b) // 666
}
```

Kotlin 中，对象访问属性实质上都是使用 `getter/setter` ，而并非直接访问属性对其赋值。这可以通过重写属性的 `getter/setter` 来验证：

```kotlin
class AClass {
    var b = 0
        get() {
            println("some one tries to get b.")
            return field
        }
        set(value) {
            println("some one tries to set b.")
            field = value
        }
}

fun main() {
    val a = AClass()
    a.b = 666 // some one tries to set b.
    println(a.b) // some one tries to get b.
                 // 666
}
```

`getter/setter` 中使用属性时，需要用 `field` 来指代，避免出现代码歧义。

> 注意：val 常量没有 setter，因为 val 是不可变的！

默认属性的 `getter/setter` 的访问权限是 public，可以对其重写修改：

```kotlin
class AClass {
    var b = 0
        protected get // IDE报错：Getter visibility must be the same as property visibility
        protected set
}
```

如果修改了 `getter` 的访问权限，就需要对属性声明做同样的修改，于是，正确的写法是：

```kotlin
class AClass {
    protected var b = 0
        protected get
        protected set
}
```

## [#](https://fullstackaction.github.io/pages/a8e073/#属性初始化)属性初始化

Kotlin 中一般成员属性在声明时就需要初始化：

```kotlin
class AClass {
    var b = 0
    var c: String? = null
    // var c: String? // IDE报错：Property must be initialized or be abstract
}
```

Kotlin 也支持属性延迟初始化，但 `var` 和 `val` 的延迟初始化写法完全不同，`var` 变量使用 `lateinit`：

```kotlin
class X
class AClass {
    lateinit var c: String
    lateinit var d: X
    // lateinit val e:X // IDE报错：'lateinit' modifier is allowed only on mutable properties
}

fun main(args: Array<String>) {
    val a = AClass()

    a.d = X()
    println(a.d) // com.charylin.kotlinlearn.X@214c265e

    println(a.c) // lateinit property c has not been initialized
}
```

- `lateinit` 只能与 `var` 搭配，不能与 `val` 一起使用。
- `lateinit var` 变量在使用前一定要确保已经初始化，否则报错：`lateinit property c has not been initialized`。

说完 `lateinit var` ，再来看看 `val` 常量的延迟初始化，使用的是 `by lazy`，作用是 "使用时加载"：

```kotlin
class X
class AClass {
    // val e: X by lazy {} // IDE报错：Type mismatch. Required:X Found: Unit
    val e: X by lazy {
        println("init X")
        X()
    }
}

fun main(args: Array<String>) {
    val a = AClass()
    println("init a") // init a

    println(a.e) // init X
                 // com.charylin.kotlinlearn.X@3d075dc0
}
```

关于属性初始化的几点建议：

- 属性的初始化尽量在构造方法中完成
- 无法在构造方法中初始化，尝试降级为局部变量
- var 用 lateinit 延迟初始化，val 用 lazy
- 可空类型慎用 null 直接初始化