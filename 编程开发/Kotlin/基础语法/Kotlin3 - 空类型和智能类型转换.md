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

  Kotlin教程笔记(3) - 空类型和智能类型转换



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 空类型和智能类型转换



## [#](https://fullstackaction.github.io/pages/a59099/#空类型)空类型

Kotlin 跟 Java 的最大不同应当就属空类型这点了，使用 Kotlin 开发，IDE 会智能的对可能为空的地方进行报错提示，开发者必须处理该错误，否则连编译都通过不了，从而降低程序 NullPointException 异常的出现几率，所以，一般情况下使用 Kotlin 开发很少见到 NPE 异常。

### [#](https://fullstackaction.github.io/pages/a59099/#非空与可空类型)非空与可空类型

```kotlin
fun getName(): String {
    return "lqr"
}
```

这是一个很普通的函数声明，它指明了函数返回值是一个 String 类型，对此，Kotlin 会认为这是一个不可能返回 null 结果的函数，那如果我就是要返回 null 会怎样？

```kotlin
// IDE报错：Null can not be a value of a non-null type String
fun getName(): String {
    return null
}
```

该 IDE 的报错提示说明了函数返回值类型 String 是一个不能为 null 的值，即非空类型。如果需要函数可以返回 null 的话，需要对函数返回值类型做一点小修改，使其可以用空，这仅仅只需要在返回值类型后面追加 `?` 即可：

```kotlin
fun getName(): String? {
    return null
}
```

综上，Kotlin 的类型声明分为两类（包括但不限于函数返回值类型），分别是：

- 非空类型：单纯声明的类就是非空类型，如：`String`。
- 可空类型：通过在类后面放置 `?` 来声明，如：`String?`。

### [#](https://fullstackaction.github.io/pages/a59099/#可空类型操作符)可空类型操作符

Kotlin 为保证代码空安全，提供了几种处理方式，本节主要陈述其中的 3 种操作符。

> 了解更多 Kotlin 空安全知识，请访问：[https://www.kotlincn.net/docs/reference/null-safety.html(opens new window)](https://www.kotlincn.net/docs/reference/null-safety.html)

#### [#](https://fullstackaction.github.io/pages/a59099/#安全调用操作符)安全调用操作符（`?.`)

以获取字符串长度为例，非空类型变量直接通过 `.length` 即可：

```kotlin
val name: String = "lqr"
println(name.length)
```

而可空类型变量，不仅需要在类型声明时使用 `?` ，在调用可空类型对象的成员变量 `length` 时也需要使用 `?.` 进行处理：

```kotlin
val name: String? = null
println(name?.length) // 输出：null
```

因为 name 的值为 null，所以 `.length` 并不会被执行，因此这代码相当于 `println(null)`，虽然结果是 null，但程序并不会崩溃。

> 安全调用操作符（`?.`)：如果接收者非空，就调用一个方法或访问一个属性，否则不执行。

#### [#](https://fullstackaction.github.io/pages/a59099/#elvis-运算符)Elvis 运算符（`?:`)

日常开发中，我们经常习惯于用一行代码同时处理变量非空或为空的情况，在 Kotlin 中，借助 `if-else` 代码可以这么写：

```kotlin
println(if (getName() != null) getName() else "Default Name")
```

> Java 有三元运算符，而 Kotlin 没有，所以这里只能用 `if-else`。

Kotlin 还提供了 Elvis 运算符（`?:`)，可以对 `if-else` 进行简化：

```kotlin
println(getName() ?: "Default Name")
```

> Elvis 运算符（`?:`)：如果 ?: 左侧表达式非空，elvis 操作符就返回其左侧表达式，否则返回右侧表达式。 请注意，当且仅当左侧为空时，才会对右侧表达式求值。

#### [#](https://fullstackaction.github.io/pages/a59099/#非空断言运算符)非空断言运算符（`!!`)

如果你非常非常确定变量的值绝对不可能为 null，那么你可以在对象调用时使用 `!!` 对其进行转换成非空类型：

```kotlin
val value: String? = "Hello LQR"
println(value!!.length)
```

> 非空断言运算符（`!!`)：将任何值转换为非空类型，若该值为空则抛出异常。

## [#](https://fullstackaction.github.io/pages/a59099/#智能类型转换)智能类型转换

类型转换在开发中很常见，特别是在多态的应用情景里，会使用父类变量接收子类对象，并且可能会需要强转成具体的子类类型以使用特定的子类功能。

```kotlin
open class Parent {}

class Child : Parent() {
    fun getName(): String {
        return "lqr"
    }
}

fun main(args: Array<String>) {
    val man: Parent = Child()
    println((man as Child).getName())
}
```

> Kotlin 里，强转需要使用 `as`　关键字来处理。

当然了，这里的代码处理的很不好，通常在转换前会先判断对象的具体类型后再做强转，以免出现类型转换异常，因此，代码可以修改为：

```kotlin
val man: Parent = Child()
if (man is Child) {
    println(man.getName())
}
```

Kotlin 中使用 `is` 关键字来判断变量类型，`if` 代码块中，man 变量已经被识别为 Child 类型了，因此不再需要显式强转，这就是 Kotlin 的智能类型转换，反观 Java 就显的有些笨笨的了：

```java
Parent man = new Child();
if (man instanceof Child) {
    System.out.println(((Child) man).getName());
}
```

回过头再来看看 `as` 关键字，Kotlin 代码中使用 `as` 进行对象的类型强转，如果我们不先进行类型判断，就直接强制变量类型，一旦被强转的对象类型有误，就必定会抛出`ClassCastException`：

```kotlin
// Exception in thread "main" java.lang.ClassCastException: com.charylin.kotlinlearn.Parent cannot be cast to com.charylin.kotlinlearn.Child
val parent: Parent = Parent()
val child: Child = parent as Child
print(child)
```

还好，Kotlin 的智能类型转换功能为 "直接强转党" 提供了一条出路，那就是使用 `as?`，同时如果变量有显式指定类型的话，需要将其改为可空类型，或者干脆把变量类型声明去掉：

```kotlin
val parent: Parent = Parent()
val child: Child? = parent as? Child
// val child = parent as? Child　// 这种写法也是OK的
print(child)　// 输出：null
```

`as?` 相比 `as` 要智能一些，当强制类型有误会时，结果会为 null。