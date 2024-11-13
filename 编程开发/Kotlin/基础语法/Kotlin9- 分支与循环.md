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



  Kotlin教程笔记(9) - 分支与循环



# Kotlin - 分支与循环



## [#](https://fullstackaction.github.io/pages/9e247e/#分支语句)分支语句

Kotlin 中的分支语句有两种，分别是 `if...else` 和 `when`。

### [#](https://fullstackaction.github.io/pages/9e247e/#if-表达式)if 表达式

Kotlin 可以像 Java 那样，使用 `if...else` 语句，通过判断条件来修改变量的值：

```kotlin
var name = ""
if (local == "en") {
    name = "lqr"
} else {
    name = "吴彦祖"
}
```

但这种写法还不够简洁，Kotlin 对 `if...else` 进行发加强，支持 `if表达式` ，可以对上述代码进行简化：

```kotlin
val name = if (local == "en") "lqr" else "吴彦祖"
```

> Kotlin 中没有三元运算符，不过可以使用 if 表达式来处理。

### [#](https://fullstackaction.github.io/pages/9e247e/#when-表达式)when 表达式

Kotlin 中的 `when` 相当于 Java 中的 `switch`，`when` 语句用于处理多分支条件判断，代码更清晰：

```kotlin
val x = 5
when (x) {
    5 -> println("x is 5")
    is Int -> println("Hello $x")
    in 1..100 -> println("$x is in 1..100")
    !in 1..100 -> println("$x is not in 1..100")
    args[0].toInt() -> println("x == args[0]")
}
```

可以看到 `when` 的条件分支很强大，除了支持值判断，甚至还支持表达式判断。与 `if表达式` 一样，Kotlin 也支持 `when表达式`：

```kotlin
val hero = when (local) {
    "en" -> "Hero"
    "zh" -> "英雄"
    "fr" -> "Un héros"
    "de" -> "Held"
    else -> "未知"
}
println(hero)
```

与 Java 的 switch 相比，Kotlin 的 when 更加强大：

- 加强版 switch，支持任意类型
- 支持纯表达式条件分支（类似 if）
- `when表达式` 要求完备性，需要将所有情况都列出来

## [#](https://fullstackaction.github.io/pages/9e247e/#循环语句)循环语句

Kotlin 中的循环语句大体有两种：`for循环` 和 `while循环`。

### [#](https://fullstackaction.github.io/pages/9e247e/#for-循环)for 循环

基本写法：`for(element in elements)...`

```kotlin
for (arg in args) {
    println(arg)
}
```

`for` 循环背后的运行机制是先通过 `args.iterator()` 获取到迭代器 `Iterator`，再结合迭代器的 `next()` 和 `hasNext()` 来处理数组中的元素，所以循环的关键点是 `Iterator`。

> Java 中 for 循环的原理也是迭代器，但不同的是，Java 的数组需要实现 `Iterable<T>` 接口，并实现`iterator()`，而 Kotlin 中则是任意类重写 `operator fun iterator()` 。

数组 `Array` 支持在 `for` 循环的同时获取索引值：

```kotlin
// 带索引的for循环
for ((index, value) in args.withIndex()) {
    println("$index : $value")
}

// 上面写法等价于下面写法
for (indexValue in args.withIndex()) {
    println("${indexValue.index} : ${indexValue.value}")
}
```

数组 `Array` 的 `withIndex()` 方法返回的是 `Iterable<IndexedValue<T>>`，其中 `IndexedValue` 是 `data class` ，支持使用 `()` 提取属性：

```kotlin
public data class IndexedValue<out T>(public val index: Int, public val value: T)
```

### [#](https://fullstackaction.github.io/pages/9e247e/#while-循环)while 循环

除了 for 循环，Kotlin 还支持 while 循环，while 循环格式分两种，两者区别如下：

- while：先判断再执行
- do-while：先执行再判断

```kotlin
var x = 5
while (x > 0) {
    print("$x ") // 5 4 3 2 1
    x--
}

var x = 5
do {
    print("$x ") // 5 4 3 2 1
    x--
} while (x > 0)
```

### [#](https://fullstackaction.github.io/pages/9e247e/#跳过和终止循环)跳过和终止循环

Kotlin 也支持跳过和终止循环语句的指令，分别是：

- `continue` ：跳过当前循环
- `break` ：终止当前循环

```kotlin
val args = intArrayOf(1, 2, 3, 4, 5)
for (arg in args) {
    if (arg == 2) continue
    if (arg == 4) break
    print("$arg ") // 1 3
}
```

> 开发中也常用 return 来终止循环，但它与 break 不同的是，return 实际上是中止方法的执行。

当有多层循环嵌套需要根据条件　跳过或终止内外套循环语句时，可以使用标签：

```kotlin
val args = intArrayOf(1, 2, 3, 4, 5)
Outter@ for (arg in args) {
    println("outter: $arg")
    var i = arg
    print("inner: ")
    Inner@ while (i > 0) {
        if (arg == 2) break@Inner // 当外循环元素为2时，跳过while，进行下次for
        if (arg == 4) break@Outter // 当外循环元素为3时，直接跳出for
        print("$i ")
        i--
    }
    println()
}
```