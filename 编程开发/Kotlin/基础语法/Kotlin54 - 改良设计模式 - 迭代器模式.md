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

Kotlin教程笔记(54) -  改良设计模式 - 迭代器模式



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 改良设计模式 - 迭代器模式



## [#](https://fullstackaction.github.io/pages/78c482/#一、前言)一、前言

- 迭代器模式
  - 作用：将遍历和实现分离开来，在遍历的同时不需要暴露对象的内部表示
  - 举例：ArrayList、LinkedList、TreeSet 均可通过 `iterator()` 方法获取到迭代器对元素进行遍历，不需要关心元素存放在哪种数据结构中。

## [#](https://fullstackaction.github.io/pages/78c482/#二、使用迭代器模式)二、使用迭代器模式

- 例子：遍历图书
- 重点：`Iterator`、`Iterable` 接口的使用

无论 Java 还是 Kotlin，都有 `Iterator` 接口，基于 `Iterator` 接口实现迭代器模式的类，可以使用 `for-in` 或 `forEach` 对其进行快速遍历，这里我们让一个自定义的图片列表（`BookList`）实现迭代器功能：

```kotlin
/**
 * 图书
 *
 * @author GitLqr
 */
data class Book(val name: String)

/**
 * 图书集（迭代器模式）：基于 Iterator，只能遍历一次
 *
 * @author GitLqr
 */
class BookList(val books: List<Book>) : Iterator<Book> {
    private val iterator: Iterator<Book> = books.iterator()

    override fun hasNext() = iterator.hasNext()

    override fun next() = iterator.next()
}

// 使用
val bookList = BookList(listOf(Book("Kotlin核心编程"), Book("深入理解Java虚拟机")))
for (book in bookList) {
    println(book.name)
}
bookList.forEach { book -> println(book.name) }

// 输出
Kotlin核心编程
深入理解Java虚拟机
```

可以看到 `BookList` 确实能使用 `for-in` 或 `forEach` 语法进行遍历了，但是结果却只输出一遍，通过源码可以知道 `Iterator` 是一次性且不可逆的：

```kotlin
public interface Iterator<out T> {
    /**
     * Returns the next element in the iteration.
     */
    public operator fun next(): T

    /**
     * Returns `true` if the iteration has more elements.
     */
    public operator fun hasNext(): Boolean
}
```

如果希望每次使用 `for-in` 或 `forEach` 语法都能从头遍历的话，很简单，只需要保证每次遍历使用的是独立的迭代器实例即可，这时，我们可以让自定义类 `BookList` 改为实现 `Iterable` 接口：

```kotlin
/**
 * 图书集（迭代器模式）：基于 Iterable，能遍历多次
 *
 * @author GitLqr
 */
class BookList(val books: List<Book>) : Iterable<Book> {
    override fun iterator(): Iterator<Book> = books.iterator()
}

// 使用
val bookList = BookList(listOf(Book("Kotlin核心编程"), Book("深入理解Java虚拟机")))
for (book in bookList) {
    println(book.name)
}
bookList.forEach { book -> println(book.name) }

// 输出
Kotlin核心编程
深入理解Java虚拟机
Kotlin核心编程
深入理解Java虚拟机
```

为防止混淆，这里对 `Iterator`、`Iterable` 各自的职能做下总结：

- `Iterator`：迭代器，迭代器模式的核心实现（本质）
- `Iterable`：可迭代的，每次获取一个新的迭代器（让 cursor 重新开始）

## [#](https://fullstackaction.github.io/pages/78c482/#三、改良迭代器模式)三、改良迭代器模式

- 例子：遍历图书
- 重点：重载运算符(`iterator`)、扩展函数

在 Kotlin 中，除了可以使用 `Iterator` 或 `Iterable` 来实现迭代器模式外，还可以通过让任意类重载运算符 `iterator()` 来实现 `Iterable` 接口相同的功能：

```kotlin
/**
 * 图书集（迭代器模式）改良：重载 iterator 运算符
 *
 * @author GitLqr
 */
class BookList(val books: List<Book>) {
    operator fun iterator(): Iterator<Book> = books.iterator()
}

// 使用
val bookList = BookList(listOf(Book("Kotlin核心编程"), Book("深入理解Java虚拟机")))
for (book in bookList) {
    println(book.name)
}
// bookList.forEach { book -> println(book.name) } // 语法错误，无法编译通过
```

使用【重载运算符 `iterator()`】与【实现 `Iterable` 接口】这两种方式来实现的迭代器模式，在代码结构上差不多，但是前者会让 `forEach` 无法使用，因为 `forEach` 是 `Iterator` 和 `Iterable` 的扩展函数，与运算符 `iterator()` 无关：

```kotlin
// Iterators.kt
public inline fun <T> Iterator<T>.forEach(operation: (T) -> Unit): Unit {
    for (element in this) operation(element)
}

// _Collections.kt
@kotlin.internal.HidesMembers
public inline fun <T> Iterable<T>.forEach(action: (T) -> Unit): Unit {
    for (element in this) action(element)
}
```

不过呢，运算符 `iterator()` 是一个方法，它的返回值类型是 `Iterator<T>` ，所以我们可以变相的使用 `forEach`：

```kotlin
bookList.iterator().forEach { book -> println(book.name) }
```

另外，Kotlin 还支持用扩展函数的方式来重载运算符，于是，上述代码还可以变成这样：

```kotlin
/**
 * 图书集（迭代器模式）改良：第三方类扩展重载 iterator 运算符
 *
 * @author GitLqr
 */
class BookList(val books: List<Book>)
operator fun BookList.iterator(): Iterator<Book> = this.books.iterator()

// 使用
for (book in bookList) {
    println(book.name)
}
bookList.iterator().forEach { book -> println(book.name) }
```

你可能会觉得，这也算改良吗？像 `forEach` 这种常见的遍历方式还得变相使用才行，感觉有点多余啊，确实如此，与其说是改良，倒不如说是 Kotlin 中迭代器模式的另一种实现思路。不过，假设 `BookList` 是第三方库中的类，你无法对其源码进行修改，这就意味着【实现 `Iterable` 接口】这种方式行不通，这时，不妨考虑一下【重载运算符 `iterator()`】（配合扩展函数）的方式。