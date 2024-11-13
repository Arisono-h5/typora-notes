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

Kotlin教程笔记(56) - 改良设计模式 - 装饰者模式



# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 改良设计模式 - 装饰者模式



## [#](https://fullstackaction.github.io/pages/41ce5a/#一、前言)一、前言

- 装饰者模式
  - 作用：在不必改变原类文件和使用继承的情况下，动态地扩展一个对象的功能。
  - 本质：该模式通过创建一个包装对象，来包裹真实的对象。
  - 核心操作：
    - 创建一个装饰类，包含一个被装饰类的实例
    - 装饰类重写所有被装饰类的方法
    - 在装饰类中对需要增强的功能进行扩展

## [#](https://fullstackaction.github.io/pages/41ce5a/#二、使用装饰者模式)二、使用装饰者模式

- 例子：枪支部件
- 重点：装饰器类设计（实现被装饰类相同的接口，构造器接收被装饰类的接口实例对象）

像绝地求生这种大型射击游戏，里面的枪支系统是很复杂的，有很多种枪，而且几乎每种枪上都可以装配各种各样的部件，比如消声器、八倍镜之类的，部件的作用各不相同，有的可以增加火力，有的可以提高精确度，等等，现在我们来简单设计一下这个枪支系统，枪有很多种，所以需要定义一个接口来描述枪都有哪些能力，供后续扩展各种新枪：

```kotlin
/**
 * 枪支接口
 *
 * @author GitLqr
 */
interface Gun {
    /**
     * 攻击力
     */
    fun attack(): Float

    /**
     * 噪音
     */
    fun noise(): Float

    /**
     * 生产日期
     */
    fun prodDate(): String
}

/**
 * Ump9
 *
 * @author GitLqr
 */
class Ump9Gun : Gun {
    override fun attack() = 100f

    override fun noise() = 20f

    override fun prodDate() = "2020-02-18"
}
```

这里只实现了 Ump9 这个型号的枪，后续还可以根据需要扩展，现在来想想枪支部件怎么设计？在 Java 中，给一个类扩展行为有两种选择：

- 设计一个继承它的子类
- 使用装饰者模式对该类进行装饰

那么枪支部件合适用继承方式来设计吗？显然不合适，因为一个部件可以装配在不只一种枪上，所以继承这种方式排除。另一种方式，使用装饰者模式有一个很大的优势，在于符合“组合优于继承”的设计原则，我们知道，部件可以和任意枪组合，显示，使用装饰者模式来设计枪支部件是一个不错的选择：

```kotlin
/**
 * 枪支部件
 *
 * @author GitLqr
 */
abstract class GunPart(protected val gun: Gun) : Gun

/**
 * 消声器
 *
 * @author GitLqr
 */
class Muffler(gun: Gun) : GunPart(gun) {
    override fun attack() = gun.attack() - 5

    override fun noise() = 0f

    override fun prodDate() = gun.prodDate()
}

/**
 * 燃烧子弹
 *
 * @author GitLqr
 */
class FireBullet(gun: Gun) : GunPart(gun) {
    override fun attack() = gun.attack() + 200

    override fun noise() = gun.noise()

    override fun prodDate() = gun.prodDate()
}
```

程序设计时，装饰器（部件）会引用被装饰实例（枪），并实现被装饰实例的所有接口，然后在需要增强的接口方法中加入增强逻辑。因为枪支部件 `GunPart` 接收 `Gun` 类型构造参数，而且本身也是 `Gun` 接口的实现类，所以，可以让多种枪支部件 `GunPart` 嵌套修饰枪实例：

```kotlin
// 使用
var ump9: Gun = Ump9Gun()
println("装配前：ump9 攻击力 ${ump9.attack()}，噪音 ${ump9.noise()}")
ump9 = Muffler(FireBullet(ump9)) // 装配了 燃烧子弹、消声器 的ump9
println("装配后：ump9 攻击力 ${ump9.attack()}，噪音 ${ump9.noise()}")

// 输出
装配前：ump9 攻击力 100.0，噪音 20.0
装配后：ump9 攻击力 295.0，噪音 0.0
```

## [#](https://fullstackaction.github.io/pages/41ce5a/#三、改良装饰者模式)三、改良装饰者模式

- 例子：枪支部件
- 重点：类委托（`by` 关键字）

在上面的例子中，装饰者模式可以很好的解决实例组合的情况，但是代码还是显得比较啰唆，因为需要重写所有的装饰对象方法，所以可能会存在大量样板代码。比如 `FireBullet` 只装饰增强 `attack()` 方法，而 `noise()`、`prodDate()` 均不做修改，但还要是把这两个方法重写一遍。Kotlin 中有类委托特性，利用 `by` 关键字，将装饰类的所有方法委托给一个被装饰的类对象，然后只需覆写装饰的方法即可：

```kotlin
/**
 * 枪支部件
 *
 * @author GitLqr
 */
abstract class GunPart(protected val gun: Gun) : Gun by gun

/**
 * 消声器
 *
 * @author GitLqr
 */
class Muffler(gun: Gun) : GunPart(gun) {
    override fun attack() = gun.attack() - 5
    override fun noise() = 0f
}

/**
 * 燃烧子弹
 *
 * @author GitLqr
 */
class FireBullet(gun: Gun) : GunPart(gun) {
    override fun attack() = gun.attack() + 200
}
```

可以看到，使用类委托之后，装饰类 `FireBullet` 中的样板代码不用重写了，从而减少了代码量。