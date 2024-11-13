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



  Kotlin教程笔记(12) - 面向对象之继承与实现

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 面向对象之继承与实现



继承是面向对象编程的三大特性之一，在开发过程中会经常使用，继承可以让子类拥有父类的功能，也可以对父类功能进行增强修改。

> 面向对象编程的三大特性：封装、继承、多态

## [#](https://fullstackaction.github.io/pages/feeb2d/#继承普通类)继承普通类

Kotlin 中默认 类、方法 都是 final 的，因此默认无法被子类继承或重写，但可通过 `open` 关键字来解除：

- 父类需要 open 才可以被继承
- 父类方法、属性需要 open 才可以被覆写
- 覆写父类成员需要 override 关键字

```kotlin
open class Person() {
    open fun walk() {
        println("慢慢走")
    }
}

class Doctor : Person() {
    override fun walk() {
        // super.walk()
        println("快走")
    }
}
```

子类重写父类方法时，会使用到 `override` 关键字，另外，重写的方法体中可以使用 `super.xxx()` 来调用父类方法中原有的逻辑，当然你也可以选择完全重写(方法体中不使用 `super.xxx()` 即可)。Kotlin 中父类的属性与方法一样，子类要重写的话，需要使用 `open` 关键字修饰父类属性，解除 final：

```kotlin
// 重写父类属性
open class Person(open val name: String) {
    ...
}
class Doctor(override val name: String) : Person(name) {
    ...
}
```

当然啦，也不是所有子类都需要重写父类成员属性的，因为子类可通过 `getter/setter` 对父类的成员属性进行访问。这时子类仅需要将临时变量（即不使用 val 或 var 修饰的构造器参数变量）传递到父类构造器中就好了：

- 继承类时实际上是调用了父类构造方法

```kotlin
// 传递构造参数
open class Person(val name: String) {　// 使用了val，所以name是父类Person的成员属性。
    ...
}
class Doctor(name: String) : Person(name) {　// 没有val，所以name仅仅只是一个临时变量。
    ...
}

// 不想重写父亲属性就不要使用val或var修改，因为这相当于在子类中定义了一个与父类成员属性同名的属性。
// class Doctor(val name: String) : Person(name) // IDE报错：'name' hides memeber of supertype 'Person' and needs 'override' modifier
```

## [#](https://fullstackaction.github.io/pages/feeb2d/#继承-实现-抽象类-接口)继承(实现)抽象类(接口)

相比于普通类，抽象类与接口就比较"开放"了，因为它们本身设计出来就是为了让子类(实现类)去继承(实现)的：

- 接口、接口方法、抽象类默认为 open

```kotlin
abstract class Person() {
    open fun walk() {　// 成员方法，想被子类重写需要使用open关键字
        println("慢慢走")
    }

    abstract fun work() // 抽象方法，默认就是open的
}

class Doctor : Person() {
    override fun walk() {
        println("快走")
    }

    override fun work() {　// 子类实现父类抽象方法，还是需要使用override关键字
    }
}
```

### [#](https://fullstackaction.github.io/pages/feeb2d/#接口代理)接口代理

Kotlin 不支持多继承，只能使用接口来实现多个功能，但我们又不想在类中将接口方法的实现写死，这样代码就不够灵活，因此，往往会在类的构造器参数中，将接口的实现类传进来，而在我们的类中，只需要在实现了接口方法的方法体中调用实现类的对应方法：

```kotlin
interface Driver {
    fun dirve()
}

class Manager(val driver: Driver) : Driver {
    override fun dirve() {
        driver.dirve()
    }
}
```

但这种写法会显得比较罗嗦，Kotlin 提供了 `接口代理` 将接口方法实现直接交给代理类实现：

- 格式: class XXX(接口实现类) : 接口 by 接口实现类

```kotlin
class Manager(driver: Driver): Driver by driver
```

> 这算不算是对 Kotlin 不支持多继承的 "曲线救国" 呢？其实 Java 也一样不支持多继承，通常会使用组合的方式来处理。

### [#](https://fullstackaction.github.io/pages/feeb2d/#接口方法冲突)接口方法冲突

前面我们已经知道了接口方法是可以有默认实现的，Kotlin 可以实现多个接口，而这些接口可能拥有相同的接口方法，就比如这样：

```kotlin
interface Radio {
    fun display(): String {
        return "107.1"
    }
    ...
}

interface Compass {
    fun display(): String {
        return "东方"
    }
    ...
}
```

这时有一个实现类，同时实现了上述两个接口，就会出现接口方法冲突问题：

```kotlin
class Phone(val type: Int) : Radio, Compass {
    override fun display(): String {
        return super.display() // IDE报错：Many supertypes available, please specify the one you mean in angle brackets, e.g. 'super<Foo>'
    }
    ...
}
```

根据提示，这个接口方法冲突问题其实也挺好解决的，只需要在 `super` 后使用泛型指定父类(接口)名即可：

```kotlin
class Phone(val type: Int) : Radio, Compass {
    override fun display(): String {
        when (type) {
            0 -> return super<Radio>.display()
            1 -> return super<Compass>.display()
            else -> return "不支持"
        }
    }
}
```

要注意，这里的接口方法冲突，指的是 `签名一致且返回值相同的冲突` ，如果签名一致但返回值类型不同，那这个问题将无解：

> 方法签名一致指的是`方法名、参数列表`相同。

```kotlin
interface Radio {
    fun display(): String {
        return "107.1"
    }
}

interface Compass {
    fun display(): Int {
        return 180
    }
}

// IDE报错：
// Platform declaration clash: The following declarations have the same JVM signature (display()Ljava/lang/String;)
// Platform declaration clash: The following declarations have the same JVM signature (display()I;)
class Phone(val type: Int) : Radio, Compass {
    override fun display(): String { // IDE报错
    }

    override fun display(): Int { // IDE报错
    }
}
```

但反过来，如果方法返回值相同但签名不一致，那这情况就不一样了，就相当于 2 个不一样的方法，需要分开重写，只是在使用 `super.xxx()` 调用接口方法时同样还是需要使用泛型来指明父接口，避免发生歧义：

```kotlin
interface Radio {
    fun display(): String {
        return "107.1"
    }
}

interface Compass {
    fun display(i: Int): Int {
        return i
    }
}

class Phone(val type: Int) : Radio, Compass {
    override fun display(): String {
        return super <Radio>.display()
    }

    override fun display(i: Int): Int {
        return super<Compass>.display(i)
    }
}
```