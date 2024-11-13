## 为什么要搭建图床？

经常在博客写文章或者搭建自己的网站时，肯定需要往里面加图片对吧。有人可能会想，我直接把图片保存在电脑上不就行了？其实这样也不是不可以，但问题来了，如果你想把你的文章转载到别的地方，那些在本地的图片别人是看不到的，你得一个个去复制粘贴，真是够呛！

这时候，如果用阿里云OSS或者腾讯云COS来搭建一个图床，问题就迎刃而解了。用这些服务，处理图片简直高效到不行。说到国内用得多的，腾讯云和阿里云绝对是排前面的，速度快，就是要花点钱。至于GitHub的gitee，那是免费的，但是最近被封了，很多小伙伴都都已经深受其好，而且速度超慢。

之前一直在薅mdnice的免费图床羊毛，这两天发现网站上的图片无法显示了，桑心，只能自己动手来搭建图床，找了一圈，Typora+PicGo+阿里云OSS/腾讯云COS的组合较多，接下来跟着我这个手残党一起来一步一步搭建图床吧，我选择的是阿里云作为例子，这里并不是对腾讯云有什么偏见哦，腾讯云也非常棒，大家自己选择。

## 阿里云OSS搭建图床

## 1. 注册登录阿里云



打开阿里云官方网站[https://www.aliyun.com/product/oss](https://link.zhihu.com/?target=https%3A//www.aliyun.com/product/oss%3Fsource%3D5176.11533457%26source%3D5176.29345612%26userCode%3Dywqc0ubl)，点击右上角的登录/注册，参考教程：[注册阿里云账号和实名认证](https://link.zhihu.com/?target=https%3A//www.yundashi168.com/492.html)



![img](https://pic1.zhimg.com/80/v2-b0e7a6bbbe4175a0f109b3e366c0bbc8_720w.webp)



直接打开手机支付宝的扫一扫，扫描页面上的二维码，然后授权登录即可。



![img](https://pica.zhimg.com/80/v2-ce372e4462aa23a678e7178818061f1e_720w.webp)



## 2. 开通OSS服务

如果你还没有开通对象存储服务OSS，那么点击立即开通，现在新人可以免费试用三个月，存储包 20 GB。



![img](https://pic4.zhimg.com/80/v2-94d738e4fca88dbbd05a0b343f1dc14f_720w.webp)



再点击立即开通



![img](https://pica.zhimg.com/80/v2-10690560dc09760ba9b0b0c9dffedf52_720w.webp)



勾选服务协议后，点击立即开通



![img](https://picx.zhimg.com/80/v2-b6413fa17ba9daba0d8f3ad98c623b19_720w.webp)



## 3. 创建OSS Bucket

开通成功后，点击管理控制台



![img](https://pic2.zhimg.com/80/v2-5141303f1e5cf1941471946e323adc7d_720w.webp)



进入控制台之后，点击红框的立即创建或者创建Bucket，都可以创建Bucket



![img](https://pic1.zhimg.com/80/v2-a9bb6321439aad07e9c37f7e2304fa46_720w.webp)



接下来填一些必填的信息：

- Bucket 名称：必须全局唯一，和你在游戏中取的名字一样，不能和别人的重名，一旦创建不可更改。
- 地域：选择“有地域属性”，然后选择一个离自己位置近的地域。
  存储类型：选择“标准存储”即可。
- 存储冗余类型：推荐选择“本地冗余存储”，“同城冗余存储”更贵，如果网站有较高的并发流量可以选择这个。
- 读写权限：一定要选择“公共读”，否则平台无法通过公网访问 Bucket 中的内容。
- 其他选择默认，无需修改。



![img](https://pica.zhimg.com/80/v2-689319f74846e1c59414f3861e05d1d2_720w.webp)



点击下面的确认按钮，然后点弹出框的我知道了，确认创建。



![img](https://pica.zhimg.com/80/v2-6d464d7662772e5530868b4e389eca16_720w.webp)



创建成功，点击进入Bucket



![img](https://pic4.zhimg.com/80/v2-b576e2b5bee7e0765eb499644a65dd29_720w.webp)



## 4. 记下Bucket信息

点击概览



![img](https://pic2.zhimg.com/80/v2-9b212f40d4f879fdb650530ff57d6321_720w.webp)



进入概览页面，这里可以看到bucket的整体信息。
用文本软件记下红框画起来的几个信息，等会儿配置PicGo要用：

- Bucket名称：aitechshare-com
- Endpoint（地域节点）：xxxx
- Bucket域名（外网地址）：xxxx



![img](https://pica.zhimg.com/80/v2-f4a111def41ba16b3210f688a31ff40c_720w.webp)



## 5. 创建AccessKey

在页面右上角，鼠标放在头像处，在弹出的框里选择AccessKey管理



![img](https://pic3.zhimg.com/80/v2-3bf58af115c37fc1840177f87b472458_720w.webp)



在弹出的选项框里，选择继续使用AccessKey。



![img](https://pica.zhimg.com/80/v2-f63a13293f37a567a27370dd16546864_720w.webp)



点击创建AccessKey，在弹出的安全验证窗口中，选择一个方式来通过安全验证。



![img](https://pic2.zhimg.com/80/v2-c146d4dca65ce67100dc87fba4351067_720w.webp)



把图中的资料下载成csv，或者复制下来保存好，这个类似于你的密码，一定不要泄露。



![img](https://picx.zhimg.com/80/v2-7bde1d6f7a8982b5c40795a7fa6ceaad_720w.webp)



## 6. 创建子账户用来配置PicGo

重要！上面生成的AccessKey是主账户的，它也可以用来配置picgo，但是如果我们只是需要使用OSS，强烈建议使用子账号来访问这个Bucket，这样可以规避主账户AccessKey或者密码泄露导致的问题。步骤如下：
点击创建 AccessKey，再点击开始使用子用户 AccessKey



![img](https://pic2.zhimg.com/80/v2-7866bbc26d9f980788c46577fb6ed679_720w.webp)



点击创建用户



![img](https://picx.zhimg.com/80/v2-f43bb493f34ebc8871f7328052d6d757_720w.webp)



填写好登录名称，显示名称，勾选控制台访问，OpenAPI调用访问，其他选择默认就好，点击确认，在弹出的安全验证中选择一种方式完成验证。



![img](https://pic2.zhimg.com/80/v2-902d03d5881f6ebfea5e509450f1ccf3_720w.webp)



将红框中的AccessKey Id和AccessKey secret复制出来保存好，配置PicGo时要用到。



![img](https://pic3.zhimg.com/80/v2-000d885371b8c685f2f342601c3bd998_720w.webp)



## 7. 配置子账户OSS权限

勾选中用户，点击添加权限，再点击下面两项权限，加到已选择框中。

选择这两项：

- AliyunOSSFullAccess——管理对象存储服务（OSS）权限
- AliyunOSSReadOnlyAccess——只读访问对象存储服务（OSS）的权限



![img](https://pic3.zhimg.com/80/v2-a9fe3f84ae6af001bacb681aea438492_720w.webp)



点击确定，授权成功了，这时阿里云相关的配置就弄好了。 之前让保存的信息要记好哦，后面还会用到。



![img](https://pica.zhimg.com/80/v2-b6d4038c10734930a11c47e253fafada_720w.webp)



如果后面不需要使用该账号，点击用户后面的删除选项即可。

## 配置PicGo

## 1. 安装PicGo

PicGo是一款功能非常强大的图床工具，支持SM.MS、腾讯COS、GitHub图床、七牛云图床、Imgur图床、阿里云OSS、gitee等多种图床平台。

下载地址：[https://github.com/Molunerfinn/PicGo/releases](https://link.zhihu.com/?target=https%3A//github.com/Molunerfinn/PicGo/releases)
下载正式版或者测试版都可以，正式版会稳定一些，测试版有一些尝鲜功能，用国内可下载链接进行下载会快一些，我这里选择的是[PicGo-Setup-2.4.0-beta.6-x64.exe](https://link.zhihu.com/?target=https%3A//picgo-release.molunerfinn.com/2.4.0-beta.6/PicGo-Setup-2.4.0-beta.6-x64.exe)这个测试版。



![img](https://pic1.zhimg.com/80/v2-94c1d61d22d2238584ffedc5180c344a_720w.webp)



安装好了之后，打开界面是这样的。



![img](https://picx.zhimg.com/80/v2-c1843f77fc3c57a70a55aec9931e157b_720w.webp)



## 2. PicGo配置阿里云OSS

点击图床设置，阿里云OSS，点击画笔修改。



![img](https://pic4.zhimg.com/80/v2-bae293cf3330699b307a18f2f6c01a25_720w.webp)



填上前面记录好的值即可

- AccessKey ID（账号）：xxxxxxxxxx
- AccessKey Secret（密钥）：xxxxxxxxxx
- 设定Bucket：刚刚在阿里云OSS中创建的Bucket名称
- 设定存储区域：地域节点中的第一个字段

**划重点！这里一定要注意，设定存储区域里要填的是之前记下来的地域节点里面的第一个字段，比如你的地域节点值是[http://oss-cn-shanghai.aliyuncs.com](https://link.zhihu.com/?target=http%3A//oss-cn-shanghai.aliyuncs.com)，那么这里只需要填oss-cn-shanghai，切记，否则配置失败无法上传图片。**

- 设定存储路径：自定义，以/结尾（相当于文件夹），例如 img/

填完了记得拉到下面点击确认保存。



![img](https://pic1.zhimg.com/80/v2-068518b6bf648a860d1e878c1ea03cfc_720w.webp)



点击设为默认图床



![img](https://picx.zhimg.com/80/v2-3b3eaaecf6d3d5103fa409fbf9771441_720w.webp)



## 3. PicGo其他配置

你可以根据喜好来设置文件以时间戳格式命名 和 上传后自动复制URL：



![img](https://pic4.zhimg.com/80/v2-601e84d2a520c4b61aab0f8f9e6e985f_720w.webp)



上传图片，测试成功！



![img](https://pic2.zhimg.com/80/v2-35d832a148e50bd56bf23492f3494681_720w.webp)



到这里PicGo就配置完成了

## 配置Typora

Typora是一款简洁而强大的Markdown编辑器。它提供实时预览功能，让用户可以即时查看文档的渲染效果。Typora采用所见即所得的编辑模式，没有繁杂的标记符号，用户可以专注于写作而不必分心处理格式。此外，Typora还支持数学公式、表格、图像等丰富的Markdown语法和扩展功能。总之，Typora是一款易用且功能丰富的Markdown编辑器，适用于撰写各种类型的文档。

## 1. 下载安装Typora

登录Typora官网[https://typora.io](https://link.zhihu.com/?target=https%3A//typora.io/)，拉到最下面下载Typora.



![img](https://pica.zhimg.com/80/v2-a035d73fce0ec79e2b1f6dfa30819624_720w.webp)



目前Typora已经收费，不过我们还可以考虑用其他办法来使用它，比如这个[https://nav.vpssw.com/sites/927.html](https://link.zhihu.com/?target=https%3A//nav.vpssw.com/sites/927.html)

## 2. 配置Typora连接PicGo

打开Typora之后，页面非常简洁。
点击左上角文件-偏好设置-图像，插入图片时选择上传图片，上传服务选择PicGo(app)，PicGo 路径选择你安装到本机的PicGo的目录，选中PicGo.exe。
都填好了，不要忘记点击验证图片上传选项来验证一下。

![img](https://pic3.zhimg.com/80/v2-c8ac255224b1a2aa44b49d0a07923606_720w.webp)



验证成功!



![img](https://picx.zhimg.com/80/v2-88d650eb277fba200cbf42e36213a223_720w.webp)



这时候你再打开Picgo，可以看到Typora自动上传了测试图片到Picgo，表示已经连通。



![img](https://pic3.zhimg.com/80/v2-a30cce77ce270d6eebaeb7e0eec38498_720w.webp)



好了，所有的配置都完成了，你也赶快去试一试吧~

## 总结

PicGo最大的特点是，可以和阿里云，腾讯云等各大图床软件连接，又可以和Typora结合使用，配置好关联之后，在使用Typora写文章时，如果需要插入图片，只需要将图片复制粘贴到Typora的编辑区域，就会自动通过PicGo上传到指定图床，自动复制外网能访问的URL并展示，简直不要太方便，极大的解决了编辑文章时复制处理图片链接的痛点。

相关链接：
[阿里云官网网站](https://link.zhihu.com/?target=https%3A//www.aliyun.com%3Fsource%3D5176.29345612%26userCode%3Dywqc0ubl)
[阿里云OSS](https://link.zhihu.com/?target=https%3A//www.aliyun.com/product/oss%3Fsource%3D5176.11533457%26source%3D5176.29345612%26userCode%3Dywqc0ubl)