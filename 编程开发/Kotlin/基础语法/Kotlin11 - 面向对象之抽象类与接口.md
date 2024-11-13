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



  Kotlin教程笔记(11) - 面向对象之抽象类与接口



# Kotlin - 面向对象之抽象类与接口

<iframe id="aswift_2" name="aswift_2" browsingtopics="true" sandbox="allow-forms allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts allow-top-navigation-by-user-activation" width="860" height="0" frameborder="0" marginwidth="0" marginheight="0" vspace="0" hspace="0" allowtransparency="true" scrolling="no" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-7828333725993554&amp;output=html&amp;h=0&amp;slotname=6625304284&amp;adk=1995415467&amp;adf=2127742292&amp;pi=t.ma~as.6625304284&amp;w=860&amp;abgtt=1&amp;lmt=1726913804&amp;rafmt=12&amp;format=860x0&amp;url=https%3A%2F%2Ffullstackaction.github.io%2Fpages%2F7cd064%2F&amp;wgl=1&amp;uach=WyJXaW5kb3dzIiwiMTUuMC4wIiwieDg2IiwiIiwiMTI2LjAuNjQ3OC4xMjciLG51bGwsMCxudWxsLCI2NCIsW1siTm90L0EpQnJhbmQiLCI4LjAuMC4wIl0sWyJDaHJvbWl1bSIsIjEyNi4wLjY0NzguMTI3Il0sWyJHb29nbGUgQ2hyb21lIiwiMTI2LjAuNjQ3OC4xMjciXV0sMF0.&amp;dt=1729733098069&amp;bpp=2&amp;bdt=1545&amp;idt=973&amp;shv=r20241022&amp;mjsv=m202410170101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie_enabled=1&amp;eoidce=1&amp;prev_fmts=0x0%2C233x600%2C860x280%2C0x0&amp;nras=1&amp;correlator=2362232041459&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=35&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=24&amp;u_sd=1&amp;dmc=8&amp;adx=552&amp;ady=230&amp;biw=1914&amp;bih=911&amp;scr_x=0&amp;scr_y=0&amp;eid=44759875%2C44759926%2C31088190%2C31088194%2C31088260%2C42531706%2C95332928%2C95342015%2C95344190%2C95345270%2C95344979&amp;oid=2&amp;pvsid=1087269695505738&amp;tmod=1819756552&amp;uas=3&amp;nvt=2&amp;ref=https%3A%2F%2Fnav.vpssw.com%2F&amp;fc=1920&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1920%2C911&amp;vis=1&amp;rsz=%7C%7CeE%7C&amp;abl=CS&amp;fu=256&amp;bc=31&amp;bz=1&amp;td=1&amp;tdf=2&amp;psd=W251bGwsbnVsbCxudWxsLDNd&amp;nt=1&amp;ifi=3&amp;uci=a!3&amp;fsb=1&amp;dtd=6779" data-google-container-id="a!3" tabindex="0" title="Advertisement" aria-label="Advertisement" data-load-complete="true" style="left: 0px; top: 0px; border: 0px; width: 860px; height: 0px;"></iframe>



## [#](https://fullstackaction.github.io/pages/1d7592/#接口)接口

接口是一种约定或协议，需要使用 `interface` 定义：

```kotlin
interface InputDevice {
    fun input(event: Any)
}
```

接口不能有状态，我们可以在接口中声明一个类似"属性"的变量 x，但它并不是一个属性，相当于只是声明 `getX/setX` 方法：

```kotlin
interface InputDevice {
    //val version: String = "default" // IDE报错：Property initializers are not allowed in interfaces
    val version: String // 相当于定义getVersion()和setVersion()方法，但它不是属性，因为接口没有状态
    ...
}
```

接口没有构造器，因此无法像类那样实例化，必须由类对其进行实现后使用：

```kotlin
fun main() {
    // val inputDevice = InputDevice() // IDE报错：Interface InputDevice does not have constructors

    val myInputDevice = MyInputDevice("1.0")
    myInputDevice.input("")
}

class MyInputDevice(override val version: String) : InputDevice {
    override fun input(event: Any) {
        println("010101010101010101001010101010....")
    }
}
```

> 实现接口需要使用 `:` 来连接，注意，因为接口没有构造器，所以实现接口时不需要带 `()`。

接口之间是可以继承的，子接口将拥有父接口的所有方法：

```kotlin
// USB输入设备
interface USBInputDevice : InputDevice
// 蓝牙输入设备
interface BLEInputDevice : InputDevice
```

另外，在 Kotlin 中接口方法可以默认实现：

```kotlin
interface InputDevice {
    ...
    fun onLowPower() {
        println("注意：当前电量低")
    }
}
```

> 与 Kotlin 不同，Java 中的接口不支持默认实现。

## [#](https://fullstackaction.github.io/pages/1d7592/#抽象类)抽象类

抽象类可以理解为是实现了一部分协议的半成品，需要使用 `abstract class` 定义：

```kotlin
abstract class USBMouse(val name: String, override val version: String = "1.0") : USBInputDevice {

    override fun input(event: Any) {
        println("x , y ... ")
    }

    fun click(key: String) {
        println("点击了 $key 键")
    }

    abstract fun isSupport(os: String): Boolean
}
```

可以看到，抽象类是有构造器的，构造器中的 val 或 var 参数会变成成员属性，也就是说抽象类可以有状态。抽象类 USBMouse 实现了 USBInputDevice 接口，并实现了 input()方法，说明抽象类可以有方法实现。当然了，抽象类中方法实现不依赖于接口，它本身就可以像类那样定义自己的方法，如 click()。甚至它也可以像接口那样定义没有方法体的抽象方法 isSupport()，由具体子类去实现：

```kotlin
class LogitechMouse : USBMouse("罗技鼠标") {
    override fun isSupport(os: String): Boolean {
        return when (os) {
            "windows" -> true
            "MacOS" -> true
            "iOS" -> false
            else -> false
        }
    }
}
```

> 类继承需要使用 `:` 来连接，注意，因为抽象类同普通类一样拥有构造器（不管有无构造参数），所以实现抽象类时需要带 `()`。

抽象类无法直接实例化，必须要子类继承后使用：

```kotlin
fun main() {
    // val mouse = USBMouse() // IDE报错：Cannot create an instance of an abstract class
    val mouse = LogitechMouse()
    if (mouse.isSupport("windows")) {
        mouse.click("left")
    }
}
```

## [#](https://fullstackaction.github.io/pages/1d7592/#单继承多实现)单继承多实现

Kotlin 不支持多继承！但支持多实现！比如，罗技 M720 鼠标本质是罗技鼠标，拥有 USB 和 BLE 两种连接功能：

```kotlin
class LogitechM720 : LogitechMouse(), USBInputDevice, BLEInputDevice {}

fun main() {
    val usbInputDevice: USBInputDevice = LogitechM720()
    val bleInputDevice: BLEInputDevice = LogitechM720()
    val usbMouse: USBMouse = LogitechM720()
    val logitechMouse: LogitechMouse = LogitechM720()
}
```

> 可以使用 接口或抽象类变量 接收 实现类实例。

## [#](https://fullstackaction.github.io/pages/1d7592/#抽象类和接口的共性与区别)抽象类和接口的共性与区别

| 共性                                             | 比较抽象，不能直接实例化   |
| ------------------------------------------------ | -------------------------- |
| 有需要子类（实现类）实现的方法                   |                            |
| 父类（接口）变量可以接收子类（实现类）的实例赋值 |                            |
| 区别                                             | 抽象类有状态，接口没有状态 |
| 抽象类有方法实现，接口只能有无状态的默认实现     |                            |
| 抽象类只能单继承，接口可以多实现                 |                            |
| 抽象类反映本质，接口体现能力                     |                            |