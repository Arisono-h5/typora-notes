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



  Kotlin教程笔记(1) - 数据类型



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 数据类型



## [#](https://fullstackaction.github.io/pages/c5b883/#boolean-类型)Boolean 类型

示例代码：

```kotlin
val aBoolean: Boolean = true
val anotherBoolean: Boolean = false
```

> kotlin 中的 Boolean 在多数情况下，相当于 Java 中基本类型 boolean，只有在必要情况下才会装箱成 Java 中的装箱类型 Boolean，由编译器决定，通常我们不需要关心。

## [#](https://fullstackaction.github.io/pages/c5b883/#number-类型)Number 类型

Number 即数字，主要包括整型和浮点型：

| 分类   | 类型   | 位宽 |
| ------ | ------ | ---- |
| 浮点型 | Double | 64   |
| Float  | 32     |      |
| 整型   | Long   | 64   |
| Int    | 32     |      |
| Short  | 16     |      |
| 字节   | Byte   | 8    |

### [#](https://fullstackaction.github.io/pages/c5b883/#int-类型)Int 类型

kotlin 的 Int 类型跟 Java 中的 int 一样，可以用整数、十六进制、二进制写法表示：

```kotlin
val anInt: Int = 8 // 8
val anotherInt: Int = 0xFF // 255
val moreInt: Int = 0b00000011 // 3
val maxInt: Int = Int.MAX_VALUE // 2147483647
val minInt: Int = Int.MIN_VALUE // -2147483648
```

> 整型是有符号的数，整型的最高位是符号位，剩下的 31 位表示数值范围，最大值是`Math.pow(2.0, 31.0) - 1`，最小值是`-Math.pow(2.0, 31.0)`

### [#](https://fullstackaction.github.io/pages/c5b883/#long-类型)Long 类型

Long 类型与 Int 类型相似，只是 Int 类型是 32 位，而 Long 类型是 64 位，能表示更大的数：

```kotlin
val aLong: Long = 12345678987654321 // 12345678987654321
val anotherLong: Long = 123 // 123
val maxLong: Long = Long.MAX_VALUE // 9223372036854775807
val minLong: Long = Long.MIN_VALUE // -9223372036854775808
```

> 因为 `anotherLong` 强制指定了 Long 类型，所以对应的值 123 是 Long 类型，而 `println(123)` 中的 123 则是 Int 类型，如果需要指定为 Long 类型的话，可以这样来书写 `println(123L)`。

### [#](https://fullstackaction.github.io/pages/c5b883/#float-类型)Float 类型

Float 即单精度浮点数，是带有小数的数，Float 类型的数值表示必须在末尾加上 `F` 或 `f`，否则编译会认为是 Double 类型。

```kotlin
val aFloat: Float = 2.0F // 2.0
val anotherFloat: Float = 1E3f // 1000.0
val maxFloat: Float = Float.MAX_VALUE // 3.4028235E38
val minFloat: Float = Float.MIN_VALUE // 1.4E-45
val minFloatReal: Float = -Float.MAX_VALUE // -3.4028235E38
val positiveInfinityFloat: Float = Float.POSITIVE_INFINITY // 正无穷，输出 Infinity
val negativeInfinityFloat: Float = Float.NEGATIVE_INFINITY // 负无穷，输出 -Infinity
```

> 要注意 `Float.MIN_VALUE` 指最小非 0 正数！最小非 0 正数！最小非 0 正数！如果想表示带符号的最小浮点数则需要使用 `-Float.MAX_VALUE`。

以下是 Kotlin 中 Float 的部分源码注释：

```kotlin
/**
 * Represents a single-precision 32-bit IEEE 754 floating point number.
 * On the JVM, non-nullable values of this type are represented as values of the primitive type `float`.
 */
public class Float private constructor() : Number(), Comparable<Float> {
    companion object {
        /**
         * A constant holding the smallest *positive* nonzero value of Float.
         */
        public val MIN_VALUE: Float

        /**
         * A constant holding the largest positive finite value of Float.
         */
        public val MAX_VALUE: Float
    }
}
```

#### [#](https://fullstackaction.github.io/pages/c5b883/#nan)NaN

Float 拥有一个 NaN 常量属性，表示"不是一个数"的数，什么情况下会得到 NaN 呢？

```kotlin
println(0.0f / 0.0f) // NaN
println(0.0f / 0.0f == Float.NaN) // false
```

通过上述 Demo 可以得出 2 个结论：

1. 除零可以得到 NaN
2. NaN 跟任何 NaN 结果不是相等的

> NaN 表示 "不是一个数" ，所以比较起来没有意义。

### [#](https://fullstackaction.github.io/pages/c5b883/#double-类型)Double 类型

Double 即双精度浮点数（或多精度浮点数），Double 之于 Float 就如同 Long 之 Int，故 Double 其实就是比 Float 能表示更大的浮点数而已。

```kotlin
val aDouble: Double = 3.0 // 3.0
val anotherDouble: Double = 3.1415926 // 3.1415926
val maxDouble: Double = Double.MAX_VALUE // 1.7976931348623157E308
val minDouble: Double = Double.MIN_VALUE // 4.9E-324
val minDoubleReal: Double = -Double.MAX_VALUE // -1.7976931348623157E308
```

> Double 与 Float 一样，`Double.MIN_VALUE` 表示的是最小非 0 正数。

### [#](https://fullstackaction.github.io/pages/c5b883/#short-类型)Short 类型

Short 也称短整型，位宽比 Int 少一半，即 16 位：

```kotlin
val aShort: Short = 127 // 127
val maxShort: Short = Short.MAX_VALUE // 32767
val minShort: Short = Short.MIN_VALUE // -32768
```

> 因为 Short 是 16 位的有符号数，所以 Short 能表示的最大数值是`2 的 15 次减 1`，即：`Math.pow(2.0, 15.0) - 1`。

### [#](https://fullstackaction.github.io/pages/c5b883/#byte-类型)Byte 类型

Byte 类型比 Short 类型更短，一般只用来处理二进制数据流：

```kotlin
val maxByte: Byte = Byte.MAX_VALUE // 127
val minByte: Byte = Byte.MIN_VALUE // -128
```

### [#](https://fullstackaction.github.io/pages/c5b883/#基本类型转换)基本类型转换

Java 支持使用 long 类型或 float 类型变量接收一个 int 类型变量，且不报错，这是因为 Java 支持隐式转换，但这在 Kotlin 中是行不通的，Kotlin 不支持隐式转换，举个例子：

```kotlin
val anInt: Int = 5
val aLong: Long = anInt // 报错：Type mismatch
val aLong: Long = anInt.toLong() // 正常
```

## [#](https://fullstackaction.github.io/pages/c5b883/#char-类型)Char 类型

- Char 称为字符，对应 Java 的 Character
- Char 占两个字节，表示一个 16 位的 Unicode 字符
- Char 需要用单引号 `''` 引起来，例如：'0'，'a'，'\n'

```kotlin
val aChar: Char = '0' // 0
val bChar: Char = '林' // 林
val cChar: Char = '\t' // 看不见的制表符
val dChar: Char = '\u9510' // 锐
```

> Char 表示一个字符，其值的书写可以是字母、数字、Unicode、以及类似 `\n` 的特殊字符。

还有一些符号，在语法上有特殊作用的，想要输出它原本的样子，需要借助 `\` 进行转义：

| 转义字符 | 含义                                          |
| :------: | :-------------------------------------------- |
|    \t    | 制表符                                        |
|    \b    | 光标后退一个字符                              |
|    \n    | 回车                                          |
|    \r    | 光标回到行首                                  |
|    \'    | 单引号                                        |
|    \"    | 双引号                                        |
|    \\    | 反斜杠                                        |
|    \$    | 美元符号，Kotlin 支持美元符号开头的字符串模板 |

```kotlin
val eChar: Char = '\'' // '
val fChar: Char = '"' // "
val gChar: Char = '\"' // "
val hChar: Char = '\$' // $
val iChar: Char = '\\' // \
```

## [#](https://fullstackaction.github.io/pages/c5b883/#string-类型)String 类型

String 字符串，即一连串的字符，字符 Char 使用 `''`引起来，字符串 String 则使用 `""`引起来：

```kotlin
val aString: String = "HelloWorld" // HelloWorld
val anotherString: String = String(charArrayOf('H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd')) // HelloWorld
println(aString == anotherString) // true
println(aString === anotherString) // false
println(aString.length) // 10
```

> 这里的 `==` 实际上就是 `equals()`，判断值是否相同；而 `===` 是全等运算符，除了判断值是否相等，还会判断地址是否也相同，只有值与地址都相等的情况下才会为 `true`。

字符串模板，可以在字符串中使用 `$` 符号引入其他变量：

```kotlin
println("输出一个字符串：" + aString) // HelloWorld
val arg1: Int = 0
val arg2: Int = 1
println("$arg1 + $arg2 = ${arg1 + arg2}") // 0 + 1 = 1
```

> 单个变量使用 `$` 即可，表达式则需要使用 `${}`

字符串除了可以用 `""`　引起来，还可以使用 `""""""` (3 对引号)引起来，3 引号字符串比双引号字符串更强大，包括换行也会被识别，不需要借助 `\n` ，但同时这些转义字符也就无效了，可以理解为是最原始的字符串。

```kotlin
// 输出结果：
//    \t \n
//    |哈哈哈
val rawString: String = """
    \t \n
    |哈哈哈
    """
val rawString1: String = """$aString  \$aString""" // HelloWorld  \HelloWorld
val rawString2: String = """$ aString""" // $ aString
```

> 三引号字符串支持字符串模板，即支持使用 `$` 引入变量，且无法使用 `\` 对 `$` 进行转义！