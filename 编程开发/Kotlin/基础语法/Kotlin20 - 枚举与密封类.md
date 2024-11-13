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

Kotlin教程笔记(20) - 枚举与密封类



# Kotlin - 枚举与密封类



## [#](https://fullstackaction.github.io/pages/a52cff/#枚举)枚举

Kotlin 支持枚举，需要使用 `enum class` 进行声明，如：

```kotlin
enum class LogLevel {
    VERBOSE, DEBUG, INFO, WARN, ERROR, ASSERT
}
```

上面的代码可以理解为是 LogLevel 类的 `companion object` 语法糖：

```kotlin
class LogLevel private constructor() {
    companion object {
        val VERBOSE = LogLevel()
        val DEBUG = LogLevel()
        val INFO = LogLevel()
        val WARN = LogLevel()
        val ERROR = LogLevel()
        val ASSERT = LogLevel()
    }
}
```

所以我们可以知道枚举中的每一个成员，其实都是枚举的一个实例对象，因此枚举会比较占内存；另外，因为 class 默认是 final 的，且构造器是 private 的，所以枚举没有子类，因此枚举是实例可数的。既然枚举是类，那它就可以有构造函数以及成员方法：

```kotlin
enum class LogLevel(val id: Int) {
    VERBOSE(0), DEBUG(1), INFO(2), WARN(3), ERROR(4), ASSERT(5);

    override fun toString(): String {
        return "id = $id, name = $name, ordinal = $ordinal"
    }
}
```

枚举 `enum class` 自身提供了几个有用的成员属性与方法：

- 成员属性 `ordinal` 可以获取到当前枚举实例的序号
- 成员方法 `values()` 可以获取到枚举的所有实例对象
- 成员方法 `valueOf()` 可以根据枚举实例名获取到枚举实例对象

```kotlin
fun main() {
    println(LogLevel.DEBUG.ordinal) // 1
    LogLevel.values().map(::println) // id = 0, name = VERBOSE, ordinal = 0
                                     // id = 1, name = DEBUG, ordinal = 1
                                     // id = 2, name = INFO, ordinal = 2
                                     // id = 3, name = WARN, ordinal = 3
                                     // id = 4, name = ERROR, ordinal = 4
                                     // id = 5, name = ASSERT, ordinal = 5
    println(LogLevel.valueOf("ERROR")) // id = 4, name = ERROR, ordinal = 4
}
```

## [#](https://fullstackaction.github.io/pages/a52cff/#密封类)密封类

密封类是子类有限的类，需要使用 `sealed class` 进行声明：

```kotlin
// SealedClassExample.kt
sealed class Human

class YellowRace : Human() // 黄种人
class WhiteRace : Human() // 白种人
class BlackRace : Human() // 黑种人
object Jesus : Human() // 耶稣
object MonkeyKing : Human() // 齐天大圣
```

它的构造器默认就是 private 的，且不可修改，它的子类只能定义在同个 kt 文件中或者是密封类的内部类：

![img](https://cdn.jsdelivr.net/gh/FullStackAction/PicBed@resource/image/20210131230402.png)

综上，我们可以发现枚举(`enum class`)和密封类(`sealed class`)很相似，但要分清楚两者的区别：

- 枚举：实例可数，没有子类。
- 密封类：子类可数，有子类。