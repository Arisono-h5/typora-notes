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

​     Kotlin教程笔记(15) - 方法重载与默认参数

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 方法重载与默认参数



## [#](https://fullstackaction.github.io/pages/334ef0/#方法重载-overloads)方法重载（Overloads）

当一个类中有两个或多个具有相同方法名和不同的参数类型的方法时，就是重载：

```kotlin
class Person {
    fun say() {
        println("hahaha")
    }
    fun say(what: String) {
        println(what)
    }
    fun say(obj: Any) {
        println("this is ${obj.javaClass.simpleName}")
    }
}

fun main() {
    val person = Person()
    person.say() // hahaha
    person.say("hehehe") // hehehe
    person.say(person) // this is Person
}
```

> 方法签名由方法名和参数类型决定，与方法的其他属性无关。

## [#](https://fullstackaction.github.io/pages/334ef0/#默认参数)默认参数

在 Kotlin 中，方法可以使用默认参数，一般情况下，方法重载可以转换成带默认参数的方法：

```kotlin
class Person {
    fun say(what: String = "hahaha") {
        println(what)
    }
    fun say(obj: Any) {
        println("this is ${obj.javaClass.simpleName}")
    }
}

fun main() {
    val person = Person()
    person.say() // hahaha
    person.say("hehehe") // hehehe
    person.say(person) // this is Person
}
```

可以看到这里只是把 `say()` 和 `say(what:String)` 使用默认参数整合了，但 `say(obj:Any)` 还在，其实 `say(obj:Any)` 的设计是不合理的，因为 String 是 Any 的子类，在调用方法时会有歧义，开发中，最好避免这种写法。

## [#](https://fullstackaction.github.io/pages/334ef0/#jvmoverloads)JvmOverloads

现在 Person 类中的 say()是重载方法，而且其中一个 say 有默认参数，我们来看看在 Java 中调用如何：

![img](https://cdn.jsdelivr.net/gh/FullStackAction/PicBed@resource/image/20210129083101.png)

可以发现，Java 中识别不到不带参数的 say()方法，这是因为 Java 并不知道 Kotlin 中有默认参数这种特性，它只能认为 `say(what:String)` 和 `say(obj:Any)` 是重载方法，把 `say(what:String)` 中的默认参数给忽略了，Kotlin 提供了 `@JvmOverloads` 可以将带有默认参数的方法转换成对应的重载方法：

```kotlin
class Person {
    @JvmOverloads
    fun say(what: String = "hahaha") {
        println(what)
    }

    fun say(obj: Any) {
        println("this is ${obj.javaClass.simpleName}")
    }
}
```

ok，这下 Java 中就识别到了不带参数的 say()方法了

![image-20241014190308995](https://s2.loli.net/2024/10/14/1NxXb69OFMDLltz.png)

