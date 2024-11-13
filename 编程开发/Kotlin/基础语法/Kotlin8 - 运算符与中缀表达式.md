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



  Kotlin教程笔记(8) - 运算符与中缀表达式



# Kotlin - 运算符与中缀表达式



## [#](https://fullstackaction.github.io/pages/37adf1/#基本运算符)基本运算符

常见的基本运算符有 `+-*/%^?` ，在 Kotlin 中，这些运算符都会有对应的具名函数：

| 表达式 | 翻译为                         |
| :----- | :----------------------------- |
| a + b  | a.plus(b)                      |
| a - b  | a.minus(b)                     |
| a * b  | a.times(b)                     |
| a / b  | a.div(b)                       |
| a % b  | a.rem(b)、 a.mod(b) （已弃用） |
| a..b   | a.rangeTo(b)                   |

除此之处，还有一些常用的操作符（统称运算符），例如 `in`、`[]`、`()` 等：

| 表达式  | 翻译为         |
| :------ | :------------- |
| a in b  | b.contains(a)  |
| a !in b | !b.contains(a) |
| a[i]    | a.get(i)       |
| a()     | a.invoke()     |

了解更多操作符对应的具名函数，请点击：[https://www.kotlincn.net/docs/reference/operator-overloading.html(opens new window)](https://www.kotlincn.net/docs/reference/operator-overloading.html)

## [#](https://fullstackaction.github.io/pages/37adf1/#操作符重载)操作符重载

根据 Kotlin 官网给出的操作符和与之对应的具名函数，我们可以自定义一个计算复数的类 Complex ：

```kotlin
class Complex(var real: Double, var imaginary: Double) {
    // 复数相加：实部与虚部分别相加
    operator fun plus(other: Complex): Complex {
        return Complex(real + other.real, imaginary + other.imaginary)
    }

    // 复数与整数相加，只处理实部
    operator fun plus(other: Int): Complex {
        return Complex(real + other, imaginary)
    }

    // 复数使用()时，求弦长（三角形的斜边长度）
    operator fun invoke(): Double {
        return Math.hypot(real, imaginary)
    }

    override fun toString(): String {
        return "$real + ${imaginary}i"
    }
}

fun main() {
    val c1 = Complex(3.0, 4.0) // 3 + 4i
    val c2 = Complex(2.0, 7.5) // 2 + 7.5i
    println(c1 + c2) // 5.0 + 11.5i
    println(c1 + 2) // 5.0 + 4.0i
    println(c1()) // 5.0
}
```

一个类的同名运算符重载是可以有多个的，但参数类型或返回值类型要有所区别。

- 何类都可以定义或重载父类的基本运算符
- 运算符重载是通过重载与运算符对应的具名函数来定义
- 运算符重载对参数个数作要求，对参数和返回值类型不作要求
- 不能像 Scala 那样定义任意运算符,如：$在 Kotlin 中就没有与之对应的具名函数。

## [#](https://fullstackaction.github.io/pages/37adf1/#中缀表达式)中缀表达式

上面已经说到了，Kotlin 不能像 Scala 那样定义任意运算符，那有没有办法定义一种具名函数，使其代码的书写跟运算符一样的呢？答案是：使用中缀表达式。

```kotlin
class Book {
    infix fun on(any: Any?): Boolean {
        return false
    }
}

class Desktop

fun main() {
    val book = Book()
    val desktop = Desktop()
    // println(book.on(desktop)) // 中缀表达式 本质还是函数
    println(book on desktop)
}
```

- 中缀表达式是 只有一个参数，且用 `infix` 修饰 的函数
- 中缀表达式的作用是让函数调用时，可以省略 `.` 和 `()`

> 中缀表达式一般只用于 dsl，滥用反而会让代码变得不够清晰。