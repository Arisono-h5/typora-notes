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



  Kotlin教程笔记(4) - Kotlin - 区间与数组

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 区间与数组



## [#](https://fullstackaction.github.io/pages/022231/#区间-range)区间（Range）

区间是一个数学上的概念，表示范围。

### [#](https://fullstackaction.github.io/pages/022231/#区间的声明)区间的声明

Kotlin 中可以使用 `..` 或 `until` 来声明区间：

```kotlin
val range: IntRange = 0..1024 // 闭区间[0,1024]，包括1024
val rangeExclusive: IntRange = 0 until 1024 // 半开区间[0,1024)，不包括1024
val emptyRange: IntRange = 0..-1 // 空区间[]
```

其实这里的 `..` 操作符对应的是 `Int` 类中的一个 `rangeTo()` 方法：

```kotlin
/** Creates a range from this value to the specified [other] value. */
public operator fun rangeTo(other: Byte): IntRange
/** Creates a range from this value to the specified [other] value. */
public operator fun rangeTo(other: Short): IntRange
/** Creates a range from this value to the specified [other] value. */
public operator fun rangeTo(other: Int): IntRange
/** Creates a range from this value to the specified [other] value. */
public operator fun rangeTo(other: Long): LongRange
```

### [#](https://fullstackaction.github.io/pages/022231/#区间常用操作)区间常用操作

判断某个元素是否在区间内：

```kotlin
println(range.contains(50)) // true
println(500 in range) // true
```

> 这里的 `in` 关键字对应的就是 `IntRange` 类中的 `contains()` 方法，因此上面的两行代码实质上是一样的。

判断区间是否为空：

```kotlin
println(rangeExclusive.isEmpty()) // false
println(emptyRange.isEmpty()) // true
```

对区间进行遍历：

```kotlin
// 输出：0, 1, 2, 3 ..... 1020, 1021, 1022, 1023,
for (i in rangeExclusive) {
    print("$i, ")
}
```

> 这里的 `in` 跟 `for` 配合使用，就可以实现区间的遍历效果。

### [#](https://fullstackaction.github.io/pages/022231/#区间的类型)区间的类型

所有的区间都是 `ClosedRange` 的子类，`IntRange` 最常用。通过源码不难发现，除了 `IntRange` ，`ClosedRange` 的子类还有 `LongRange`、`CharRange` 等等。

![img](https://cdn.jsdelivr.net/gh/FullStackAction/PicBed@resource/image/20210116211449.png)

以 CharRange 为例，我们还可以写出 26 个大小写字母的区间：

```kotlin
// a b c d e f g h i j k l m n o p q r s t u v w x y z
val lowerRange: CharRange = 'a'..'z'
// A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
val upperRange: CharRange = 'A'..'Z'
```

## [#](https://fullstackaction.github.io/pages/022231/#数组-array)数组（Array）

数组(Array)跟数(Number)没有关系，它指的是一系列对象。

### [#](https://fullstackaction.github.io/pages/022231/#创建数组)创建数组

创建数组一般有 2 种方式：

1. 使用 `Array` 类创建数组
2. 使用库函数 `arrayOfXXX()` 创建数组

### [#](https://fullstackaction.github.io/pages/022231/#使用-array-类创建数组)使用 `Array` 类创建数组

先看看 Array 的构造函数：

```kotlin
public class Array<T> {
    /**
     * Creates a new array with the specified [size], where each element is calculated by calling the specified
     * [init] function. The [init] function returns an array element given its index.
     */
    public inline constructor(size: Int, init: (Int) -> T)

    ...
}
```

使用 `Array` 创建数组，需要指定元素类型（一般情况下可以省略），有 2 个必传参数，分别是数组长度 size，和元素初始化函数 init。

```kotlin
val array = Array<String>(5) { index -> "No.$index" }
println(array.size) // 5
for (str in array) { // No.0 No.1 No.2 No.3 No.4
    print("$str ")
}
```

> 当函数参数是最后一个形参时，可以把它写到括号外，这是 Kotlin 中的 lambda 写法，当然，你也可以不用 lambda 写法，就写在括号内：`val array = Array<String>(5, { index -> "No.$index" })`，关于 lambda 的相关知识在这里暂不细说。

### [#](https://fullstackaction.github.io/pages/022231/#使用库函数-arrayofxxx-创建数组)使用库函数 `arrayOfXXX()` 创建数组

直接使用 `Array` 创建数组会稍稍有点麻烦，要指定个数，又要传入初始化函数， 而实际开发中，我们希望有更方便的写法来提高工作效率，Kotlin 就为此就提供了一系列创建数组的库函数 `arrayOfXXX()` ：

```kotlin
val arrayOfString: Array<String> = arrayOf("我", "是", "LQR")
val arrayOfHuman: Array<Human> = arrayOf(Boy("温和", "英俊", "浑厚"), Girl("温柔", "甜美", "动人"))
val arrayOfInt: IntArray = intArrayOf(1, 3, 5, 7)
val arrayOfChar: CharArray = charArrayOf('H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd')
```

要注意，用于存放 String 类型或自定义类型的对象数组　的创建使用的是 `arrayOf()`，而基本数据类型数组的创建则有专门的库函数，如：`intArrayOf()`、`charArrayOf()` 等。`intArrayOf()`、`charArrayOf()` 等库函数是 Kotlin 为了避免基本数据装箱折箱的开销而专门创造出来的，比如：`intArrayOf(1, 3, 5, 7)` 创建出来的数组是 `IntArray` 类型，对应到 Java 中是 `int[]` ，而 `arrayOf(1, 2, 3, 4)` 创建出来的数组是 `Array<Int>` 类型，对应 Java 中是 `Integer[]`。

### [#](https://fullstackaction.github.io/pages/022231/#基本数据类型数组)基本数据类型数组

为了避免不必要的装箱和拆箱，基本数据类型的数组是定制的：

| Java     | Kotlin      |
| :------- | :---------- |
| int[]    | IntArray    |
| short[]  | ShortArray  |
| long[]   | LongArray   |
| float[]  | FloatArray  |
| double[] | DoubleArray |
| char[]   | CharArray   |

> 注意：`IntArray` 和 `Array<Int>` 是完全不同的类型，无法直接相互转换！
> 原话：Kotlin 也有无装箱开销的专门的类来表示原生类型数组: ByteArray、 ShortArray、IntArray 等等。这些类与 Array 并没有继承关系，但是它们有同样的方法属性集。

了解更多 Kotlin 中数组的相关知识，请访问：[https://www.kotlincn.net/docs/reference/basic-types.html#数组(opens new window)](https://www.kotlincn.net/docs/reference/basic-types.html#数组)

### [#](https://fullstackaction.github.io/pages/022231/#数组常用操作)数组常用操作

可以使用 `.size` 获取数组长度，使用 `for-in` 遍历数组：

```kotlin
println(arrayOfInt.size) // 4
for (int in arrayOfInt) { // 1 3 5 7
    print("$int ")
}
```

`Array` 定义了 get 与 set 函数（按照运算符重载约定这会转变为 `[]`），因此我们可以通过 `[]` 来获取或修改数组中的元素：

```kotlin
println(arrayOfHuman[1]) // 我是性格温柔，长相甜美，声音动人的人
arrayOfHuman[1] = Boy("温和1", "英俊1", "浑厚1")
println(arrayOfHuman[1]) // 我是性格温和1，长相英俊1，声音浑厚1的人
```

> 注意：自定义类型对象使用 `println()` 默认输出的是对象地址信息，如：`com.charylin.kotlinlearn.Boy@7440e464` ，需要重写类的 `toString()` 方法来修改输出日志内容。

`CharArray` 提供了 `joinToString()` 方法，用于将字符数组拼接成字符串，默认以 `,` 作为拼接符：

```kotlin
println(arrayOfChar.joinToString()) // H, e, l, l, o, W, o, r, l, d
println(arrayOfChar.joinToString("")) // HelloWorld
```

可以使用 `slice()` 方法对数组进行切片：

```kotlin
println(arrayOfInt.slice(1..2)) // [3, 5]
```