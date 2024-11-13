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



  Kotlin教程笔记(5) - 常量与变量

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABKFJREFUSA3tVl1oFVcQnrMbrak3QUgkya1akpJYcrUtIqW1JvFBE9LiQ5v6JmJpolbMg32rVrhgoYK0QiMY6i9Y6EMaW5D+xFJaTYItIuK2Kr3+BJNwkxBj05sQY3b3nM6cs2dv9t7NT/vQJw/sndk5M/PNzJkzewGerP+pAmy+ON8lLzUJgA8ZYxYIYZmGYRnctDaWvJJAmTtfP1pvXsBCCPP8QFcCaRkZYACgDZFO4stNIcBCajEOlmmC9XpJ9bAGCaPaPmzPl32dvLSVu3BWCTQs0XQQ6g0DYgwLIoAZbBCdW/i+781o1VVlm/410mw4h06Y7bIPHNyWDyL4FHkX03Q8SrzNhZTZriieckWt7cL6MM85YcLpsi/7O9/iXFT6MswI0DmmpkSaJ0qLxFIm3+i1THHB3zmBH3PYx9CcykcLOeQVVa7QtdxTgQgEleX2AjHYfwA+2ddV77ruGoJUbhGDI09YSNXyMpUt5ylOzxgbUmtOp7NmbNt8v3arjTBfYELmLUV+M+nSawNNAUqpT3ClJWg5I3BLT+cGW/DXNGCa6tx1aakCGEigArTn4TDIPdrXXYKCZNrHLMCOEPvHBlLQ99s9eHB7EB6NTki73CVPQ2F5MSx/uRQixfmq7rK0wYD8w8E905bnPDfwoWs/rfv93NWN/ZfvwsLIU7A09gxECyISeGJkHAau98L97tuw7NXnoPyNF8FcYGLGKsOs0mN3OEyec9esGW/ZEl945dTP34wlR2FZVQWU1q0Cw8Tr7p+hgLLNL0FPxx/Q35mA8aEUrH6nCgwEl0tn7wUiZYJnNRh6DK4UH/k0lfyrsBKdPVv/AriGIQcEDQZ65LBAGe2Rzui9Ybjz7XUppz1/uKBbyVPGkN3ZAeC6hr0x7Nr38N5+EqkoOm17xpoqR9ohQF55ERSvr4Dkr3chNfC3DMzGJlNBElW8w9nsGQvhNGIzDkXzCg8cLK951xHsFBlTJspJNi3ZFIMF2AeDV3q8DNOB+YHi6QTrChDIWDBRi5U5f+ZMfJLu3ccrqxtdxk4SKH336LFxSmkqefwU5T8fhdSdQf9IVKD6aNiwI/hnmcAZ91isYMJIaCUCx9W098+LgruikeTqzqqxKPUwqJyCPJiyemVVZBOijDGjD38Os0jOiSPL1z3SPjXNANbiNPXAdzTfukjjuknNBbyz3nwgTd3AVFqUJ5hpHlq9MveLnWwttUfoygBmvVjuikxND3znrhsELnZk7k+OjIGxeNEkomyLVta0xxn+HZhjBc4YZ/AFjHjz9u3xRZl2BN4aq9nFwWh16IrQ1aHHEd3j1+4/dB9OtH4e29A2H1DyHQRmOSfQZ1Fy7MHBTGB6J/Djq6p3OxyO2cB+4Car7v/o3GXgfAkj23+x9ID1Teoamo/SXcbvSf2PX7Vc8DdCmE1vN9di+32P9/5YR3vLnhCVGUWBjEkr3yh4H8v9CzmsbdhzOKzsJKM90iFdaTMjRPhGVsakRvOaRidljo6H6G7j+ctrJpsP+4COhDIl0La2+FS4+5mlocBaXY5QnGZysIBYoeSsl5qQzrSj/cgNrfuEzlWBfwA+EjrZyWUvpAAAAABJRU5ErkJggg==)Kotlin - 常量与变量



## [#](https://fullstackaction.github.io/pages/661407/#常量)常量

Kotlin 中的常量使用 `val` 修改，一旦定义值后"不可再修改"，常量类型分 2 种：

- 运行时常量(`val`)：编译期不能确定它的值，代码中会保留变量对它的引用。
- 编译期常量(`const val`)：编译期就知道值，并且会把代码中所有对它的引用都替换成它的值。

下面我们来举例看看，这两者在代码层面上的区别到底是什么。

### [#](https://fullstackaction.github.io/pages/661407/#运行时常量-val)运行时常量(`val`)

这是一段很简单的 Kotlin 代码，先定义一个常量 FINAL_NAME，再定义一个变量 myName 引用常量 FINAL_NAME：

```kotlin
val FINAL_NAME: String = "lqr"
var myName = FINAL_NAME
```

通过 IDEA 自带的 `Show Kotlin Bytecode` 工具将 Kotlin 代码转换成二进制，再反编译成 Java 代码：

```java
@NotNull
private static final String FINAL_NAME = "lqr";
@NotNull
private static String myName;
...
static {
    myName = FINAL_NAME;
}
```

结论：Kotlin 中变量对 `val常量` 的引用，会转变成 java 语言在 static 代码块中的赋值语句，即变量在编译期只保留了 `val常量` 的引用。

> `Show Kotlin Bytecode` 工具所在路径：Tools -> Kotlin -> Show Kotlin Bytecode

### [#](https://fullstackaction.github.io/pages/661407/#编译期常量-const-val)编译期常量(`const val`)

跟上面一样，先定义一个常量 FINAL_CONST_NAME，再定义一个变量 myConstName 引用常量 FINAL_CONST_NAME：

```kotlin
const val FINAL_CONST_NAME: String = "lqr"
var myConstName = FINAL_CONST_NAME
```

通过 IDEA 自带的 `Show Kotlin Bytecode` 工具将 Kotlin 代码转换成二进制，再反编译成 Java 代码：

```java
@NotNull
public static final String FINAL_CONST_NAME = "lqr";
@NotNull
private static String myConstName = "lqr";
```

结论：Kotlin 中变量对 `const val常量` 的引用，会转变成直接赋值语句，即编译期会把代码中所有对 `const val常量` 的引用都替换成它的值。

> Kotlin 中 `val常量` 仅仅只是类似 Java 中的 final 常量而已，而 `const val` 常量，才是真正对应 Java 中的 final 常量。因为 Java 中的 final 常量是编译期常量。

## [#](https://fullstackaction.github.io/pages/661407/#变量)变量

与常量不同，变量是后续可修改的，Kotlin 中使用 `var` 定义：

```kotlin
var myName: String = "lqr"
myName = "吴彦祖"
```

那如果对 `val常量` 再执行赋值操作会怎样呢？

```kotlin
val FINAL_NAME: String = "lqr"
FINAL_NAME = "吴彦祖" // 报错：Val cannot be reassigned
```

`val常量` 如此，`const val常量` 也是一样的，就不多废话了。

## [#](https://fullstackaction.github.io/pages/661407/#类型推导)类型推导

Kotlin 支持类型推导，当常量或变量在定义并且赋值时，Kotlin 就已经明确了该常量或变量的类型，于是常量或变量的类型可省略：

```kotlin
val string = "Hello" // 推导出 String 类型
val int = 5 // Int 类型
var x = getString() + 5 // String 类型
```

> 注意：Kotlin 是支持类型推导的强类型语言，不同于 python、js 中的动态类型，Kotlin 中一旦确定了变量类型，后续将不可修改。