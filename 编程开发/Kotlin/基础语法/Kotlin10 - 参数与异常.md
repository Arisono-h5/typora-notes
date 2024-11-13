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



  Kotlin教程笔记(10) - 参数与异常



# Kotlin - 参数与异常

<iframe id="aswift_2" name="aswift_2" browsingtopics="true" sandbox="allow-forms allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts allow-top-navigation-by-user-activation" width="860" height="0" frameborder="0" marginwidth="0" marginheight="0" vspace="0" hspace="0" allowtransparency="true" scrolling="no" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-7828333725993554&amp;output=html&amp;h=0&amp;slotname=6625304284&amp;adk=1995415467&amp;adf=2127742292&amp;pi=t.ma~as.6625304284&amp;w=860&amp;abgtt=1&amp;lmt=1726913804&amp;rafmt=12&amp;format=860x0&amp;url=https%3A%2F%2Ffullstackaction.github.io%2Fpages%2F7cd064%2F&amp;wgl=1&amp;uach=WyJXaW5kb3dzIiwiMTUuMC4wIiwieDg2IiwiIiwiMTI2LjAuNjQ3OC4xMjciLG51bGwsMCxudWxsLCI2NCIsW1siTm90L0EpQnJhbmQiLCI4LjAuMC4wIl0sWyJDaHJvbWl1bSIsIjEyNi4wLjY0NzguMTI3Il0sWyJHb29nbGUgQ2hyb21lIiwiMTI2LjAuNjQ3OC4xMjciXV0sMF0.&amp;dt=1729733098069&amp;bpp=2&amp;bdt=1545&amp;idt=973&amp;shv=r20241022&amp;mjsv=m202410170101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie_enabled=1&amp;eoidce=1&amp;prev_fmts=0x0%2C233x600%2C860x280%2C0x0&amp;nras=1&amp;correlator=2362232041459&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=35&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=24&amp;u_sd=1&amp;dmc=8&amp;adx=552&amp;ady=230&amp;biw=1914&amp;bih=911&amp;scr_x=0&amp;scr_y=0&amp;eid=44759875%2C44759926%2C31088190%2C31088194%2C31088260%2C42531706%2C95332928%2C95342015%2C95344190%2C95345270%2C95344979&amp;oid=2&amp;pvsid=1087269695505738&amp;tmod=1819756552&amp;uas=3&amp;nvt=2&amp;ref=https%3A%2F%2Fnav.vpssw.com%2F&amp;fc=1920&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1920%2C911&amp;vis=1&amp;rsz=%7C%7CeE%7C&amp;abl=CS&amp;fu=256&amp;bc=31&amp;bz=1&amp;td=1&amp;tdf=2&amp;psd=W251bGwsbnVsbCxudWxsLDNd&amp;nt=1&amp;ifi=3&amp;uci=a!3&amp;fsb=1&amp;dtd=6779" data-google-container-id="a!3" tabindex="0" title="Advertisement" aria-label="Advertisement" data-load-complete="true" style="left: 0px; top: 0px; border: 0px; width: 860px; height: 0px;"></iframe>



## [#](https://fullstackaction.github.io/pages/7cd064/#具名参数)具名参数

具名参数就是在调用函数时，给函数的实参附上形参：

```kotlin
fun sum(arg1: Int, arg2: Int) = arg1 + arg2

fun main(vararg args: String) {
    sum(arg1 = 2, arg2 = 3)
    sum(arg2 = 3, arg1 = 2)
}
```

使用具名参数可以把实参精确的传递给指定形参，因此具名参数可以不用按顺序传入。

## [#](https://fullstackaction.github.io/pages/7cd064/#变长参数)变长参数

`vararg` 可以让某个参数接收多个值，`vararg` 修饰的参数称为变长参数：

```kotlin
fun hello(vararg ints: Int, string: String) {
    ints.forEach(::println)
    println(string)
}

fun main(vararg args: String) {
    // hello(1, 2, 3, 4, 5, "hello") // IDE报错：Type mismatch. Required:Int Found:String
    hello(1, 2, 3, 4, 5, string = "hello")
}
```

- 变长参数可以不为最后一个参数
- 如果传参时有歧义，需要使用具名参数

### [#](https://fullstackaction.github.io/pages/7cd064/#展开操作符-spread-operator)展开操作符（Spread Operator）

当变长参数需要传入一个数组时，可以使用展开操作符 `*` ，`*` 会将数组展开后一一传入：

```kotlin
val array = intArrayOf(1, 2, 3, 4, 5)
hello(*array, string = "Hello") // vararg变长参数场景下，*号可以把Array数组展开，但不支持List
```

展开操作符 `*` 有以下几个特点：

- 只支持展开 Array
- 只用于变长参数列表的实参
- 不是一般意义上的操作符，不能重载

## [#](https://fullstackaction.github.io/pages/7cd064/#默认参数)默认参数

默认参数，即可以为函数任意位置的参数指定默认值：

```kotlin
fun say(age: Int = 20, name: String, height: Float) {
    ...
}

fun main(vararg args: String) {
    say(18, "lqr", 2.0f)
    say(name = "lqr", height = 2.0f)
}
```

如果默认参数导致传参出现歧义时，需要使用具名参数。换句话说，就是默认参数后面的参数需要使用具名参数传值。

## [#](https://fullstackaction.github.io/pages/7cd064/#多返回值)多返回值

借助 `Pair` 和 `Triple` 可以实现函数返回多值（注：伪多返回值），因为 `Pair` 和 `Triple` 支持 `解构` 语法：

```kotlin
fun main(vararg args: String) {
    val (myName, myAge) = multiReturnValues()
    println("myName is $myName, myAge is $myAge")

    val (name, age, height) = multiReturnValues(180.0)
    println("name is $name, age is $age, height is $height")
}

fun multiReturnValues(): Pair<String, Int> {
    // return Pair("lqr", 18)
    return "lqr" to 18
}

fun multiReturnValues(height: Double): Triple<String, Int, Double> {
    return Triple("lqr", 18, height)
}
```

> `to` 是中缀表达式，返回的就是 `Pair`，也就是 Map 里的键值对。

## [#](https://fullstackaction.github.io/pages/7cd064/#捕获异常)捕获异常

Kotlin 支持 `try...catch` 或 `try...catch...finally` 捕获异常，catch 分支匹配异常类型，finally 无论代码是否抛出异常都会执行：

```kotlin
try {
    val arg1 = args[0].toInt()
    val arg2 = args[1].toInt()
    println("$arg1 + $arg2 = ${sum(arg1, arg2)}")
} catch (e: NumberFormatException) {
    println("输入的数据不是数字")
} catch (e: ArrayIndexOutOfBoundsException) {
    println("需要输入2个数字")
} catch (e: Exception) {
    println("出现未知异常：${e.message}")
} finally {
    println("感谢使用")
}
```

跟 if、when 一样，`try...catch` 也可以是表达式，可以用来赋值：

```kotlin
val result = try {
    args[0].toInt() / args[1].toInt()
} catch (e: Exception) {
    0
}
```