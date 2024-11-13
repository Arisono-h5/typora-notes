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

Kotlin教程笔记(22) -常见高阶函数



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 常见高阶函数



## [#](https://fullstackaction.github.io/pages/defa2f/#foreach)forEach

高阶函数 `forEach` 是可迭代对象的扩展方法，接收函数类型是 `(T) -> Unit` 的参数 action，`forEach` 会将 action 这个函数作用于可迭代对象中的每个元素，这是源码：

```kotlin
/**
 * Performs the given [action] on each element.
 */
@kotlin.internal.HidesMembers
public inline fun <T> Iterable<T>.forEach(action: (T) -> Unit): Unit {
    for (element in this) action(element)
}
```

根据 forEach 的入参要求，我们给其传递一个 lambda 表达式或是函数引用：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6, 7, 8)
    // list.forEach { it -> println(it) } // it可以省略
    list.forEach { println(it) }
    list.forEach(::println)
    list.forEachIndexed { index, i -> println("index=$index, value=$i") }
}
```

> `forEachIndexed` 相比 `forEach` 只是多了索引 index。

## [#](https://fullstackaction.github.io/pages/defa2f/#map)map

高阶函数 `map` 也是可迭代对象的扩展方法，根据 `map` 的源码与注释，我们知道 map 接收一个类型是 `(T) -> R` 的参数 transform，`map` 会将 transform 作用于可迭代对象中的每个元素，并最终返回一个新的集合 List：

```kotlin
/**
 * Returns a list containing the results of applying the given [transform] function
 * to each element in the original collection.
 *
 * @sample samples.collections.Collections.Transformations.map
 */
public inline fun <T, R> Iterable<T>.map(transform: (T) -> R): List<R> {
    return mapTo(ArrayList<R>(collectionSizeOrDefault(10)), transform)
}
```

借助 map 的功能，我们可以将一个数组  “映射” 成另一个数组，这在日常开发很有用：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6, 7, 8)

    // 将int数组中的元素经过某种运算形成一个新的int数组
    val newList = list.map { it * 2 + 3 }
    newList.forEach(::println)

    // 将int转成double
    val newList2 = list.map(Int::toDouble) // (Int) -> Double
    newList2.forEach(::println)
}
```

> 注意：toDouble()是 Int 类中的一个方法，在函数引用部分已经讲过，当使用 `类名::方法名` 这种方式引用一个成员方法时，会自动在函数类型的参数列表第 1 位多出一个接收者 `Receiver`，用于接收类实例对象 ，刚好 toDouble()没有参数列表，因此 `Int::toDouble` 对应的函数类型是 `(Int) -> Double`，符合高阶函数 map 的参数要求。

## [#](https://fullstackaction.github.io/pages/defa2f/#flatmap)flatMap

高阶函数 `flatMap` 比 `map` 高一个维度，可以将可迭代对象中的每个可迭代对象进行处理，最终返回一个 `扁平化` 的可迭代对象，注意参数 transform 的函数类型是 `(T) -> Iterable<R>`：

```kotlin
/**
 * Returns a single list of all elements yielded from results of [transform] function being invoked on each element of original collection.
 *
 * @sample samples.collections.Collections.Transformations.flatMap
 */
public inline fun <T, R> Iterable<T>.flatMap(transform: (T) -> Iterable<R>): List<R> {
    return flatMapTo(ArrayList<R>(), transform)
}
```

什么是 `扁平化` ，直观的说，就是胖变瘦，多维变一维：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(
        8..10,
        1..3,
        98..100
    )
    val flatList = list.flatMap { it } // it->it，这里同时也是 (Iterable) -> Iterable
    flatList.forEach(::println) // 这时的 flatList 就相当于 [8,9,10,1,2,3,98,99,100]
}
```

`flatMap` 除了 `扁平化` 这个特性外，也拥有 map 的特性，可以将可迭代对象中的元素进行转换处理：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(
        8..10,
        1..3,
        98..100
    )
    val flatList2 = list.flatMap { intRange ->
        intRange.map { intElement -> "No. $intElement " }　// 把Int转成String
    }
    flatList2.forEach(::print) // No. 8 No. 9 No. 10 No. 1 No. 2 No. 3 No. 98 No. 99 No. 100
}
```

## [#](https://fullstackaction.github.io/pages/defa2f/#filter)filter

高阶函数 `filter` 可以将可迭代对象进行过滤，只有满足 predicate 过滤条件的元素(即 return true)才会被 "留下"：

```kotlin
/**
 * Returns a list containing only elements matching the given [predicate].
 *
 * @sample samples.collections.Collections.Filtering.filter
 */
public inline fun <T> Iterable<T>.filter(predicate: (T) -> Boolean): List<T> {
    return filterTo(ArrayList<T>(), predicate)
}
```

我们可以使用 `filter` 过滤出数组中的奇数：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6, 7, 8)
    val newList = list.filter { it % 2 == 1 }
    newList.forEachIndexed { index, i -> print(if (index > 0) " $i" else i) } // 1 3 5 7
}
```

## [#](https://fullstackaction.github.io/pages/defa2f/#takewhile)takeWhile

高阶函数 `takeWhile` 会在遇到第一个不符合条件的元素时就结束取数据，留下前面的作为新的集合返回：

```kotlin
/**
 * Returns a list containing first elements satisfying the given [predicate].
 *
 * @sample samples.collections.Collections.Transformations.take
 */
public inline fun <T> Iterable<T>.takeWhile(predicate: (T) -> Boolean): List<T> {
    val list = ArrayList<T>()
    for (item in this) {
        if (!predicate(item))
            break
        list.add(item)
    }
    return list
}
```

我们可以使用 takeWhile 筛选出前面满足条件的元素：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 1, 2, 3, 5, 8, 13, 21)

    var newList = list.takeWhile { it % 2 == 1 } // 筛选出前面的奇数
    newList.forEachIndexed { index, i -> print(if (index > 0) " $i" else i) } // 1 1

    newList = list.takeWhile { it < 5 } // 筛选出前面小于5的数
    newList.forEachIndexed { index, i -> print(if (index > 0) " $i" else i) } // 1 1 2 3
}
```

## [#](https://fullstackaction.github.io/pages/defa2f/#reduce)reduce

高阶函数 `reduce` 会从第一个元素开始累加，并从左到右将 operation 函数应用于当前累加值和每个元素：

```kotlin
/**
 * Accumulates value starting with the first element and applying [operation] from left to right to current accumulator value and each element.
 *
 * @sample samples.collections.Collections.Aggregates.reduce
 */
public inline fun <S, T : S> Iterable<T>.reduce(operation: (acc: S, T) -> S): S {
    val iterator = this.iterator()
    if (!iterator.hasNext()) throw UnsupportedOperationException("Empty collection can't be reduced.")
    var accumulator: S = iterator.next()
    while (iterator.hasNext()) {
        accumulator = operation(accumulator, iterator.next())
    }
    return accumulator
}
```

我们可以用 `reduce` 来处理一些累加的操作，如计算 1 到 8 之间所有的数进行求和：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6, 7, 8)
    val result = list.reduce { acc, i -> acc + i }
    println(result) // 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 = 36
}
```

## [#](https://fullstackaction.github.io/pages/defa2f/#fold)fold

高阶函数 `fold` 跟 `reduce` 差不多，只是 `fold` 多了一个初始值，后续处理与 `reduce` 一样：

```kotlin
/**
 * Accumulates value starting with [initial] value and applying [operation] from left to right to current accumulator value and each element.
 */
public inline fun <T, R> Iterable<T>.fold(initial: R, operation: (acc: R, T) -> R): R {
    var accumulator = initial
    for (element in this) accumulator = operation(accumulator, element)
    return accumulator
}
```

我们可以 fold 来计算在 100 的基础上，再累加 1 到 8 的和：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6, 7, 8)
    val result = list.fold(100, { acc, i -> acc + i })
    println(result) // 100 + 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 = 37
}
```