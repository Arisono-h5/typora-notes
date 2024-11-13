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

Kotlin教程笔记(24) -尾递归优化



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABH1JREFUSA3tVl1oHFUUPmdmd2ltklqbpJDiNnXFmgbFktho7YMPNiJSSZM0+CAYSkUELVhM6YuwIPpgoOKDqOBDC0XE2CQoNtQXBUFTTcCi+Wlh1V2TQExsUzcltd3M9Tt3ZjZzZ2fT+OJTL8yeM+eee757fmeJbq//KQL8X3DUSFOcfr7cRsRtxNQMWueeVzOkaITIGqQHNg5y8+jNW9ldM7A6nTpAjuolUikAwq7CE3WcM2RRDz+XGVgN3FptU/aUSlvq9Pa3iZ1+sgAqJyyAFqkipd9dqiwHF3P65YycLWc/6sqGrvoEoIp6DOFaX5h6+dnfjkWprwqsPk0dUGq5vySwDImC10KxFHgGL1SWoc92O3eVht09qdXNH11I2SsTsJYqMWzihqGMi+A+Garf3BAuuLI5oGlULyNfyB/HYNujwktOfRrMr5t77NmevqaUopx0grnKAyvVpmwUDB4x6FPXuGvYLTDwWsejwgtgkYKPqRJg8SV6xaiZ3ZTppGneS4yfH5/66fZSDHv+QZci/+h5c5UHtpy67JUqGppM0sh0Nc1dW6/N1W5Yoqat8/TU/VnadmdeW2PLLSyh0cvxBs3KbqTmwYPpxN4do/mzE8nEpvX/UMu2Wbp74zUAK5q6WkHns7V0eWkdPbPzd3rxkTGybadYySumVzhcaJFbs5UrEkQ/+CK8gF5dnh/6ciIZ73gwQ927L1IitoxKLXYP3SjYdOrHHfTZhRRlFyrorafPk20B3HPD1y2G3qKZME5Jcf3t/HUC13/8tSd++vqFveMUTwAUxSUFI1QekR1+bIze3D9MF2aq6cPvG72CgnldWCFqyRw3lwH8ZMerjTD9ElRO7Gv44wNpC90aASqGfVlz/Rx17srQ57/UU26hkhQqUB7dBR71WmzQhHUnblGmVOEw0jhbV1n9OlXUDCIRGaNV5Jp43N516fN7JmnTHdfp7Hgy0luO4aMhtkLL8Bi3bUWYvzh5Mn1dTxrL6QmGuRhGL/TiTTxRoEdTszSaq9GR0NGA3KdkOz3hqSV3MIDhQ5IVX/Ivx3umBti2es2h4eZby7x8br1rkf7Mo90AqC8aQ3sJeNzqFRu+vSANAQe3PL7l0HGOAdwDCeZYvNKeoZp1Qfs6Aipndh86HmFRi0LAnEO47wsqM6cdfjh3jBPUzhZy7nvlUfFsamED1VQt6aISHVymXZ/B2aCtIG8AI8xfobj2d3en1wWVhOeHELKmLQ1s211s88comkv4UCwWyF787mJdYXtNfhKAXVqnKTq8QZvGAGGOfaTo5pGZ/PwbUCr5+DPr/1J92JNHr9aOl/F3iI5+O1nfybsGxoimvZ3ViWSluDITw3P37mypheDIPY0tw7+O/5ApbkYw+zpfaUVu32Pi98+defdUhEpZkRFq0aqyNh9FuL9hpYbEm6iwi0z2REd09ZmyENEbuhjDWzKvZXTqKYaBIr3tt5kuPtQBZFvEUwHt60vfCNu41XsksH9Ij1BMMz1Y0OOunHNShFIP5868g5zeXmuLwL9T4b6Q2+KejgAAAABJRU5ErkJggg==)Kotlin - 尾递归优化



## [#](https://fullstackaction.github.io/pages/0790a0/#尾递归)尾递归

尾递归就是函数在调用完自己之后没有其他操作的递归，是递归的一种特殊形式。举个例子，"计算斐波那契数列第 n 项"的递归算法有哪些？

### [#](https://fullstackaction.github.io/pages/0790a0/#简单递归实现)简单递归实现

斐波那契数列第 0、1 位都是 1，从第二位开始，每项是前两位之和，因此用递归算法很容易就能实现出来了：

```kotlin
fun fib1(n: Int): Int {
    if (n == 0 || n == 1) return 1
    return fib1(n - 1) + fib1(n - 2);
}
```

这种写法虽然递归调用是在方法的最后一行，但其实这里还有结果相加的操作，并不符合尾递归的定义。

简单递归虽然容易理解，但实际上，该算法会有冗余计算，比如：fib1(2)会被执行多次，如果 n 越大，这种冗余计算就会越多：

![image-20241015093649384](https://s2.loli.net/2024/10/15/SNfhk1UznbVZoER.png)



### [#](https://fullstackaction.github.io/pages/0790a0/#尾递归实现)尾递归实现

为了解决上述简单递归实现的弊端，我们可以把已经计算过的结果保存起来，传递给下次计算，所以可以将递归写法进行优化：

```kotlin
fun fib2(n: Int): Int {
    return fibIter(1, 1, n);
}

fun fibIter(a: Int, b: Int, n: Int): Int {
    // return if (n == 0) a else fibIter(b, a + b, n - 1) // 简便写法
    if (n == 0) {
        return a
    } else {
        return fibIter(b, a + b, n - 1)
    }
}
```

其中，`fibIter()` 的递归代码在方法的最后一行，调用完也没有其他的操作，符合尾递归的定义。

### [#](https://fullstackaction.github.io/pages/0790a0/#性能对比)性能对比

理论归理论，我们还是得用实际代码来测试一下两种递归算法的运行耗时情况，这种才更能直观看出差别，为了方便测试，这里写了一个耗时测试方法：

```kotlin
fun timeConsume(operation: () -> Unit) {
    val begin = System.currentTimeMillis()
    operation()
    val end = System.currentTimeMillis()
    println("begin = ${begin}ms , end = ${end}ms , 耗时 ${end - begin}ms")
}
```

分别将两种递归算法丢到耗时测试方法 `timeConsume()` 中，得到测试结果：

```kotlin
fun main(args: Array<String>) {
    timeConsume {
        println(fib1(45))
    }
    // 1836311903
    // begin = 1612368480299ms , end = 1612368486217ms , 耗时 5918ms

    timeConsume {
        println(fib2(45))
    }
    // 1836311903
    // begin = 1612368486217ms , end = 1612368486217ms , 耗时 0ms
}
```

为了拿到斐波那契数列第 45 个元素值，fib1() 耗时近 6s，而 fib2() 耗时 0ms，这是何等的差距。

> 注意：测试 fib1(50) 会内存溢出。

## [#](https://fullstackaction.github.io/pages/0790a0/#尾递归优化-tailrec)尾递归优化(tailrec)

虽然上述尾递归算法的耗时很小，但我们知道，递归算法效率其实并不高，因为每递归一次就要开辟一个方法栈，这是有性能消耗的，还有可能因为递归次数过多导致出现内存溢出的情况，而迭代算法就没有这种问题：

```kotlin
fun fib3(n: Int): Int {
    if (n == 0 || n == 1) return 1
    var a = 1
    var b = 1
    for (i in 0 until n) {
        val a_ = b
        val b_ = a + b
        a = a_
        b = b_
    }
    return a
}
```

同样的，我们来对尾递归算法和迭代算法进行耗时测试：

```kotlin
fun main(args: Array<String>) {
    timeConsume {
        println(fib2(12000))
    }
    // 690383169
    // begin = 1612369032575ms , end = 1612369032578ms , 耗时 3ms

    timeConsume {
        println(fib3(12000))
    }
    // 690383169
    // begin = 1612369032578ms , end = 1612369032579ms , 耗时 1ms
}
```

理论与实际相结合，通过测试结果可以得知，尾递归算法和迭代算法的差距还是有的，如果电脑 CPU 性能较低，或者方法中存在内存操作，这个差距会更大。

> 注意：因为"计算斐波那契数列第 n 项"这个算法题目仅仅只是数值运行，对于这 2 个算法来说太 easy 了，都是毫秒级别的，所以，需要取较后的元素这样计算量会多一点才能看出差距，同时因为递归过多会出现内存溢出，因此 n 的取值也不能太大，测试 15000 会内存溢出，12000 则不会。

既然递归有这种缺点，那么我们以后就杜绝使用递归算法吧？当然不行，递归也有一个很大的优点，那就是代码逻辑理解容易，既然这样，那有没有办法让递归算法的性能跟迭代算法一样呢？还真有，Kotlin 提供了 `tailrec` 关键字，可以让 `尾递归算法` 在编译期自动进行代码优化，从而解决尾递归算法的缺点。我们将 fibIter() 加上 `tailrec` 关键字：

```kotlin
fun fib2(n: Int): Int {
    return fibIter(1, 1, n);
}

// 只加了 tailrec 关键字
tailrec fun fibIter(a: Int, b: Int, n: Int): Int {
    return if (n == 0) a else fibIter(b, a + b, n - 1)
}
```

再来测试 fib2() 与 fib3() 两个算法的耗时情况：

```kotlin
fun main(args: Array<String>) {
    timeConsume {
        println(fib2(50000))
    }
    // -1256600222
    // begin = 1612370134450ms , end = 1612370134451ms , 耗时 1ms

    timeConsume {
        println(fib3(50000))
    }
    // -1256600222
    // begin = 1612370134452ms , end = 1612370134453ms , 耗时 1ms
}
```

这原本传入 15000 就会出现内存溢出的尾递归算法 fib2()，现在居然能传入 50000 了，耗时也与迭代算法 fib3() 一样，这就是 `tailrec` 关键字的厉害之处。

> 注意：`tailrec` 关键字只能优化尾递归算法，其它递归算法无法优化。