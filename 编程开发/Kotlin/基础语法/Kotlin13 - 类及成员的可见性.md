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



​     Kotlin教程笔记(13) - 类及成员的可见性

# ![img](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAAXNSR0IArs4c6QAABH1JREFUSA3tVl1oHFUUPmdmd2ltklqbpJDiNnXFmgbFktho7YMPNiJSSZM0+CAYSkUELVhM6YuwIPpgoOKDqOBDC0XE2CQoNtQXBUFTTcCi+Wlh1V2TQExsUzcltd3M9Tt3ZjZzZ2fT+OJTL8yeM+eee757fmeJbq//KQL8X3DUSFOcfr7cRsRtxNQMWueeVzOkaITIGqQHNg5y8+jNW9ldM7A6nTpAjuolUikAwq7CE3WcM2RRDz+XGVgN3FptU/aUSlvq9Pa3iZ1+sgAqJyyAFqkipd9dqiwHF3P65YycLWc/6sqGrvoEoIp6DOFaX5h6+dnfjkWprwqsPk0dUGq5vySwDImC10KxFHgGL1SWoc92O3eVht09qdXNH11I2SsTsJYqMWzihqGMi+A+Garf3BAuuLI5oGlULyNfyB/HYNujwktOfRrMr5t77NmevqaUopx0grnKAyvVpmwUDB4x6FPXuGvYLTDwWsejwgtgkYKPqRJg8SV6xaiZ3ZTppGneS4yfH5/66fZSDHv+QZci/+h5c5UHtpy67JUqGppM0sh0Nc1dW6/N1W5Yoqat8/TU/VnadmdeW2PLLSyh0cvxBs3KbqTmwYPpxN4do/mzE8nEpvX/UMu2Wbp74zUAK5q6WkHns7V0eWkdPbPzd3rxkTGybadYySumVzhcaJFbs5UrEkQ/+CK8gF5dnh/6ciIZ73gwQ927L1IitoxKLXYP3SjYdOrHHfTZhRRlFyrorafPk20B3HPD1y2G3qKZME5Jcf3t/HUC13/8tSd++vqFveMUTwAUxSUFI1QekR1+bIze3D9MF2aq6cPvG72CgnldWCFqyRw3lwH8ZMerjTD9ElRO7Gv44wNpC90aASqGfVlz/Rx17srQ57/UU26hkhQqUB7dBR71WmzQhHUnblGmVOEw0jhbV1n9OlXUDCIRGaNV5Jp43N516fN7JmnTHdfp7Hgy0luO4aMhtkLL8Bi3bUWYvzh5Mn1dTxrL6QmGuRhGL/TiTTxRoEdTszSaq9GR0NGA3KdkOz3hqSV3MIDhQ5IVX/Ivx3umBti2es2h4eZby7x8br1rkf7Mo90AqC8aQ3sJeNzqFRu+vSANAQe3PL7l0HGOAdwDCeZYvNKeoZp1Qfs6Aipndh86HmFRi0LAnEO47wsqM6cdfjh3jBPUzhZy7nvlUfFsamED1VQt6aISHVymXZ/B2aCtIG8AI8xfobj2d3en1wWVhOeHELKmLQ1s211s88comkv4UCwWyF787mJdYXtNfhKAXVqnKTq8QZvGAGGOfaTo5pGZ/PwbUCr5+DPr/1J92JNHr9aOl/F3iI5+O1nfybsGxoimvZ3ViWSluDITw3P37mypheDIPY0tw7+O/5ApbkYw+zpfaUVu32Pi98+defdUhEpZkRFq0aqyNh9FuL9hpYbEm6iwi0z2REd09ZmyENEbuhjDWzKvZXTqKYaBIr3tt5kuPtQBZFvEUwHt60vfCNu41XsksH9Ij1BMMz1Y0OOunHNShFIP5868g5zeXmuLwL9T4b6Q2+KejgAAAABJRU5ErkJggg==)Kotlin - 类及成员的可见性



## [#](https://fullstackaction.github.io/pages/7b4815/#类及成员可见性)类及成员可见性

Kotlin 中可见性有 4 个级别：`private` -> `protect` -> `internal` -> `public`，从左至右可见范围逐渐放宽。

| Kotlin       | Java          | 可见性                  |
| :----------- | :------------ | :---------------------- |
| private      | private       | 自己可见                |
| protected    | protected     | 子类可见                |
| -            | default(默认) | 包内可见(Java 特有)     |
| internal     | -             | 模块内可见(Kotlin 特有) |
| public(默认) | public        | 外部可见                |

为了方便理解，这里举个例子，一个父亲的零花钱只能自己使用(`private`)，游戏机可以给孩子使用(`protected`)，族谱可以给村里人使用(`internal`)，名片可以给所有人使用(`public`)。

```kotlin
open class Father {
    private val pinMoney = 200 // 零花钱
    protected val gamePlayer = Switch() // 游戏机
    internal val familyTree = FamilyTree() // 族谱

    // public val callingCard = CallingCard()
    val callingCard = CallingCard() // 名片
}
```

因为 kotlin 中类及成员可见性默认是 `public`，所以 `public` 可以不写。来看看子类 Son 中访问父类 Father 中成员属性会是如何：

```kotlin
class Son : Father() {
    fun getFromFather() {
        val pinMoney = super.pinMoney // IDE报错：Cannot access 'pinMoney': it is private in 'Father'
        val gamePlayer = super.gamePlayer
        val familyTree = super.familyTree
        val callingCard = super.callingCard
    }
}
```

可见子类最多可以访问父类 `protected` 级别的成员，再来看看外界访问 Father 成员属性的情况：

```kotlin
fun main(args: Array<String>) {
    val father = Father()
    val pinMoney = father.pinMoney // IDE报错：Cannot access 'pinMoney': it is private in 'Father'
    val gamePlayer = father.gamePlayer // IDE报错：Cannot access 'gamePlayer': it is protected in 'Father'
    val familyTree = father.familyTree
    val callingCard = father.callingCard
}
```

外界最多可以访问类中 `internal` 级别的成员。internal 是模块内可见，这里的模块指的是 IDEA 项目结构中的 Module（ModuleB 不能访问 ModuleA 中 internal 类与成员），有兴趣的话，可以自己尝试下。

> Kotlin 中的 internal 与 Java 中的 default 是不一样的，所以，如果代码要做到两者互通的话，建议还是少用 internal。