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



  Kotlin教程笔记(6) - 函数与Lambda表达式

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABH1JREFUSA3tVl1oHFUUPmdmd2ltklqbpJDiNnXFmgbFktho7YMPNiJSSZM0+CAYSkUELVhM6YuwIPpgoOKDqOBDC0XE2CQoNtQXBUFTTcCi+Wlh1V2TQExsUzcltd3M9Tt3ZjZzZ2fT+OJTL8yeM+eee757fmeJbq//KQL8X3DUSFOcfr7cRsRtxNQMWueeVzOkaITIGqQHNg5y8+jNW9ldM7A6nTpAjuolUikAwq7CE3WcM2RRDz+XGVgN3FptU/aUSlvq9Pa3iZ1+sgAqJyyAFqkipd9dqiwHF3P65YycLWc/6sqGrvoEoIp6DOFaX5h6+dnfjkWprwqsPk0dUGq5vySwDImC10KxFHgGL1SWoc92O3eVht09qdXNH11I2SsTsJYqMWzihqGMi+A+Garf3BAuuLI5oGlULyNfyB/HYNujwktOfRrMr5t77NmevqaUopx0grnKAyvVpmwUDB4x6FPXuGvYLTDwWsejwgtgkYKPqRJg8SV6xaiZ3ZTppGneS4yfH5/66fZSDHv+QZci/+h5c5UHtpy67JUqGppM0sh0Nc1dW6/N1W5Yoqat8/TU/VnadmdeW2PLLSyh0cvxBs3KbqTmwYPpxN4do/mzE8nEpvX/UMu2Wbp74zUAK5q6WkHns7V0eWkdPbPzd3rxkTGybadYySumVzhcaJFbs5UrEkQ/+CK8gF5dnh/6ciIZ73gwQ927L1IitoxKLXYP3SjYdOrHHfTZhRRlFyrorafPk20B3HPD1y2G3qKZME5Jcf3t/HUC13/8tSd++vqFveMUTwAUxSUFI1QekR1+bIze3D9MF2aq6cPvG72CgnldWCFqyRw3lwH8ZMerjTD9ElRO7Gv44wNpC90aASqGfVlz/Rx17srQ57/UU26hkhQqUB7dBR71WmzQhHUnblGmVOEw0jhbV1n9OlXUDCIRGaNV5Jp43N516fN7JmnTHdfp7Hgy0luO4aMhtkLL8Bi3bUWYvzh5Mn1dTxrL6QmGuRhGL/TiTTxRoEdTszSaq9GR0NGA3KdkOz3hqSV3MIDhQ5IVX/Ivx3umBti2es2h4eZby7x8br1rkf7Mo90AqC8aQ3sJeNzqFRu+vSANAQe3PL7l0HGOAdwDCeZYvNKeoZp1Qfs6Aipndh86HmFRi0LAnEO47wsqM6cdfjh3jBPUzhZy7nvlUfFsamED1VQt6aISHVymXZ/B2aCtIG8AI8xfobj2d3en1wWVhOeHELKmLQ1s211s88comkv4UCwWyF787mJdYXtNfhKAXVqnKTq8QZvGAGGOfaTo5pGZ/PwbUCr5+DPr/1J92JNHr9aOl/F3iI5+O1nfybsGxoimvZ3ViWSluDITw3P37mypheDIPY0tw7+O/5ApbkYw+zpfaUVu32Pi98+defdUhEpZkRFq0aqyNh9FuL9hpYbEm6iwi0z2REd09ZmyENEbuhjDWzKvZXTqKYaBIr3tt5kuPtQBZFvEUwHt60vfCNu41XsksH9Ij1BMMz1Y0OOunHNShFIP5868g5zeXmuLwL9T4b6Q2+KejgAAAABJRU5ErkJggg==)Kotlin - 函数与Lambda表达式



## [#](https://fullstackaction.github.io/pages/ee17d1/#函数)函数

函数是以特定功能组织起来的代码块，函数定义格式如下：

- fun [函数名](https://fullstackaction.github.io/pages/ee17d1/[参数列表]):[返回值类型]{[函数体]}
- fun [函数名](https://fullstackaction.github.io/pages/ee17d1/[参数列表]) = [表达式]

```kotlin
fun sum(arg1: Int, arg2: Int): Int {
    return arg1 + arg2
}
```

如果函数方法体只有一行代码，那可以将 `{}` 改为 `=`，去掉 `return`，表达式的值将作为函数返回值：

```kotlin
fun sum(arg1: Int, arg2: Int) = arg1 + arg2
```

### [#](https://fullstackaction.github.io/pages/ee17d1/#默认返回值类型)默认返回值类型

任何函数都是有返回值的，一般函数方法体中会使用 `return` 将结果进行返回，但有的函数就是不需要返回结果，此时可以将 `return` 省略：

```kotlin
fun main(args: Array<String>) {
    ...
}
```

即使函数方法体中没有 `return` 返回结果，但函数还是有返回值类型的，默认的返回值类型就是 `Unit` ，但一般 `Unit` 会省略不写：

```kotlin
fun main(args: Array<String>): Unit {
    ...
}
```

### [#](https://fullstackaction.github.io/pages/ee17d1/#匿名函数)匿名函数

匿名函数就是没有名字的函数，但是需要赋值给一个变量，否则 IDE 会报错：

```kotlin
// 变量sum，它的值是一个函数
val sum = fun(arg1: Int, arg2: Int): Int {
    return arg1 + arg2
}

fun main(args: Array<String>): Unit {
    val result = sum(1, 2)
    println(result) // 3
}
```

> 此时 `sum` 是一个变量，只是它的值是一个函数。

## [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-表达式)Lambda 表达式

Lambda 表达式也是一种"匿名函数"，不过格式上会有些不同：

- {[参数列表] -> [函数体, 最后一行是返回值]}

```kotlin
val sum = { arg1: Int, arg2: Int ->
    println("$arg1 + $arg2 = ${arg1 + arg2}")
    arg1 + arg2
}

fun main(){
    println(sum(1, 2)) // 3
}
```

> Lambda 表达式的返回值是表达式中最后一行的结果。

### [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-的类型)Lambda 的类型

Kotlin 中，不管是常量或是变量，都会有各自的类型，如：Human，那如果一个变量的值是 Lambda 表达式，那它的类型是什么呢？没错，就是 Lambda 类型：

- () -> Unit : 无参，返回值为 null
- (Int) -> Int : 传入整型，返回一个整型
- (String, (String)->String) -> Boolean : 传入字符串、Lambda 表达式，返回 Boolean

```kotlin
// lambda的类型：(Int,Int) -> Int
val sum = { arg1: Int, arg2: Int -> arg1 + arg2 }

// lambda的类型：() -> Unit
val printlnHello = {
    println("Hello")
}
```

### [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-表达式的调用)Lambda 表达式的调用

与匿名函数一样，值为 Lambda 表达式的变量可通过以下两种方式执行 Lambda 表达式：

- 用 `()` 进行调用
- 用 `invoke()` 调用

```kotlin
println(sum(1, 2)) // 3
println(sum.invoke(1, 2)) // 3
```

> 实际上，`()` 就是 `invoke()`。

### [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-表达式的简化)Lambda 表达式的简化

- 函数参数调用时最后一个 Lambda 可以移出去
- 函数参数只有一个 Lambda，调用时小括号可省略
- Lambda 只有一个参数可默认为 it
- 入参、返回值与形参一致的函数可以用函数引用的方式作为实参传入

我们先来看一下 Array 数组的一个扩展函数 `forEach`：

```kotlin
/**
 * Performs the given [action] on each element.
 */
public inline fun <T> Array<out T>.forEach(action: (T) -> Unit): Unit {
    for (element in this) action(element)
}
```

这个扩展函数为 Array 类扩展了一个 `forEach` 方法，需要传入一个参数 action，其类型是 `(T) -> Unit` 的 Lambda 类型，返回值为 Unit（即没有返回值），方法体中使用 `for-in` 对数组进行遍历，同时使用参数 action 处理遍历的元素。

> 关于扩展函数这里不展开细讲，后续文章会专门解读，这里只需要知道 `forEach` 的功能即可。

```kotlin
val args = arrayOf("1", "2", "3", "l", "q", "r")

// 使用 for-in 遍历数组并打印元素内容
for (arg in args) {
    println(arg)
}
```

这是一个普通的数组遍历打印功能，上面已经使用 `for-in` 实现了，下面就使用前面学到的扩展函数 `forEach` 来处理：

```kotlin
// Lambda完整写法
args.forEach({ it -> println(it) })

// Lambda简化写法
args.forEach({ println(it) })

// 重命名参数it，此时ele不可省略
args.forEach({ ele -> println(ele) })
```

Lambda 只有一个参数时可默认为 it，当然了，如果你不想使用 it 也是可以改名的，但如果改名了，就不能将其省略。除了省略默认参数 it，还有如下方法简化 Lambda 表达式：

```kotlin
// 函数参数调用时最后一个 Lambda 可以移出去
args.forEach(){ println(it) }

// 函数参数只有一个 Lambda，调用时小括号可省略
args.forEach{ println(it) }
```

以上就是 Kotlin 中 Lambda 表达式的简化流程，以后开发中会经常遇到最后的简化写法。

### [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-表达式与函数引用)Lambda 表达式与函数引用

再回头看看这个扩展函数 `forEach` 的参数 action 的类型：

```kotlin
// action: (T) -> Unit
public inline fun <T> Array<out T>.forEach(action: (T) -> Unit): Unit {
    for (element in this) action(element)
}
```

再看看 `println()` 的定义：

```kotlin
// println: (Any?) -> Unit
public actual inline fun println(message: Any?) {
    System.out.println(message)
}
```

不难发现 `println()` 的定义完全符合 action 的 Lambda 类型要求，于是此场景下还可以将 `forEach` 参数 action 需要的 Lambda 表达式转换成 `println` 函数的引用，引用函数需要使用 `::` ：

```kotlin
// 入参、返回值与形参一致的函数可以用函数引用的方式作为实参传入
args.forEach(::println)
```

### [#](https://fullstackaction.github.io/pages/ee17d1/#lambda-表达式跳出-foreach)Lambda 表达式跳出 forEach

> 这里严重超纲，看不明白也无所谓，可以先跳过～

需求：遍历数组时，当发现元素是 q 时，中断循环。

```kotlin
val args = arrayOf("1", "2", "3", "l", "q", "r")
for (arg in args) {
    if (arg == "q") break
    println(arg)
}
println("The End") // 1 2 3 l The End
```

使用 `for-in` 配置 `break` 即可实现该功能，下面试试使用 `forEach`：

```kotlin
fun main() {
    val args = arrayOf("1", "2", "3", "l", "q", "r")
    args.forEach {
        if (it == "q") break // IDE报错：'break' and 'continue' are only allowed inside a loop
        print("$it ")
    }
    println("The End")
}
```

是的，Lambda 表达式仅仅是一个表达式而已，不是循环体，所以无法使用 `break` 和 `continue`，那这里为了中断遍历只能使用 `return` 了：

```kotlin
fun main() {
    val args = arrayOf("1", "2", "3", "l", "q", "r")
    args.forEach { // 1 2 3 l
        if (it == "q") return
        print("$it ")
    }
    println("The End") // 不会被执行
}
```

乍一看，这里使用了 `return` 实现了中断遍历，但其实 "The End" 没有输出，说明 return 并非中断遍历，而是中断了当前的 main 函数，原因还是那个：Lambda 表达式仅仅只是表达式而已。

针对 Lambda 表达式，Kotlin 提供了标签式返回，可以在 Lambda 表达式中使用 `return@xxx` 方法跳出遍历，那使用这个来试试看：

```kotlin
fun main() {
    val args = arrayOf("1", "2", "3", "l", "q", "r")
    args.forEach {
        if (it == "q") return@forEach
        print("$it ")
    }
    println("The End") // 1 2 3 l r The End
}
```

程序跳过 q 继续往下执行了，这又是什么情况？这还是要回到 Lambda 表达式的本质，`forEach`里的 Lambda 表达式其实就是一个函数体，因此标签式返回 `return@xxx` 对这个函数体的退出只能退出当前的调用罢了。那就没有办法使用 `forEach` 实现这个需求了吗？是的，单靠 `forEach` 不行，需要配置 StreamApi 对数组进行过滤后再遍历：

```kotlin
val args = arrayOf("1", "2", "3", "l", "q", "r")
args.takeWhile { it != "q" }.forEach { print("$it ") }
println("The End")　// 1 2 3 l The End
```