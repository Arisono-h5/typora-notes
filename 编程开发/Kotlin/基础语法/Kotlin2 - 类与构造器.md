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

  Kotlin教程笔记(2) - 类与构造器

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 类与构造器



## [#](https://fullstackaction.github.io/pages/901745/#类是什么)类是什么？

类是一个抽象的概念，是具有某些特征的事物的概括，不特定指代任何一个具体的事物。写法：

```kotlin
class <类名> {
    <成员>
}
```

> Number(Int、Float、Byte)、字符串(String)也是类

```kotlin
class Girl constructor(var nature: String,var appearance: String,var sound: String){
    // 构造方法的方法体
    init {
        println("女孩的性格：$nature，长相：$appearance，声音：$sound")
    }
}
```

- `constructor` 是构造器关键字，如果只有一个构造器，则该关键字可以省略。
- `init` 是构造方法的方法体，当用该类创建出一个对象时就会执行。

```kotlin
fun main(args: Array<String>) {
    val girl: Girl = Girl("温柔", "甜美", "动人") // 女孩的性格：温柔，长相：甜美，声音：动人
}
```

## [#](https://fullstackaction.github.io/pages/901745/#类构造器)类构造器

构造器分为两种，分别是：

- 主构造器：紧接在类名后面的构造器，参数可以使用 `var` 声明，`init` 是主构造器的方法体。
- 次构造器：在类代码块中声明的构造器，参数不可以使用 `var` 声明，与 `init` 无直接关系。

```kotlin
class Girl constructor(var nature: String, var appearance: String, var sound: String) {

    // 主构造器的方法体
    init {
        println("女孩的性格：$nature，长相：$appearance，声音：$sound")
    }

    // 次级构造器，无法使用 var 声明变量
    constructor(nature: String, appearance: String) : this(nature, appearance, sound = "未知") {
        println("次级构造器")
    }
}

fun main(args: Array<String>) {
    val girl: Girl = Girl("温柔", "甜美")
    // 输出2句：
    // 女孩的性格：温柔，长相：甜美，声音：未知
    // 次级构造器被调用
}
```

上面说到，次级构造器与 `init` 无直接关系，但次级构造器会通过 `:this(...)` 调用主构造器，从而触发 `init` 方法体执行。另外，通过输出结果，可以确定 次级构造器方法体 会比 `init` 方法体晚执行。

> 个人建议：先写 `init`，再写次级构造器，看起来会比较舒服。

### [#](https://fullstackaction.github.io/pages/901745/#构造器省略-constructor-关键字)构造器省略 `constructor` 关键字

当没有次级构造器，只有一个主构造器时，可以省略 `constructor` 关键字：

```kotlin
class Girl(var nature: String, var appearance: String, var sound: String) {
    ...
}
```

### [#](https://fullstackaction.github.io/pages/901745/#主构造器中的-var-参数)主构造器中的 `var` 参数

上面说到，主构造器的参数才能使用 `var` 声明，而次构造器则不行，那么主构造器中有无使用 `var` 声明的参数，会有何不同？

```kotlin
// 注意：只有nature使用了var声明
class Girl constructor(var nature: String, appearance: String, sound: String) {

    init {
        println("女孩的性格：$nature，长相：$appearance，声音：$sound")
    }

    fun test() {
        println(nature) // 编译OK
        println(appearance)　// 编译不通过
        println(sound)　// 编译不通过
    }
}
```

`init` 方法体中可以访问主构造器的所有参数，而方法 `test()` 却只能访问 `var` 声明的构造器参数。

- 主构造器中，使用 `var` 声明的参数，将成为成员变量，可以在类的各个方法中调用。
- 而不使用 `var` 声明参数，只是临时变量，只能在 `init` 方法体中使用。

## [#](https://fullstackaction.github.io/pages/901745/#类的继承)类的继承

子类继承父类，可以获得父类的能力，Kotlin 中使用 `:` 连接子父类，形成继承关系，同时，父类需要使用 `open` 关键字修饰：

```kotlin
open class Human(nature: String, appearance: String, sound: String) {
    init {
        println("${this.javaClass.simpleName} 的性格：$nature，长相：$appearance，声音：$sound")
    }
}

class Girl(nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
class Boy(nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
```

> 从 Java 开发者的角度来讲，Kotlin 中的类默认是 `final` 类，而使用 `open` 修饰过的类，会去除 `final` 关键字。

### [#](https://fullstackaction.github.io/pages/901745/#子类构造器)子类构造器

上述例子中，无论是 Girl 或是 Boy，它们的主构造器参数都没有使用 `var` 声明，实事上也不能使用 `var` 声明，我们可以做个实验：

```kotlin
// 报错：'nature' hides member of supertype 'Human' and needs 'override' modifier
class Boy(var nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
```

Boy 主构造器中使用 `var` 声明 nature，会报错提示 nature 在父类 Human 中是隐藏成员，你需要使用 `override` 对其修改，那就按提示把 `override` 关键字加上，但还会报另一个错：

```kotlin
// 报错：'nature' in 'Human' is final and cannot be overridden
class Boy(override var nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
```

如果单单对 nature 追加 `override` 关键字是不够的，因为构造器中的参数默认是 `final` 修饰过的不可修改变量，需要对父类 Human 主构造器中的 nature 参数再追加 `open` 关键字来去除这个限制。

```kotlin
open class Human(open var nature: String, var appearance: String, var sound: String) {
    ...
}
class Boy(override var nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
```

好了，终于把子类 Boy 的主构造器参数 nature 加上了 `var` 声明，那这有什么呢？答案是似乎没啥用。

![img](https://cdn.jsdelivr.net/gh/FullStackAction/PicBed@resource/image/20210116122644.jpg)

因为就算子类 Boy 主构造器参数 nature 不用 `var` 声明，也一样可以在子类 Boy 的成员方法中使用这个 nature 变量，原因是 nature 早已在父类 Human 的主构造器中使用了 `var` 声明，它是父类 Human 的成员变量（类似 Java 中的 `protected final String nature` ），可以被子类 Boy 识别和调用。所以，话说回来，我们什么时候会需要使用 `var` 来声明与父类构造器参数同名的子类主构造器参数呢？

```kotlin
open class Human(nature: String, var appearance: String, var sound: String) {
    ...
}

class Boy(var nature: String, appearance: String, sound: String) : Human(nature, appearance, sound)
```

当父类主构造器参数没有使用 `var` 声明，而子类又需要在成员方法中使用该参数时，可以在子类的构造器中，为该参数使用 `var` 追加声明，让其成为子类的成员变量。除此之外，子类主构造器参数的使用与普通的主构造器参数没什么区别。

### [#](https://fullstackaction.github.io/pages/901745/#any-类)Any 类

在 Kotlin 中，Any 是所有类的始祖，相当于 Java 中的 Object。

```kotlin
/**
 * The root of the Kotlin class hierarchy. Every Kotlin class has [Any] as a superclass.
 */
public open class Any {
    ...
}
```

## [#](https://fullstackaction.github.io/pages/901745/#包-package)包（Package）

- 包就是命名空间
- 包的声明必须在非注释代码的第一行
- 类的全名是 `包名＋类名` ，如：com.area.guangzhou.Human

举个例子，在 com.area.guangzhou 包下声明一个 Human 类：

```kotlin
package com.area.guangzhou　// 第一行代码：包声明
/**
 * 广州人
 */
class Human {
}
```

由于包的存在，因此工程中可以在不同的目录下，声明多个类名相同的类，比如在 com.area.shantou 再声明一个 Human 类：

```kotlin
package com.area.shantou
/**
 * 汕头人
 */
class Human {
}
```

因为类名相同，所以在同个文件中使用时，为了区分 2 个 Human，需要使用类的全名：

```kotlin
fun main(args: Array<String>) {
    val gzHuman = com.area.guangzhou.Human()
    val stHuman = com.area.shantou.Human()
}
```

这样写出来的代码，看起来很不雅观，这时我们可以使用 `as` 关键字对导包设置别名：

```kotlin
import com.area.guangzhou.Human as 自给人
import com.area.shantou.Human as 胶己人

fun main(args: Array<String>) {
    val gzHuman = 自给人()
    val stHuman = 胶己人()
}
```

> 注意：这里的代码仅为演示说明，实际开发中，为了避免不必要的麻烦，最好不要使用中文进行 coding。