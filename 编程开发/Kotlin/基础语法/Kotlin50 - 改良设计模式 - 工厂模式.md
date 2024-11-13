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

Kotlin教程笔记(50) - 改良设计模式 - 工厂模式

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 改良设计模式 - 工厂模式



## [#](https://fullstackaction.github.io/pages/d45f5d/#一、前言)一、前言

设计模式是软件工程中解决特定问题的一种指南，我们常说 Java 有 23 种设计模式，而多范式的 Kotlin 作为更好的 Java，拥有很多新的语言特性，在使用原本 Java 中常用的设计模式时，可以有哪些方面的改良呢？

> 说明：本系列是本人对《Kotlin 核心编程》第 9 章 设计模式 的理解总结，所以总结内容上会有些改动，另外，部分篇章个人觉得意义不大，所以没有在本系列中进行概括，有兴趣可自行查阅原书籍。

- 工厂模式
  - 作用：隐藏对象实例的创建逻辑，而不需要暴露给客户端。
  - 细分：简单工厂、工厂方法、抽象工厂。

## [#](https://fullstackaction.github.io/pages/d45f5d/#二、改良简单工厂)二、改良简单工厂

- 例子：电脑厂商生产电脑（服务器、家用 PC）
- 重点：伴生对象、运算符重载(`invoke`)

```kotlin
/**
 * 电脑接口
 *
 * @author GitLqr
 */
interface Computer {
    val cpu: String
}

/**
 * 电脑类
 *
 * @author GitLqr
 */
class PC(override val cpu: String = "Core") : Computer
class Server(override val cpu: String = "Xeon") : Computer

/**
 * 电脑类型枚举
 *
 * @author GitLqr
 */
enum class ComputerType {
    PC, SERVER
}
```

简单工厂，一般会使用单例模式（私有化构造器，强制通过类方法来使用），先来看 Java 版本：

```java
/**
 * 简单电脑工厂（Java版）
 *
 * @author GitLqr
 */
public static class ComputerFactory {
    private ComputerFactory() {
    }

    public static Computer produce(ComputerType type) {
        if (type == ComputerType.PC) {
            return new PC();
        } else if (type == ComputerType.SERVER) {
            return new Server();
        } else {
            throw new IllegalArgumentException("没有其他类型的电脑了");
        }
    }
}

// 使用
Computer pc = ComputerFactory.produce(ComputerType.PC);
Computer server = ComputerFactory.produce(ComputerType.SERVER);
```

Kotlin 在语言层面就已经实现了单例（使用 `object` 关键字替代 `class`），所以将上述代码改造成 Kotlin 版本：

```kotlin
/**
 * 简单电脑工厂（Kotlin版）
 *
 * @author GitLqr
 */
object ComputerFactory {
    fun produce(type: ComputerType): Computer {
        return when (type) {
            ComputerType.PC -> PC()
            ComputerType.SERVER -> Server()
        }
    }
}

// 使用
val pc = ComputerFactory.produce(ComputerType.PC)
val server = ComputerFactory.produce(ComputerType.SERVER)
```

以上只不过是用 Kotlin 翻译了一遍 Java 代码，下面进入正题，从这个简单工厂的使用上，我们知道核心是让 `ComputerFactory` 根据不同的 `ComputerType` 参数来创建电脑实例，而这个 `produce` 方法名并不重要，结合 Kotlin 的运算符重载，可以进一步简化代码：

```kotlin
/**
 * 简单工厂改良：重载 invoke 运算符
 *
 * @author GitLqr
 */
object ComputerFactory {
    operator fun invoke(type: ComputerType): Computer {
        return when (type) {
            ComputerType.PC -> PC()
            ComputerType.SERVER -> Server()
        }
    }
}

// 使用
val pc = ComputerFactory(ComputerType.PC)
val server = ComputerFactory(ComputerType.SERVER)
```

你可能会觉得 `ComputerFactory(ComputerType.PC)` 这样的代码也太奇怪了，更像是在创建一个工厂实例，如果能改成 `Computer(ComputerType.PC)` 这样的代码的话，才比较符合正常逻辑吧，没问题，只需要在 `Computer` 接口中搞一个静态工厂方法代替构造器就好了，先来看下 Java 版本：

```java
/**
 * 静态工厂方法（Java版）
 *
 * @author GitLqr
 */
interface Computer {
    class Factory{ // 等同于 public static class Factory
        public static Computer produce(ComputerType type){
            if (type == ComputerType.PC) {
                return new PC();
            } else if (type == ComputerType.SERVER) {
                return new Server();
            } else {
                throw new IllegalArgumentException("没有其他类型的电脑了");
            }
        }
    }
    ...
}

// 使用
Computer pc = Computer.Factory.produce(ComputerType.PC);
Computer server = Computer.Factory.produce(ComputerType.SERVER);
```

将上面的 Java 代码翻译成 Kotlin 版本：

```kotlin
/**
 * 静态工厂方法（Kotlin版）
 *
 * @author GitLqr
 */
interface Computer {
    companion object Factory{
        fun produce(type: ComputerType): Computer {
            return when (type) {
                ComputerType.PC -> PC()
                ComputerType.SERVER -> Server()
            }
        }
    }
    ...
}

// 使用
val pc = Computer.Factory.produce(ComputerType.PC)
val server = Computer.Factory.produce(ComputerType.SERVER)
```

> 注意：伴生对象名称默认是 `Companion`，可以自定义，但是不管指不指定名称，使用时都可以省略不写，所以上面的代码也可以这样 `Computer.produce(ComputerType.PC)`，但有一种情况除外，如果是给伴生对象扩展属性或方法时，就必须写上伴生对象的自定义名称了。

我们知道，Kotlin 中伴生对象的名称是可以省略不写的的，结合运算符重载，上述代码可以进一步简化为：

```kotlin
/**
 * 静态工厂方法改良：重载【伴生对象】 invoke 运算符
 *
 * @author GitLqr
 */
interface Computer {
    companion object {
        operator fun invoke(type: ComputerType): Computer {
            return when (type) {
                ComputerType.PC -> PC()
                ComputerType.SERVER -> Server()
            }
        }
    }
    ...
}

// 使用
val pc = Computer(ComputerType.PC)
val server = Computer(ComputerType.SERVER)
```

## [#](https://fullstackaction.github.io/pages/d45f5d/#三、改良抽象工厂)三、改良抽象工厂

- 例子：电脑**品牌**厂商生产电脑
- 重点：内联函数（`inline` + `reified`）

现在增加了品牌厂商的概念，比如 Dell、Asus 等，如果用简单工厂模式，则需要再创建 n 个品牌厂商工厂类，比如 DellComputerFactory、AsusComputerFactory，品牌厂商众多，为了后续扩展，需要对工厂进行抽象：

```kotlin
/**
 * 各品牌电脑
 *
 * @author GitLqr
 */
interface Computer
class Dell : Computer
class Asus : Computer

/**
 * 各品牌厂商
 *
 * @author GitLqr
 */
abstract class AbstractFactory {
    abstract fun produce(): Computer
}

class DellFactory : AbstractFactory() {
    override fun produce() = Dell()
}

class AsusFactory : AbstractFactory() {
    override fun produce() = Asus()
}
```

抽象工厂模式，一般会在抽象工厂类中提供一个根据 `参数` 获取具体工厂实例的方法，结合 Kotlin 的重载运算符特性，该方法可以这么写：

```kotlin
/**
 * 抽象工厂：根据方法参数构建工厂实例
 *
 * @author GitLqr
 */
abstract class AbstractFactory {
    abstract fun produce(): Computer

    companion object {
        operator fun invoke(type: String): AbstractFactory {
            return when (type) {
                "dell" -> DellFactory()
                "asus" -> AsusFactory()
                else -> throw IllegalArgumentException()
            }
        }
    }
}

// 使用：
val factory = AbstractFactory("dell")
val computer = factory.produce()
```

> 注意：该 `参数` 是什么东西并没有限制，可以是字符串、枚举、具体工厂实例等等，在《Kotlin 核心编程》中，案例使用的参数是传入具体工厂实例，我个人认为这样不妥，因为工厂模式的核心就是 `隐藏对象实例的创建逻辑，而不需要暴露给客户端` ，所以这里我改用为字符串来做区分。

这里要思考一个问题，实际项目中使用字符串方式来区分工厂类型并不合理，因为会造成调用处硬编码的问题，改用枚举会更加合适，但是枚举会增加类文件啊，那么有什么方案可以规避掉上述两种弊端呢？很简单，直接把具体 `Computer` 的类类型传进方法内做判断：

```kotlin
import java.lang.reflect.Type

/**
 * 抽象工厂传参优化（Java反射包）
 *
 * @author GitLqr
 */
abstract class AbstractFactory {
    abstract fun produce(): Computer

    companion object {
        operator fun invoke(type: Type): AbstractFactory {
            return when (type) {
                Dell::class -> DellFactory()
                Asus::class -> AsusFactory()
                else -> throw IllegalArgumentException()
            }
        }
    }
}

// 使用
val factory = AbstractFactory(Dell::class.java)
val computer = factory.produce()
```

> 注意：在 Java 中，类类型对应是用 `java.lang.reflect.Type` 来表示，一般通过 `类.class` 这种方式来获取，对应到 Kotlin 的写法就是 `类::class.java`

你应该注意到了，这个 `Type` 是 Java 反射包中的类，而 Kotlin 完全兼容 Java，自然可以使用 `java.lang.reflect.Type` 来表示类类型，不过，Kotlin 自身也有一套反射机制，可以使用 `kotlin.reflect.KClass` 来表示类类型，所以，使用 Kotlin 反射 API 版本如下：

```kotlin
import kotlin.reflect.KClass

/**
 * 抽象工厂传参优化（Kotlin反射包）
 *
 * @author GitLqr
 */
abstract class AbstractFactory {
    abstract fun produce(): Computer

    companion object {
        // operator fun invoke(type: KClass<*>): AbstractFactory
        operator fun invoke(type: KClass<out Computer>): AbstractFactory {
            return when (type) {
                Dell::class -> DellFactory()
                Asus::class -> AsusFactory()
                else -> throw IllegalArgumentException()
            }
        }
    }
}

// 使用
val factory = AbstractFactory(Dell::class)
val computer = factory.produce()
```

> 注意：`KClass<*>` 中的 `*` 是一个通配符，表示接收任意类类型；而 `KClass<out Computer>` 中使用了 `out` 关键字，这是 Kotlin 中的泛型协变，表示只接收 `Computer` 子类的类类型。

其实，通过 `AbstractFactory(Dell::class)` 这种方式来获取具体工厂实例已经够用了，但是使用泛型还可以进一步简化代码，最终写法为：`AbstractFactory<Dell>()` ，是不是更加直观优雅？那么要怎么使用泛型来改造上面的方法呢？要知道 Java 泛型是在 1.5 之后才有的，为了向后兼容，泛型参数类型会在编译期被擦除（纯粹的历史包袱 =_=），所以在 Java 中要获取一个泛型的参数类型是十分困难的，而 Kotlin 的内联函数(`inline`)配合 `reified` 关键字，却可以做到具体化泛型参数类型，从而让获取 泛型参数类型 变得尤为简单：

```kotlin
/**
 * 抽象工厂改良：根据泛型参数类型构建工厂实例（inline + reified 具体化泛型参数类型）
 *
 * @author GitLqr
 */
abstract class AbstractFactory {
    abstract fun produce(): Computer

    companion object {
        inline operator fun <reified T : Computer> invoke(): AbstractFactory {
            return when (T::class) { // 不使用 reified 的话，T::class 会报错
                Dell::class -> DellFactory()
                Asus::class -> AsusFactory()
                else -> throw IllegalArgumentException()
            }
        }
    }
}

// 使用
val factory = AbstractFactory<Dell>()
val computer = factory.produce()
```

## [#](https://fullstackaction.github.io/pages/d45f5d/#四、补充)四、补充

在 [【二、改良简单工厂】](https://fullstackaction.github.io/pages/d45f5d/#二、改良简单工厂) 部分提到了伴生对象指定名称问题， 这里做一下补充。假设 Computer 是由其他同事或第三方人员编写的，我们不方便直接在其伴生对象中增加新功能，这时，可以使用 Kotlin 的扩展特性，给伴生对象扩展方法，比如给 Computer 增加一个功能，通过 CPU 型号来判断电脑类型：

```kotlin
/**
 * 伴生对象扩展方法（默认名称）
 *
 * @author GitLqr
 */
fun Computer.Companion.fromCPU(cpu: String): ComputerType? = when (cpu) {
    "Core" -> ComputerType.PC
    "Xeon" -> ComputerType.SERVER
    else -> null
}

// 使用
val type = Computer.fromCPU(pc.cpu)
```

如果此时 Computer 中的伴生对象已经指定了名称为 `Factory`，那么在给伴生对象扩展方法时就必须使用对应的伴生对象名称，而不是默认的 `Companion` 了：

```kotlin
interface Computer {
    // 自定义伴生对象名称
    companion object Factory { ... }
}

/**
 * 伴生对象扩展方法（自定义名称）
 *
 * @author GitLqr
 */
fun Computer.Factory.fromCPU(cpu: String): ComputerType? = when (cpu) { ... }

// 使用
val type = Computer.fromCPU(pc.cpu)
```

结论：

- 扩展伴生对象方法时，如果伴生对象有自定义名称，则使用自定义名称进行扩展。
- 无论伴生对象是否有自定义名称，调用时均可省略不写。