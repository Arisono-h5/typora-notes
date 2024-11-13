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

Kotlin教程笔记(51) - 改良设计模式 - 构建者模式



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 改良设计模式 - 构建者模式



## [#](https://fullstackaction.github.io/pages/dd574d/#一、前言)一、前言

- 构建者模式
  - 作用：将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。
  - 核心操作：私有化复杂对象（Product）的类构造器，设计并创建 Builder 类。

## [#](https://fullstackaction.github.io/pages/dd574d/#二、使用构建者模式)二、使用构建者模式

- 例子：组装电脑
- 重点：多构造器、构建者模式

应用开发过程中，总会遇到创建复杂对象（Product）的情况，以组装电脑为例，从硬件到软件，需要配置的参数非常多，即构造器需要传入 n 个参数，于是我们可能会写出如下代码：

```kotlin
/**
 * 电脑类
 *
 * @author GitLqr
 */
class Computer(
    val mainboard: String, // 主板
    val cpu: String, // 处理器
    val ram: String, // 内存
    val battery: String, // 电源
    val gpu: String?, // 显卡
    val hardDisk: String?, // 硬盘
    val networkInterface: String?, // 网线接口
    val cdDriver: String?, // 光驱
    val os: String?, // 系统
    val chassis: String?, // 机箱
    val mouse: String?, // 鼠标
    val keyboard: String?, // 键盘
    val monitor: String? // 显示器
)

// 使用
val nbComputer = Computer(
    "超微X8QB6-F", "Intel Xeon E7-8870", "海盗船(CORSAIR) 复仇者LPX DDR4 2133 64GB 7000",
    "西门子豪华供电柜", "Leadtek/丽台Quadro Plex 7000", "WD_BLACK SN850 2T",
    "Intel/英特尔 万兆光纤网卡 EXPX9501AFXLR", "ThinkPad 43N3215 Blu-ray Burner Ultrabay",
    "Windows 11", "游戏悍将太极施洛华世奇", "RAPOO雷柏 3710 2.4G激光无线鼠标",
    "Optimus Maximus 多功能 概念式键盘", "Sharp/夏普 LB-1085 108英寸 FULL HD专业液晶显示器"
)
```

但是并不是所有的参数都是必须的，在 Java 中，我们一般会通过 `重载构造器` 来减少对象创建时需要传入的参数个数，在 Kotlin 中，`重载构造器` 就是定义次级构造器：

```kotlin
/**
 * 电脑类（重载构造器）
 *
 * @author GitLqr
 */
class Computer(
    val mainboard: String, // 主板
    val cpu: String, // 处理器
    val ram: String, // 内存
    val battery: String, // 电源
    val gpu: String?, // 显卡
    val hardDisk: String?, // 硬盘
    val networkInterface: String?, // 网线接口
    val cdDriver: String?, // 光驱
    val os: String?, // 系统
    val chassis: String?, // 机箱
    val mouse: String?, // 鼠标
    val keyboard: String?, // 键盘
    val monitor: String? // 显示器
) {
    // 次构造器需要调用主构造器传参
    constructor(mainboard: String, cpu: String, ram: String, battery: String) :
            this(mainboard, cpu, ram, battery, null, null, null, null, null, null, null, null, null)
}

// 使用
val simpleComputer = Computer("超微X8QB6-F", "Intel Xeon E7-8870", "海盗船(CORSAIR) 复仇者LPX DDR4 2133 64GB 7000", "西门子豪华供电柜")
```

但是 `重载构造器` 这种方案并不好，一旦重载的多了，代码就会变得很难维护，于是，在 Java 中，对于创建复杂对象这种情景，一般会使用 `构建者模式` 来处理，在使用 `构建者模式` 时需要遵循以下几点套路：

- Product：私有化复杂对象的类构造器（确保使用者无法直接通过构造器创建实例）
- Builder：
  - `必传参数` 通过 构造器 传入
  - `可选参数` 通过一系列 Setter 传入
  - 提供一个 `build()` 方法返回一个 Product 对象

下面我们就用 `构建者模式` 来改造上面的代码:

```kotlin
/**
 * 电脑类（构建者模式）
 *
 * @author GitLqr
 */
class Computer private constructor( // 私有化复杂对象的类构造器
    val mainboard: String, // 主板
    val cpu: String, // 处理器
    val ram: String, // 内存
    val battery: String, // 电源
    val gpu: String?, // 显卡
    val hardDisk: String?, // 硬盘
    val networkInterface: String? // 网线接口
    ...
) {
    // 【必传参数】通过 构造器 传入
    class Builder(val mainboard: String, val cpu: String, val ram: String, val battery: String) {
        var gpu: String? = null
        var hardDisk: String? = null
        var networkInterface: String? = null
        ...

        fun setGpu(gpu: String): Builder {
            this.gpu = gpu
            return this
        }

        fun setHardDisk(hardDisk: String): Builder {
            this.hardDisk = hardDisk
            return this
        }

        fun setNetworkInterface(networkInterface: String): Builder {
            this.networkInterface = networkInterface
            return this
        }

        ...

        // 别忘了，还要有一个 build() 方法，用来创建复杂对象并返回
        fun build(): Computer {
            return Computer(mainboard, cpu, ram, battery, gpu, hardDisk, networkInterface, ...)
        }
    }
}

// 使用
val computer =
    Computer.Builder("超微X8QB6-F", "Intel Xeon E7-8870", "海盗船(CORSAIR) 复仇者LPX DDR4 2133 64GB 7000", "西门子豪华供电柜")
        .setGpu("Leadtek/丽台Quadro Plex 7000")
        .setHardDisk("WD_BLACK SN850 2T")
        .setNetworkInterface("Intel/英特尔 万兆光纤网卡 EXPX9501AFXLR")
        .build()
```

总结一下 `构建者模式` 的优缺点：

- 优点：
  - 结合 `链式调用` 设计，代码上更加美观
  - 对于可选参数的设置，更加语义化
- 缺点：
  - 当可选参数比较多时，Builder 代码比较冗长
  - 在使用 Builder 时可能会忘记 `build()` 方法的调用
  - 在创建 Product 对象之前，必须先创建 Builder 对象，会增加额外的开销

## [#](https://fullstackaction.github.io/pages/dd574d/#三、改良构建者模式)三、改良构建者模式

- 例子：组装电脑
- 重点：构建者模式本质上是模拟了具名的可选参数

Kotlin 作为更好的 Java，拥有更多现代语言的特性，`具名可选参数` 就是众多特性之一，我们完全可以使用这个特性来改良（或者说是取代）构建者模式。

Kotlin 的 `具名可选参数` 有以下特点：

- 在具体化一个参数的取值时，可以通过带上它的参数名，而不是它在所有参数中的位置决定
- 由于参数可以设置默认值，这允许我们可以只给出部分参数的取值，而不必是所有的参数

下面我们用 Kotlin 的 `具名可选参数` 来改造上面的代码：

```kotlin
/**
 * 电脑类（构建者模式）改良：带默认值的具名可选参数
 *
 * @author GitLqr
 */
class Computer(
    val mainboard: String, // 主板
    val cpu: String, // 处理器
    val ram: String, // 内存
    val battery: String, // 电源
    val gpu: String? = null, // 显卡
    val hardDisk: String? = null, // 硬盘
    val networkInterface: String? = null, // 网线接口
    val cdDriver: String? = null, // 光驱
    val os: String? = null, // 系统
    val chassis: String? = null, // 机箱
    val mouse: String? = null, // 鼠标
    val keyboard: String? = null, // 键盘
    val monitor: String? = null // 显示器
)

// 使用
val computer = Computer(
    "超微X8QB6-F", "Intel Xeon E7-8870", "海盗船(CORSAIR) 复仇者LPX DDR4 2133 64GB 7000", "西门子豪华供电柜",
    gpu = "Leadtek/丽台Quadro Plex 7000",
    os = "Windows 11",
    mouse = "RAPOO雷柏 3710 2.4G激光无线鼠标",
    keyboard = "Optimus Maximus 多功能 概念式键盘",
    monitor = "Sharp/夏普 LB-1085 108英寸 FULL HD专业液晶显示器"
)
```

总结一下 `具名可选参数` 的优点：

- 代码简洁优雅，无论是 Product 的类结构，或者是创建一个 Product 实例
- 创建 Product 实例时，显式指定参数名即可，无须按顺序传入
- 所有参数均使用 val 声明，相比 Builder 中使用 var 更加安全

## [#](https://fullstackaction.github.io/pages/dd574d/#四、对参数进行约束)四、对参数进行约束

构建者模式还有另一个作用，就是在 `build()` 方法中可以对参数进行约束，比如，如果一台电脑有指定操作系统（`os`），可是它没有硬盘（`hardDisk`），这显然是不对的，若使用构建者模式，则可以在 `build()` 方法中做如下条件约束：

```kotlin
/**
 * 构建者模式：在 build() 方法中对参数进行约束、校验
 *
 * @author GitLqr
 */
class Computer private constructor( ... ) {
    class Builder( ... ) {
        ...
        fun build(): Computer {
            if (os != null && hardDisk == null) {
                throw IllegalArgumentException("没有硬盘安装不了操作系统")
            }
            return Computer(...)
        }
    }
}
```

那么改用 `具名可选参数` 这种方案之后，如果需要给参数添加约束条件时该怎么办呢？可以在 `init` 代码块中进行约束条件判断，这时顺便介绍一下 Kotlin 提供的 `require()` 方法，相当于是 Java 中的 `assert`：

```kotlin
/**
 * 具名可选参数：在 init{} 代码块中对参数进行约束、校验
 *
 * @author GitLqr
 */
class Computer(
    val mainboard: String, // 主板
    val cpu: String, // 处理器
    val ram: String, // 内存
    val battery: String, // 电源
    val gpu: String? = null, // 显卡
    val hardDisk: String? = null, // 硬盘
    val networkInterface: String? = null, // 网线接口
    val cdDriver: String? = null, // 光驱
    val os: String? = null, // 系统
    val chassis: String? = null, // 机箱
    val mouse: String? = null, // 鼠标
    val keyboard: String? = null, // 键盘
    val monitor: String? = null // 显示器
) {
    init {

        // if (os != null && hardDisk == null) {
        //     throw IllegalArgumentException("没有硬盘安装不了操作系统")
        // }

        require(!(os != null && hardDisk == null)) {
            "没有硬盘安装不了操作系统"
        }
    }
}
```

所以，综上所述，在 Kotlin 中，大可不必使用构建者模式~

> 《Effective Java》中是这样介绍构建者模式的：本质上 builder 模式模拟了具名的可选参数，就像 Ada 和 Python 中的一样。