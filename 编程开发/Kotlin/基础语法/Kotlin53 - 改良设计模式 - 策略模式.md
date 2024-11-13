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

Kotlin教程笔记(53） - 改良设计模式 - 策略模式



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 改良设计模式 - 策略模式



## [#](https://fullstackaction.github.io/pages/89ebcc/#一、前言)一、前言

- 策略模式
  - 作用：让算法的变化独立于使用算法的客户
  - 核心操作：定义了算法族，分别封装起来，让它们之间可以相互替换

## [#](https://fullstackaction.github.io/pages/89ebcc/#二、使用策略模式)二、使用策略模式

- 例子：游泳运动员的游泳姿势
- 重点：算法抽离，封装成策略

作为一个游泳运动员，最基本的技能就是游泳，所以该类可以这么定义：

```kotlin
/**
 * 游泳运动员
 *
 * @author GitLqr
 */
class Swimmer {
    fun swim() {
        println("游泳中...")
    }
}

// 使用
val shaw = Swimmer()
shaw.swim() // 游泳中...
```

但是，游泳体育项目会对游泳姿势进行细分（姑且称之为技能吧），比如：蛙泳、仰泳、自由泳等等，那怎么让 `Swimmer` 可以使用这些技能呢？一种做法是直接给 `Swimmer` 添加这些技能对应的方法，比如：

```kotlin
// ========== 错误演示 ==========
class Swimmer {
    fun breaststroke() {
        print("蛙泳...")
    }

    fun backstroke() {
        print("仰泳...")
    }

    fun freestyle() {
        print("自由泳...")
    }
}
```

可以很明确的说，这种做法是不行的，因为违背了开闭原则，后续被纳入标准的游泳姿势可能会越来越多，比如：狗刨，继续往 `Swimmer` 增加新方法吗？肯定不行，这时策略模式就派上用场了，站在程序角度看，游泳姿势也不过是一种算法，可以把这几种游泳姿势（算法）分别封装起来，为了能让算法相互替换，需要定义一个算法接口：

```kotlin
/**
 * 游泳姿势接口
 *
 * @author GitLqr
 */
interface SwimStrategy {
    fun swim()
}

/**
 * 各种游泳姿势的具体实现
 *
 * @author GitLqr
 */
class Breaststroke : SwimStrategy {
    override fun swim() {
        print("蛙泳...")
    }
}

class Backstroke : SwimStrategy {
    override fun swim() {
        print("仰泳...")
    }
}

class Freestyle : SwimStrategy {
    override fun swim() {
        print("自由泳...")
    }
}
```

接着，再通过构造器，把算法交给 `Swimmer` 使用即可：

```kotlin
/**
 * 游泳运动员（策略模式）
 *
 * @author GitLqr
 */
class Swimmer(val strategy: SwimStrategy) {
    fun swim() {
        strategy.swim()
    }
}

// 使用
val freestyleSwimmer = Swimmer(Freestyle())
freestyleSwimmer.swim()
val breaststrokeSwimmer = Swimmer(Breaststroke())
breaststrokeSwimmer.swim()
```

以后有更多的游泳姿势，只需要扩展 `SwimStrategy` 的实现类即可，无需修改 `Swimmer`。

## [#](https://fullstackaction.github.io/pages/89ebcc/#三、改良策略模式)三、改良策略模式

- 例子：游泳运动员的游泳姿势
- 重点：高阶函数

高阶函数是参数或返回值是函数的函数，由于策略模式是对行为算法的一种抽象，上述例子的本质是让 `Swimmer` 对象执行外界传入的 `算法函数` 而已，那么借助高阶函数的特性，我们可以让 `算法函数` 作为高阶函数的参数传入即可，而不需要单独定义接口，所以在 Kotlin 中可以使用高阶函数来改良策略模式：

```kotlin
fun breaststroke() {
    print("蛙泳...")
}

fun backstroke() {
    print("仰泳...")
}

fun freestyle() {
    print("自由泳...")
}

/**
 * 游泳运动员（策略模式）改良：高阶函数
 *
 * @author GitLqr
 */
class Swimmer(val strategy: () -> Unit) {
    fun swim() {
        strategy()
    }
}

// 使用
val freestyleSwimmer = Swimmer(::freestyle) // 传入方法引用
freestyleSwimmer.swim()
val breaststrokeSwimmer = Swimmer(::breaststroke)
breaststrokeSwimmer.swim()
```

改造之后，不但减少了代码量（去掉了策略算法接口），也使代码结构更加直观。