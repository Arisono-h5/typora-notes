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



​     Kotlin教程笔记(16) - 扩展成员

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 扩展成员



## [#](https://fullstackaction.github.io/pages/e18f51/#扩展方法)扩展方法

Kotlin 中支持在不修改类原本结构的前提下，对类功能进行扩展，比如对 String 类新增一个 multiply()方法，可返回重复 n 次的字符串：

```kotlin
fun String.multiply(time: Int): String {
    val stringBuilder = StringBuilder()
    for (i in 0 until time) stringBuilder.append(this)
    return stringBuilder.toString()
}

fun main() {
    println("hehe".multiply(3)) // hehehehehehe
}
```

可以看到扩展方法的格式其实很简单，跟普通的函数差不多，只不过在函数名前面多了 `要扩展的类名` 和一个 `.` 而已，扩展方法的方法体中，可以使用 `this` 得到原本的对象。

> 扩展成员的相关代码外层不需要包裹诸如 class 的代码块，可直接存放在任意 kt 文件中，且在其它 kt 文件中可以直接调用。

## [#](https://fullstackaction.github.io/pages/e18f51/#扩展运算符函数)扩展运算符函数

在 Python 中，字符串若是乘上整数 n，将返回由 n 个此字符串拼接起来的新字符串。这个语法特性我是挺喜欢的，那么 Kotlin 中是否也可以做到像 Python 那样呢？答案是可以的，类似 `"hehe" * 3` 这种写法，结合之前所学的运算符重载知识，这个问题其实本质上就是对 String 类中的 `*`运行符函数 `times()` 进行重载即可，但 String 类我们无法直接修改其源码，同时由于 Kotlin 支持扩展类成员的特性，因此我们可以对运算符函数进行如下扩展：

> 了解更多操作符对应的具名函数，请点击：[https://www.kotlincn.net/docs/reference/operator-overloading.html(opens new window)](https://www.kotlincn.net/docs/reference/operator-overloading.html)

```kotlin
operator fun String.times(time: Int): String {
    val stringBuilder = StringBuilder()
    for (i in 0 until time) stringBuilder.append(this)
    return stringBuilder.toString()
}

fun main() {
    println("hehe" * 3) // hehehehehehe
}
```

扩展运算符函数 跟扩展方法的格式是一样的，先书写要重载的运算符函数，然后在函数名前面增加 `类名` 和 `.` 即可。

## [#](https://fullstackaction.github.io/pages/e18f51/#扩展属性)扩展属性

Kotlin 不仅支持扩展类方法，也支持扩展类属性，例如 String 原本只有 length 属性，我们可以扩展一个 size 属性，功能与 length 属性一样：

```kotlin
val String.size: Int
    get() {
        return this.length
    }

fun main() {
    println("hehe".size) // 4
}
```

注意，扩展属性如果使用 val 修饰，则只有 `get()` 方法，如果使用 var 修饰，则可以有 `set()` 方法，但因为扩展属性没有 `backing field`，即无法使用 `field = value` 这类代码，因此，这个 `set()` 方法其实形同虚设。

```kotlin
var String.size: Int
    get() {
        return this.length
    }
    set(value) {
        // field = value // IDE报错：Unresolved reference: field
    }
```

> 扩展属性不能初始化，类似接口属性

## [#](https://fullstackaction.github.io/pages/e18f51/#java-调用-kotlin-扩展成员)Java 调用 Kotlin 扩展成员

Java 不认识 Kotlin 的语法糖，所以没办法像 Kotlin 代码那样使用原对象直接调用扩展成员，而是类似调用静态方法的方式：

```java
String str = "hehe";
System.out.println(ExtendExampleKt.multiply(str, 4)); // hehehehehehehehe
System.out.println(ExtendExampleKt.times(str, 5)); // hehehehehehehehehehe
System.out.println(ExtendExampleKt.getSize(str)); // 4
```

Kotlin 的扩展成员在 Java 中会被识别成 类名为 `kt文件名＋Kt` 组成的类静态方法，附上下图方便理解：

![image-20241014190547875](https://s2.loli.net/2024/10/14/UmQZ6t4GDR3ELJk.png)