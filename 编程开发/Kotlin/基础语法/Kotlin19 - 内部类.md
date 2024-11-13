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

Kotlin教程笔记(19) - 内部类

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 内部类



## [#](https://fullstackaction.github.io/pages/3420a3/#内部类)内部类

内部类就是定义在类内部的类，Kotlin 中的内部类大致分为 2 种：

- 静态内部类
- 非静态内部类

### [#](https://fullstackaction.github.io/pages/3420a3/#静态内部类)静态内部类

在某个类中像普通类一样声明即可，可以认为静态内部类与外部类没有关系，只是定义在了外部类"体内"而已，在使用静态内部类时需要"带上"外部类：

```kotlin
class Outer {
    val a: Int = 0

    class Inner {
        val a: Int = 5
    }
}

fun main() {
    val outer = Outer()
    println(outer.a)
    val inner = Outer.Inner()
    println(inner.a)
}
```

> 注意，在 Java 中，这种写法就是在定义 `非静态内部类`，而 `静态内部类` 需要在声明时使用 `static` 修饰。

### [#](https://fullstackaction.github.io/pages/3420a3/#非静态内部类)非静态内部类

非静态内部类与静态内部类有的区别有：

- `非静态内部类` 会持有外部类的引用，而 `静态内部类` 不会(可以认为两者没有关系)。
- `非静态内部类` 使用时需要基于外部类对象（`Outer().Inner()`），而 `静态内部类` 则是基于外部类（`Outer.Inner()`）。

因为 `非静态内部类` 会持有外部类的引用，所以内部类可以直接使用外部类成员；当非静态内部类与外部类存在同名成员时，可以使用 `@标记` 来解决歧义：

```kotlin
class Outer {
    val b: Int = 3
    val a: Int = 0

    inner class Inner {
        val a: Int = 5
        fun test() {
            println("Outer b = $b") // 3，因为持有外部类的引用，所以直接使用外部类成员
            println("Outer a = ${this@Outer.a}") // 0，使用 @Outer 指定this是外部类对象
            println("Inner a = ${this@Inner.a}") // 5，使用 @Inner 指定this是内部类对象
            println("Inner a = ${this.a}") // 5，不使用 @标记 默认this就是内部类对象
        }
    }
}

fun main() {
    val inner = Outer().Inner()
    inner.test()
}
```

为了区分 Kotlin 与 Java 中静态内部类和非静态内部类声明上的不同，以下分别使用 Kotlin 和 Java 各自编写内部类代码：

```kotlin
// Kotlin - 非静态内部类
class Outer {
    inner class Inner {...}
}

// Kotlin - 静态内部类
class Outer {
    class Inner {...}
}
// Java - 非静态内部类
public class Outer {
    public class Inner {...}
}

// Java - 静态内部类
public class Outer {
    public static class Inner {...}
}
```

## [#](https://fullstackaction.github.io/pages/3420a3/#匿名内部类)匿名内部类

匿名内部类就是没有定义名字的内部类，一般格式为 `object : 接口或(和)类`，实际开发中，方法的回调接口(即 callback)一般不会专门声明一个类再创建对象来使用，而是直接使用匿名内部类：

```kotlin
val textArea = TextArea()
textArea.addTextListener(object : TextListener {
    override fun textValueChanged(e: TextEvent?) {...}
})
```

Kotlin 的匿名内部类很强大，在使用时，可以有多个接口或父类，如：

```kotlin
val textArea = TextArea()
textArea.addTextListener(object : TextField(), TextListener {
    override fun textValueChanged(e: TextEvent?) {...}
})
```

这个匿名内部类既是 TextField 的子类，也是 TextListener 的实现类，不过可能实际应用场景会比较少，了解即可。

> Java 中的匿名内部类就没这么强大了，只能是 `单个` 接口(或父类) 的 实现类(子类)。