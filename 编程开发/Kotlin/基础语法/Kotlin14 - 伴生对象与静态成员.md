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



​     Kotlin教程笔记(14) - 伴生对象与静态成员

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABGpJREFUSA3tVVtoXFUU3fvOI53UlmCaKIFmwEhsE7QK0ipFEdHEKpXaZGrp15SINsXUWvBDpBgQRKi0+KKoFeJHfZA+ED9KKoIU2gYD9UejTW4rVIzm0VSTziPzuNu1z507dibTTjL4U/DAzLn3nL3X2o91ziX6f9wMFdh6Jvbm9nNSV0msViVO6tN1Rm7NMu2OpeJ9lWBUTDxrJbYTS0hInuwciu9eLHlFxCLCZEk3MegsJmZ5K/JD6t7FkFdEvGUo1g7qJoG3MHImqRIn8/nzY1K9UPKKiJmtnUqHVE3Gbuay6vJE/N2FEmuxFjW2nUuE0yQXRRxLiTUAzs36zhZvOXJPdX850EVnnLZkB8prodQoM5JGj7Xk2mvC7JB8tG04Ef5PiXtG0UtxupRQSfTnBoCy554x18yJHI6I+G5Eru4LHmPJZEQsrvPUbMiA8G/WgMK7w7I+ez7++o2ANfbrjvaOl1tFMs+htG3IrZH9/hDX1Pr8Tc0UvH8tcX29KzAgIGcEkINyW5BF9x891hw6VYqgJHEk0huccS7vh3C6gTiODL+26huuBtbct8eZnqLML8PkxGYpuPZBqtqwkSjgc4mB5gbgig5i+y0UDK35LMxXisn9xQtK+nd26gTIHsHe/oblK/b29fUmN/8Y+9jAQrnBp56m1LcDlDp9irKTExSKduXJVWSqdBMA08pEJnEIOB3FPPMybu/oeV8zFeYN3xx576Q6RH+VmplE4ncQV5v+5rzSoyOU7PuEAg8g803PwBJ0CExno/jcMbN8tONYeOmHiuUNryvm3fRUy4tMPVLdAGkUhNWuggGrJcXPv+ouCjz0MKUHz1J2/E8IC9nqTabcxgaBYM0hPhD5Y65FsbxRQKxCQrDjDctW7PUM3HuZunFyifSAqEfuzCp48Il24luWUWZoyJCaPR82jE0+kFA643wRFVni4RYSq3ohJO2pZ7B5dO4xkDWbEpossJPLSrPjYID8rS2UHTlvyNxqIGsg674XJJ7vnh5L7PNwC4hh2sjCI96mzszOTpxLF0T7l88Yz7lAuK6OnL8gXLOnTvpzSb22YG8W7us3jSebFHeeqnXRG1vt+MoUM84LQIBmMsCTAcOauTh0T0l0neQK7m2bLMt2mGxU3HYssS0J2cdv5wljlPsrIuZLAG/2DOZIXgCYT8uMGZN+e2kSirfxZOPCsC0f24nTZzspnVn9VePS1Z5vubmAGGXG8ZFno9Hel0yfA5ZPhF7Dh972BQJ2qCpgH67lmWtBYbvk6sz02wjky2vXyz0XErP/kFB619js1BtwfOV4OPRqOQBjy3Qbk18vigUPPSD5ceHnwck7W9bhAqZdd7SuG7w4/P2F/GaJh8c7e9qgow+Q7cGBo+98WsLkuktFqiZabtXuQTu/Y5ETbR0v7tNSFnvrmu6pjdoan2KjMu8q/Hmj1EfCO2ZGfEIbIXKUlw8qaX9/b2oeSJmFksSeT/Fn0V3nSypChh4Gjh74ybO9aeZ/AN2dwciu2/MhAAAAAElFTkSuQmCC)Kotlin - 伴生对象与静态成员



## [#](https://fullstackaction.github.io/pages/c7c2c0/#object-关键字)object 关键字

Kotlin 中有一种特殊的类，它本身也是一个实例（单例），这种既是类又是对象的类需要使用 `object` 关键字声明（普通类声明使用 `class`），它跟普通类一样，也可以实现接口和继承父类：

```kotlin
object MusicPlayer : Player(), OnStatusChangeListener {

    var state: Int = 0

    fun play(url: String) {
        ...
    }

    fun stop() {
        ...
    }

    override fun onMount(driver: Driver) {
    }

    override fun onUnmount(driver: Driver) {
    }
}
```

这种 `object` 类的方法可以通过类名直接调用：

```kotlin
fun main() {
    MusicPlayer.play("http://qqmusic.com/123213.mp3")
    MusicPlayer.stop()
}
```

借助 `Show Kotlin Bytecode` 工具，将上述 Kotlin 代码反编译成 java 代码如下：

```java
public final class MusicPlayer extends Player implements OnStatusChangeListener {
   public static final MusicPlayer INSTANCE;

   private MusicPlayer() {
   }

   static {
      MusicPlayer var0 = new MusicPlayer();
      INSTANCE = var0;
   }
   ...
}
```

可以发现，Kotlin 中的 `object` 本质上就是 Java 中简单的单例模式，同时它的构造方法是 private 的，因此 `object` 类不能自定义构造方法！

## [#](https://fullstackaction.github.io/pages/c7c2c0/#伴生对象-companion-object)伴生对象(companion object)

日常开发中，经常会编写一些 Bean 类，用于描述一类事物，Bean 中会包含事物的属性，有的 Bean 类还会提供一系列"工具方法"来帮助开发者快速创建 Bean 对象，就比如在 Java 中，`Integer.valueOf()` 就可以帮助开发者快速将字符串转成整型，进入源码一看，可以发现这是一个使用了 `static` 关键字修饰的静态方法：

```java
public static Integer valueOf(String s) throws NumberFormatException {
    return Integer.valueOf(parseInt(s, 10));
}
```

可是，在 Kotlin 中是没有 `static` 关键字的！！！想要实现通过 `类名.xxx()` 的方式调用工具方法，可以使用上述的 `object` 类，但 `object` 本身就是一个对象，我们无法在外部调用其构造方法，既然想拥有 `object` 类(通过类名调用方法)与 `class` 类(外部可以调用构造方法)的两种特性，这时伴生对象 `companion object` 就完全可以满足这个需求：

```kotlin
class Rectangle(val width: Int, val height: Int) {
    companion object {
        fun ofSize(width: Int, height: Int): Rectangle {
            return Rectangle(width, height)
        }

        fun ofRectangle(rectangle: Rectangle): Rectangle {
            return Rectangle(rectangle.width, rectangle.height)
        }
    }
}

fun main() {
    val width = 4
    val height = 5
    val rectangle1 = Rectangle(width, height) // 调用构造方法
    val rectangle2 = Rectangle.ofRectangle(rectangle1) // 通过类名调用方法
    val rectangle3 = Rectangle.ofSize(width, height) // 通过类名调用方法
}
```

伴生对象顾名思义，就是与类一起诞生的对象，类一加载，它的伴生对象也就被创建了，每个类都可以对应一个伴生对象，并且该伴生对象的成员全局独一份，也就是说伴生对象 `companion object` 也是一种单例，再次借助 `Show Kotlin Bytecode` 工具，将上述 Kotlin 代码反编译成 java 代码如下：

```java
public final class Rectangle {
   ...
   public static final Rectangle.Companion Companion = new Rectangle.Companion((DefaultConstructorMarker)null);

   public static final class Companion {
      @NotNull
      public final Rectangle ofSize(int width, int height) {
         return new Rectangle(width, height);
      }

      @NotNull
      public final Rectangle ofRectangle(@NotNull Rectangle rectangle) {
         Intrinsics.checkParameterIsNotNull(rectangle, "rectangle");
         return new Rectangle(rectangle.getWidth(), rectangle.getHeight());
      }

      private Companion() {
      }

      // $FF: synthetic method
      public Companion(DefaultConstructorMarker $constructor_marker) {
         this();
      }
   }
}
```

可以发现，Kotlin 中的 `companion object` 其实对应到 Java 中也就只是 Rectangle 的一个静态内部类实例而已。

## [#](https://fullstackaction.github.io/pages/c7c2c0/#jvm-静态成员-jvmstatic)JVM 静态成员(@JvmStatic)

我们把上面 Kotlin 的 main 方法中的代码用 java 重写一遍：

```java
int width = 4;
int height = 5;
Rectangle rectangle1 = new Rectangle(width,height);
Rectangle rectangle2 = Rectangle.Companion.ofSize(width,height);
Rectangle rectangle3 = Rectangle.Companion.ofRectangle(rectangle2);
```

发现 `ofSize` 和 `ofRectangle` 方法并不是通过 Rectangle 类直接调用的，结合上述反编译后的 java 代码，应该不难理解，因为 Kotlin 中 Rectangle 的伴生对象本质上就是这个 `Rectangle.Companion` 实例，`ofSize` 和 `ofRectangle` 都是 `Rectangle.Companion` 的方法，所以，用 `Rectangle.Companion` 对象调用它自己的方法这完全没有毛病，可是，难道就不能在 Java 中也像 Kotlin 那样，直接通过 `类名.xxx()` 的方法来调用伴生对象方法吗？答案肯定是有的啦，Kotlin 提供了 `@JvmStatic` 和 `@JvmField`，可以让伴生对象中的方法和属性在 java 中通过类名直接调用：

```kotlin
class Rectangle(val width: Int, val height: Int) {
    companion object {
        @JvmStatic
        fun ofSize(width: Int, height: Int): Rectangle {
            return Rectangle(width, height)
        }

        @JvmStatic
        fun ofRectangle(rectangle: Rectangle): Rectangle {
            return Rectangle(rectangle.width, rectangle.height)
        }

        @JvmField
        val Tag = "Rectangle"
    }
}
```

这次 java 代码也可以使用 Rectangle 类名来调用 ofSize 和 ofRectangle 方法了：

```java
int width = 4;
int height = 5;
Rectangle rectangle1 = new Rectangle(width, height);
Rectangle rectangle2 = Rectangle.ofSize(width, height);
Rectangle rectangle3 = Rectangle.ofRectangle(rectangle2);
System.out.println(Rectangle.Tag);
```

再来反编译一次，看其究竟是什么原理，原来就只是在 Rectangle 中增加了对应的 static 属性和方法而已：

```java
public final class Rectangle {
   public static final Rectangle.Companion Companion = new Rectangle.Companion((DefaultConstructorMarker)null);

   @JvmField
   @NotNull
   public static final String Tag = "Rectangle";

   @JvmStatic
   @NotNull
   public static final Rectangle ofSize(int width, int height) {
      return Companion.ofSize(width, height);
   }

   @JvmStatic
   @NotNull
   public static final Rectangle ofRectangle(@NotNull Rectangle rectangle) {
      return Companion.ofRectangle(rectangle);
   }

   public static final class Companion {
      @JvmStatic
      @NotNull
      public final Rectangle ofSize(int width, int height) {
          ...
      }

      @JvmStatic
      @NotNull
      public final Rectangle ofRectangle(@NotNull Rectangle rectangle) {
          ...
      }
   }
}
```