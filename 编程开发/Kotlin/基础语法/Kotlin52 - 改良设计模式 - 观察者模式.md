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

Kotlin教程笔记(52) - 改良设计模式 - 观察者模式

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 改良设计模式 - 观察者模式



## [#](https://fullstackaction.github.io/pages/fcfa28/#一、前言)一、前言

- 观察者模式
  - 作用：定义了一个一对多的依赖关系，让一个或多个观察者对象监听一个主题对象。这样一来，当被观察者状态发生改变时，需要通知相应的观察者，使这些观察者对象能够自动更新。
  - 核心操作：
    - 观察者（订阅者）添加或删除对 被观察者（主题）的状态监听
    - 被观察者（主题）状态改变时，将事件通知给所有观察者，观察者执行响应逻辑

## [#](https://fullstackaction.github.io/pages/fcfa28/#二、使用观察者模式)二、使用观察者模式

- 例子：监听股票价格变动
- 重点：使用 Java API 或 自定义实现 观察者模式

### [#](https://fullstackaction.github.io/pages/fcfa28/#_1、使用-java-api-实现观察者模式)1、使用 Java API 实现观察者模式

Java 标准库中提供了通用观察者模式的 API，分别是：

- ```
  java.util.Observable
  ```

  ：被观察者（主题）

  - `setChanged()`：标记状态更新
  - `addObserver()`：添加观察者
  - `deleteObserver()`：删除观察者
  - `countObservers()`：获取观察者数量
  - `notifyObservers()`：通知所有观察者
  - `notifyObservers(Object arg)`：通知所有观察者（携带参数 arg）

- `java.util.Observer`：观察者（订阅者）

利用 Java API，可以实现监听股票价格变动这个功能：

```kotlin
import java.util.Observable
import java.util.Observer

/**
 * 被观察者（主题）
 *
 * @author GitLqr
 */
class StockSubject : Observable() {
    fun changeStockPrice(price: Int) {
        this.setChanged() // 标识状态更新
        this.notifyObservers(price) // 通知所有观察者当前股票价格
    }
}

/**
 * 观察者（订阅者）
 *
 * @author GitLqr
 */
class StockDisplay(val name: String) : Observer {
    override fun update(o: Observable?, price: Any?) {
        println("$name receive stock price : $price") // 注意 price 的类型是 Any?
    }
}

// 使用
val subject = StockSubject()
subject.addObserver(StockDisplay("observer 1"))
subject.addObserver(StockDisplay("observer 2"))
subject.changeStockPrice(200)

// 输出
// observer 2 receive stock price : 200
// observer 1 receive stock price : 200
```

> 注意：在主题中通过 `notifyObservers()` 方法通知订阅者之前，需要先调用 `setChanged()` 标识状态更新，才能正常通知给订阅者，这是使用 Java API 实现观察者模式时需要注意的一点。

Java 提供的 API 已经涵盖了观察者模式的完整实现，所以我们在使用的时候，只需要关注业务本身，而不用自己去做模式的具体实现，但是呢，Java 提供的 API 是一种通用实现，从上面的例子中可以注意到，`StockDisplay.update(o: Observable?, price: Any?)` 中的 `price` 参数类型是 `Any?` ，这就会有以下几个问题：

- 参数判断：因为参数类型是 `Any?`，所以开发中不得不对 参数是否为空 以及 参数的实际类型 做判断。
- 通知入口单一：实际业务需求会更加复杂，而 `java.util.Observer` 只有唯一一个通知入口 `update(o: Observable?, arg: Any?)`，所以我们不得不在该方法中分离响应逻辑，比如股票价格升降，这会让代码显得臃肿。

### [#](https://fullstackaction.github.io/pages/fcfa28/#_2、自定义实现观察者模式)2、自定义实现观察者模式

虽然 Java 提供了现成的观察者模式 API，但是实际开发中，我们通常还是会自定义实现观察者模式，以便更好的控制代码结构：

```kotlin
/**
 * 回调接口（解耦业务通知入口）
 *
 * @author GitLqr
 */
interface StockUpdateListener {
    fun onRise(price: Int)
    fun onFall(price: Int)
}

/**
 * 被观察者（主题）
 *
 * @author GitLqr
 */
class StockSubject {
    val listeners = mutableSetOf<StockUpdateListener>()
    var price: Int = 0

    fun subscribe(observer: StockUpdateListener) {
        listeners.add(observer)
    }

    fun unsubscribe(observer: StockUpdateListener) {
        listeners.remove(observer)
    }

    fun changeStockPrice(price: Int) {
        val isRise = price > this.price
        listeners.forEach { if (isRise) it.onRise(price) else it.onFall(price) }
        this.price = price
    }
}

/**
 * 观察者（订阅者）
 *
 * @author GitLqr
 */
class StockDisplay : StockUpdateListener {
    override fun onRise(price: Int) {
        println("The latest stock price has rise to $price")
    }

    override fun onFall(price: Int) {
        println("The latest stock price has fell to $price")
    }
}

// 使用
val subject = StockSubject()
subject.subscribe(StockDisplay())
subject.changeStockPrice(200) // The latest stock price has rise to 200
```

可见，自定义实现观察者模式，可以让代码结构变得更加简单直观。

## [#](https://fullstackaction.github.io/pages/fcfa28/#三、改良观察者模式)三、改良观察者模式

- 例子：监听股票价格变动
- 重点：委托属性 `Delegates.observable()`

Kotlin 标准库引入了可被观察的委托属性，可通过 `xxx by Delegates.observable()` 的方式，用来监听 `xxx` 属性的改变，于是可以用来改良上面的自定义观察者模式：

```kotlin
import kotlin.properties.Delegates

/**
 * 观察者模式改良：使用委托属性监听值变化后通知
 *
 * @author GitLqr
 */
class StockSubject {
    val listeners = mutableSetOf<StockUpdateListener>()

    var price: Int by Delegates.observable(0) { prop, old, new ->
        val isRise = new > old
        listeners.forEach { if (isRise) it.onRise(price) else it.onFall(price) }
    }

    fun subscribe(observer: StockUpdateListener) {
        listeners.add(observer)
    }

    fun unsubscribe(observer: StockUpdateListener) {
        listeners.remove(observer)
    }

    // fun changeStockPrice(price: Int) { ... }
}

// 使用
val subject = StockSubject()
subject.subscribe(StockDisplay())
subject.price = 250 // The latest stock price has rise to 200
```

使用 `Delegates.observable()` 之后，`StockSubject` 相比之前减少了一个 `changeStockPrice()` 方法。使用上，一旦对 `price` 属性赋值，就可以触发通知，显然，这对使用者更加友好了（直观，少记一个方法）。

## [#](https://fullstackaction.github.io/pages/fcfa28/#四、补充)四、补充

前面说到，Kotlin 标准库引入可被观察的委托属性，除了 `Delegates.observable()` 之外，还有 `Delegates.vetoable()` 也很实用，当我们不希望被监控的属性被随意修改时，就可以用它来否决属性赋值：

```kotlin
import kotlin.properties.Delegates

var value: Int by Delegates.vetoable(0) { prop, old, new ->
    // 新值大于0时，才给属性赋值
    new > 0
}

// 使用
value = 1
println(value) // 1
value = -1
println(value) // 1（没能赋值成功）
```