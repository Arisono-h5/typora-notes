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

Kotlin教程笔记(23) -作用域函数





# Kotlin - 作用域函数



## [#](https://fullstackaction.github.io/pages/ea91be/#作用域函数)作用域函数

Kotlin 提供了一系列的作用域函数，可以在函数形成的临时作用域中对象上下文执行代码块，这些作用域函数共有 5 个：`let`、`with`、`run`、`apply`、`also`，它们区别有 2 个：

- 对象上下文在作用域名中的使用（this 还是 it）
- 作用域函数的返回结果（上下文对象 还是 Lambda 表达式结果）

### [#](https://fullstackaction.github.io/pages/ea91be/#let)let

`let` 经常用于非空值执行代码块，通过与安全操作符 `?` 组合成 `?.let` 进行安全的非空代码操作：

- 对象上下文：it
- 返回值：lambda 表达式结果

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6)

    list?.let { it ->
        println(it[0]) // 1
        it.forEach(::println) // 1 2 3 4 5 6
    }

    val ele1 = list.let { it[5] }.let { it * 2 }
    println(ele1) // 12
}
```

另外，还有一种经常使用 `let` 的场景，那就是懒得给变量命名，使用 `it` 代替。

### [#](https://fullstackaction.github.io/pages/ea91be/#with)with

`with` 不是一个扩展函数，所以 `不能使用 对象.with` 的方式来执行！！！ `with` 接收 2 个参数，参数 1 是 receiver，即上下文对象，在临时作用域中可以使用 `this` 代替使用：

- 对象上下文：this
- 返回值：lambda 表达式结果

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6)
    with(list) {
        println(this[0]) // 1
        // this.forEach(::println) // this可以省略
        forEach(::println) // 1 2 3 4 5 6
    }

    val ele1 = with(list) { this[5] }
    println(ele1) // 6
}
```

> `with` 可以这么理解记忆：对于这个对象，进行以下操作。

### [#](https://fullstackaction.github.io/pages/ea91be/#run)run

`run` 其实就是 `with` 的扩展函数版本，除了调用方式有区别，其他的都与 `with` 一模一样：

- 对象上下文：this
- 返回值：lambda 表达式结果

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6)
    list.run {
        println(this[0]) // 1
        // this.forEach(::println) // this可以省略
        forEach(::println) // 1 2 3 4 5 6
    }

    val ele1 = list.run { this[5] }
    println(ele1) // 6
}
```

不过，`run` 还有个非扩展函数版本，`非扩展run` 有点类似于一个纯粹代码块的作用，相比 `扩展run` 少了一个对象上下文：

```kotlin
fun main(args: Array<String>) {
    val list = listOf(1, 2, 3, 4, 5, 6)
    run {
        // 没有上下文
        list.forEach { println(it) } // 1 2 3 4 5 6
    }
    val ele1 = run { list[5] }
    println(ele1) // 6
}
```

### [#](https://fullstackaction.github.io/pages/ea91be/#apply)apply

`apply` 接收对象上下文，最终也返回对象上下文，常用于对对象进行配置：

- 对象上下文：this
- 返回值：上下文对象

```kotlin
fun main(args: Array<String>) {
    val list = mutableListOf(1, 2, 3, 4, 5, 6)
    list.apply {
        this.add(0, 0)
    }.apply {
        add(0, -1)
    }

    list.forEach(::println) // -1 0 1 2 3 4 5 6
}
```

> `apply` 可以这么理解记忆：对于这个对象，进行以下配置。

### [#](https://fullstackaction.github.io/pages/ea91be/#also)also

`also` 对于执行一些将上下文对象作为参数的操作很有用。对于需要引用对象而不是其属性与函数的操作，或者不想屏蔽来自外部作用域的 `this` 引用时，请使用 `also`。

- 对象上下文：it
- 返回值：上下文对象

```kotlin
fun main(args: Array<String>) {
    val list = mutableListOf(1, 2, 3, 4, 5, 6)
    list.also {
        it.add(0, 0)
    }.also {
        it.add(0, -1)
    }
    list.forEach(::println) // -1 0 1 2 3 4 5 6
}
```

## [#](https://fullstackaction.github.io/pages/ea91be/#总结)总结

作用域函数的目的是一样的，只是彼此之间在使用上存在一些细微的区别：

- 作用：生成一个临时作用域，并在该作用域名中对对象上下文进行操作。
- 差别：对象上下文在临时作用域中的使用（this 或 it），以及作用域的返回值（对象上下文 或 Lambda 表达式结果）。

正是因为这些细微区别，才让人觉得有些混乱，引用 Kotlin 官方文档的汇总表格，可以帮助我们直观的理清这些区别：

| 函数  | 对象引用 | 返回值            | 是否是扩展函数             |
| :---- | :------- | :---------------- | :------------------------- |
| let   | it       | Lambda 表达式结果 | 是                         |
| run   | this     | Lambda 表达式结果 | 是                         |
| run   | -        | Lambda 表达式结果 | 不是：调用无需上下文对象   |
| with  | this     | Lambda 表达式结果 | 不是：把上下文对象当做参数 |
| apply | this     | 上下文对象        | 是                         |
| also  | it       | 上下文对象        | 是                         |

以下是根据预期目的选择作用域函数的简短指南：

- 对一个非空（non-null）对象执行 lambda 表达式：let
- 将表达式作为变量引入为局部作用域中：let
- 对象配置：apply
- 对象配置并且计算结果：run
- 在需要表达式的地方运行语句：非扩展的 run
- 附加效果：also
- 一个对象的一组函数调用：with

> 文章部分引用自 Kotlin 官方文档：https://www.kotlincn.net/docs/reference/scope-functions.html