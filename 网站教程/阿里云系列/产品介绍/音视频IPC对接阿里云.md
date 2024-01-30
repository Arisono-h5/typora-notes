# 什么是Link Visual、



Link Visual是生活物联网平台针对视频产品推出的增值服务，提供视频数据上云、存储、转发、AI计算等能力。

> 大白话就是：通过阿里云的Link Visual视频服务，可以让你的IPC摄像头设备完成上云功能，并快速实现如下功能介绍中的功能。其中可以享受阿里云P2P协议支持，帮助企业节省流量服务器流量带宽。

快速上手入门，请参考阿里云官网文档说明：[Link Visual视频开发技术文档](https://help.aliyun.com/document_detail/140539.html?source=5176.11533457&userCode=ywqc0ubl)



## 功能介绍

Link Visual提供的设备端SDK（支持各种标准的适配与统一），配合阿里云物联网标准化物模型，可实现最轻量级的设备上云连接。同时提供自有品牌App开发需要的API和SDK，可以为您打造一整套的设备连接云端、App开发控制等能力，再辅助云端转发、存储、视频AI等增值扩展服务，帮助您快速完成视频方案搭建，满足客户远程视频观看、存储、报警与控制需求等。

Link Visual主要提供以下功能。

- 云端摄像头视频直播
- 摄像头云端视频存储
- 云端、本地TF存储录像播放
- 语音对讲
- 远程摄像头控制
- 摄像头规则管理（报警、抓图、录像、检测识别等）
- 设备数据分析、云存储资源购买等运营管理功能

## 产品架构

Link Visual产品的功能链路及结构如下。


![Link Visual功能链路](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261623612.png)



## 应用场景

Link Visual主要面向的场景包括：家用级别的安防监控、视频采集直播存储场景等。



## 收费策略

  具体详细的收费策略请查看[：Link Visual收费策略详细说明](https://help.aliyun.com/document_detail/151917.html?source=5176.11533457&userCode=ywqc0ubl)  

>    如果您还需要用到阿里云的服务器，数据库，Redis数据库，消息中间件，短信或者其它任何产品，可以先点击领取  [阿里云内部优惠券](https://www.aliyun.com/activity?source=5176.11533457&userCode=ywqc0ubl)  (很多人还不知道阿里云有内部代金券,领取可减免不少现金)
>
> 这个内部代金券，最高可减2000元，云产品通用红包，可以叠加官网常规优惠使用。这个代金券是新用户专享的，如果你还没有注册阿里云账号，可以领取这个代金券。



![image-20240126163543346](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261635414.png)

- 智能云存储按照服务周期分为月套餐（按30天计）和年套餐（按365天计）。

  智能云存储主要指事件云存储，事件云存储服务是指设备接入阿里云且网络良好的情况下，当设备检测到监控画面变化，包括但不限于有人走过，物品移动，光线变化等事件的时候，设备会自动录像并上传到阿里云。

  事件云存储按照存储周期分为1天、3天、7天、14天、和30天。以7天循环事件年套餐举例，2019年1月1日，购买并立即生效，系统自动开始存储2019年1月1日至2019年1月7号时间段内产生的所有录像和图片。在2019年1月8号，系统会删除2019年1月1日的数据，并开始存储2019年1月8号产生的视频数据，依次类推。至2020年1月1日，服务到期，将不再存储新的数据（已存数据仍然可以查看）。至2020年1月8号，已存储数据将全部删除并不可访问。

- 赠送规则

  阿里云可以为购买视频激活码的每个量产设备赠送一份智能云存储套餐，但原则上每个设备只能领用一次，换一个用户账号绑定不可以再领取。考虑到您的消费类产品可能发生退回二次销售，允许一个设备最多在三个不同用户账号下各领用一次赠送套餐。您不得向用户宣传可以通过更换账号骗取赠送资源，否则阿里云有权立即收回赠送资源，并要求您支付所有赠送资源对应款项的三倍作为违约金。对于每个购买视频激活码的设备，阿里云可以赠送3个月7天的事件云存储套餐。赠送活动阿里云可随时停止。

- 购买和激活规则

  您自建的用户体系下，单个用户账号下可以同时购买多份智能云存储的月套餐和年套餐，多个有效套餐可以同时存在于一个用户账号下，但同一时刻只能有一个激活套餐。智能云存储套餐的激活可以选择立即生效还是延迟生效。立即生效会保留原套餐（原套餐按剩余天数保留，不满一天按使用了一天计算），但是立即切换到购买套餐上。延迟生效方式是新套餐在原套餐自然结束以后再生效。您可以基于用户需要允许同时拥有多个套餐的用户自行调整套餐激活顺序，默认是按照购买下单顺序激活。

  智能云存储套餐一旦购买立即生效。云存储作为虚拟商品，不支持退货，换货和退款，不退差价，可以停用。

  设备解绑以后，新用户账号绑定后不可以使用和访问原云存储的数据，新用户只能向您重新购买智能云存储。

  一个用户账号下的多个设备只能分别为每个设备购买智能云存储服务。

- 转移规则

  您自建用户体系的用户，如果为设备购买了智能云存储服务，不管是否解绑了该设备，智能云存储服务的剩余期限（非内容）都可以转移到任何该用户账号绑定的其他购买了视频激活码的设备上。转移的条件如下：

  - 能转移的智能云存储服务必须是购买的并且在有效期内，赠送的智能云存储服务不可以转移。
  - 能接受转移智能云存储服务的设备必须购买该用户账号绑定的LV设备，不可以在您自建用户体系内跨用户转移。



## 安全机制说明

设备数据安全问题是重中之重,  更详细的安全机制说明, 见[<<阿里云Link Visual安全机制说明文档>>](https://help.aliyun.com/document_detail/2546058.html?source=5176.11533457&userCode=ywqc0ubl)

| **业务场景**     | **安全机制** | **安全等级**                      | **使用方式**                                     |
| ---------------- | ------------ | --------------------------------- | ------------------------------------------------ |
| 设备身份认证     | 一机一密     | 较高                              | 云端控制台配置                                   |
| 一型一密         | 中           | 云端控制台配置                    |                                                  |
| 防串号           | 较高         | 需要设备端做少量开发              |                                                  |
| APP身份认证      | 安全登录     | 高                                | Andoird/iOS/PC默认支持                           |
| API安全          | 较高         | 默认支持身份及权限管控，HTTPS可选 |                                                  |
| 视频播放         | 播放数据加密 | 较高                              | 1.x版本播放器版本加密可选，2.x版本播放器强制加密 |
| 设备推流数据加密 | 较高         | 需要设备端做少量开发              |                                                  |



### 设备身份认证

设备接入生活物联网平台之前，需通过身份认证。目前平台支持的多种认证方式对比以及相关的风险说明，请参考[量产设备](https://help.aliyun.com/document_detail/611005.html?source=5176.11533457&userCode=ywqc0ubl)文档。

**对于一机一密设备，平台针对设备证书（即三元组，ProductKey、DeviceName、DeviceSecret）重复烧录的情况提供了防串号方案**（需要在设备端做少量开发）。不同APP分享方式下重复烧录的具体表现列举如下：



| **分享方式** | **设备不支持防串号**                                         | **设备支持防串号**                                      |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------- |
| 抢占式       | 当A用户绑定A设备后，B用户仍可绑定成功、且A用户自动解绑。当A设备上线后，B用户可看到A设备的画面。 | B设备无法上线，B用户无法绑定B设备，A用户正常使用A设备。 |
| 授权式       | 当A用户绑定A设备后，B用户无法再绑定设备，但B设备配网成功仍可正常上线。A用户可看到B设备的画面。 | B设备无法上线，B用户无法绑定B设备，A用户正常使用A设备。 |
| 共享式       | A用户绑定A设备成为管理员，B用户绑定B设备成为子成员。当A、B设备同时在线时，A和B用户能随机看到A、B设备的画面。 | B设备无法上线，B用户无法绑定B设备，A用户正常使用A设备。 |

### 防串号方案机制

开启防串号功能后，设备使用唯一UUID标识进行连云上线。设备成功上线后，该设备证书将绑定此唯一UUID，后续当同样设备证书的其他设备（UUID不同）上线时，云端会禁止该设备上线，从而避免隐私泄露。

UUID选取建议方式：

1. 从 IMEI/MAC地址/CPU序列号等信息中择一作为设备的UUID。使用此类设备信息请确保每次读取不会发生变化，若有偶现无法读取成功的情况，会导致设备有概率无法上线。
2. 带有持久化存储器件的设备，可在首次开机时创建UUID，并将其固化到存储器件中。

### 设备端开发方法

更详细的安全机制说明, 参考[<<阿里云Link Visual安全机制说明文档>>](https://help.aliyun.com/document_detail/2546058.html?source=5176.11533457&userCode=ywqc0ubl)

### APP身份认证

更详细的安全机制说明, 参考[<<阿里云Link Visual安全机制说明文档>>](https://help.aliyun.com/document_detail/2546058.html?source=5176.11533457&userCode=ywqc0ubl)

### 视频播放

LinkVisual提供了视频播放全链路传输加密机制，即使网络传输中的数据包遭到拦截，也能有效防止视频画面被非法获取。请按照如下方法对视频播放和设备推流分别做加密，否则存在用户隐私泄露风险。

更详细的安全机制说明, 参考[<<阿里云Link Visual安全机制说明文档>>](https://help.aliyun.com/document_detail/2546058.html?source=5176.11533457&userCode=ywqc0ubl)



## 快速体验

您可以根据本文档快速体验Link Visual服务的开发流程，并熟悉Link Visual的能力

1. 登录[生活物联网控制台](https://help.aliyun.com/document_detail/614922.html?source=5176.11533457&userCode=ywqc0ubl)。产品介绍: [阿里云生活物联网飞燕平台](https://cn.aliyun.com/product/livinglink?from_alibabacloud=&source=5176.11533457&userCode=ywqc0ubl)(什么是生活物联网平台? [生活物联网平台](https://help.aliyun.com/document_detail/614922.html?source=5176.11533457&source=5176.11533457&userCode=ywqc0ubl)是一个开发消费级智能IoT设备的平台. 更多说明参考:[阿里云生活物联网平台说明文档](https://help.aliyun.com/document_detail/614922.html?source=5176.11533457&source=5176.11533457&userCode=ywqc0ubl))
2. 单击控制台主页面右下角的**服务中心**，并单击**Link Visual**对应的**查看详情**。

![link visual](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261731460.png)

   3.从**项目选择**列表中，选择一个项目。

若您当前没有已存在的项目，请单击**创建项目**来创建一个新项目。详细操作请参见[创建项目](https://help.aliyun.com/document_detail/126400.html#task-1305446)。

   4.单击**服务流程**中的**快速创建产品**。



![flow1](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261754383.png)



5.配置视频产品的相关参数。

快速体验阶段您需要将**连网方式**设置为**蜂窝（2G/3G/4G）**（正式接入设备时请按设备的实际情况配置）。

![快捷创建产品](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261755207.png)   

产品创建成功后，页面自动跳转至产品的**功能定义**页面。

6.定义产品的功能属性。

生活物联网平台为视频产品提供了默认的功能定义，快速体验阶段您直接使用默认属性即可。

7.单击**下一步：设备调试**，添加调试设备。

 a.选择模组信息。

 快速体验阶段，您可以选择任意的模组信息（真正接入设备时请按实际情况选择）。

 b.单击**新增测试设备**，弹出**新增测试设备**对话框。

 添加测试设备后，可以免费使用平台提供的测试设备证书调试设备（每个产品最多可添加50个免费测试设备，测试设备的证书不能用于量产，仅供调试使用）。

![测试设备](http://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3640688951/p76134.png)

c.单击**确定**，对话框中显示测试设备的激活凭证。

图 1. 测试设备的激活凭证![设备激活凭证](http://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3640688951/p76135.png)

8.单击**下一步：人机交互**，选择App版本并获取配网二维码。

快速体验阶段，建议您使用公版App（云智能）来快速体验设备控制。

a.打开**使用公版App控制产品**的开关。

![选择App版本](http://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/9540688951/p76136.png)

b.单击**配网+App下载二维码**，获取配网二维码。

![配网二维码](http://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/9540688951/p76137.png)

c.在文本框中，输入[测试设备激活凭证图](https://help.aliyun.com/document_detail/151918.html?source=5176.11533457&userCode=ywqc0ubl)中的**DeviceName**，单击**生成二维码**。

图 2. 配网+App下载的二维码

![生成二维码](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261758040.png)

## 运行Link Visual Demo

生活物联网平台为您提供了Linux语言的Link Visual Demo，您可以根据以下步骤来运行该Demo，从而使用虚拟摄像头来体验Link Visual服务。

1. 下载Link Visual Demo。

   生活物联网平台提供了两种Link Visual Demo，请根据您的开发环境选择。

   - 基于Ubuntu的Link Visual Demo

     该Demo基于x86 64位Ubuntu 16.04系统上编译，在其他Linux版本上尚未验证过，推荐您安装相同的Ubuntu版本以规避兼容性问题。[单击下载基于Ubuntu的Link Visual Demo](https://g.aliplus.com/ilop/linkvisual/link_visual_ipc_ubuntu_1.2.2.tar.gz)

   - 基于Docker的Link Visual Demo

     Docker镜像提供更好的跨平台能力，您可以在Windows、Mac、Linux等操作系统上安装Docker软件，并在Docker系统上运行该Demo。[单击下载基于Docker的Link Visual Demo](https://g.aliplus.com/ilop/linkvisual/link_visual_ipc_docker_1.2.2.tar.gz)

   **说明**

   下载本Link Visual Demo，将默认您已同意[本软件许可协议](https://files.alicdn.com/tpsservice/64be8487cc5d8fe6d3c84e4dc9a93c17.pdf?spm=a2c4g.11186623.2.15.5e5fe2b0YTDVc9&file=64be8487cc5d8fe6d3c84e4dc9a93c17.pdf)。

2. 运行Link Visual Demo程序。

   - Ubuntu的Link Visual Demo

      

     ```shell
     # 下载得到文件link_visual_ipc_ubuntu_1.2.2.tar.gz
     # 解压缩文件，并进入解压后的文件夹
     $ tar -xf link_visual_ipc_ubuntu_1.2.2.tar.gz
     $ cd link_visual_ipc_ubuntu_1.2.2
     # 确认文件内容
     $ ls
     aac_h265_640
     aac_h265_640.index
     aac_h265_640.meta
     aac_h265_768
     aac_h265_768.index
     aac_h265_768.meta
     link_visual_demo
     # 传入设备的激活凭证信息，并运行
     $ ./link_visual_demo -p your_product_name -n your_device_name -s your_device_secret
     ```

   - Docker的Link Visual Demo

      

     ```shell
     # 下载得到文件link_visual_ipc_docker_1.2.2.tar.gz
     # 导入docker镜像
     $ docker load -i link_visual_ipc_docker_1.2.2.tar.gz
     Loaded image: ubuntu:lv_1.2.2
     # 运行镜像，此时会进入到镜像生成的容器中
     $ docker run -it --rm ubuntu:lv_1.2.2 bash
     # 进入link_visual目录
     $ cd /link_visual
     # 解压缩内容并进入
     $ tar -xf sample.tar.gz
     $ cd sample
     # 确认文件内容
     $ ls
     aac_h265_640
     aac_h265_640.index
     aac_h265_640.meta
     aac_h265_768
     aac_h265_768.index
     aac_h265_768.meta
     link_visual_demo
     # 传入设备的激活凭证信息，并运行
     $ ./link_visual_demo -p your_product_name -n your_device_name -s your_device_secret
     ```

   **说明**

   命令中的your_productname、your_devicename、your_devicesecret，需要替换为您的设备激活凭证信息 。请参见[测试设备激活凭证](https://help.aliyun.com/document_detail/142144.html#task-2326463)。

3. 查看Link Visual Demo运行效果。

   - App上触发直播、点播等功能，观看App的播放情况。
   - App触发功能时，在运行Link Visual Demo的Docker或Ubuntu内查看设备实时日志。

## 使用公版App体验Link Visual

1. 扫描生成的[配网+App下载二维码图](https://help.aliyun.com/document_detail/151918.html?source=5176.11533457&userCode=ywqc0ubl)，下载公版App（云智能）。更多公版App的下载方式请参见[公版App介绍https://help.aliyun.com/document_detail/143848.html#task-2338021。](https://help.aliyun.com/document_detail/143848.html#task-2338021?source=5176.11533457&userCode=ywqc0ubl)

2. 使用下载的公版App（云智能），扫描生成的[配网+App下载的二维码](https://help.aliyun.com/document_detail/151918.html?source=5176.11533457&userCode=ywqc0ubl)，绑定虚拟设备。

   虚拟设备绑定后，您就可以体验Link Visual的能力了。

   从公版App（云智能）设备列表进入到对应的摄像头设备后，您将看到如下界面（依次为直播、设置、图库和本地录像播放的界面）。

   ![云智能摄像头界面](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401261758074.png)

   当前公版App中摄像头产品包含以下功能。

   | 功能           | 描述                                                         |
   | :------------- | :----------------------------------------------------------- |
   | 摄像头设置     | 包含摄像头日夜模式、视频画面翻转、报警开关（设备报警的总开关，当触发报警时设备将上传一张报警照片到云端，用户可以在图库中进行查看）、移动侦测灵敏度设置、报警频率设置（控制摄像头上报报警事件的频率）、报警时段设置（摄像头在哪些时段进行报警）、存储卡状态、容量展示和格式化存储卡（格式化掉摄像头内存储卡上的所有文件）等。 |
   | 直播清晰度切换 | 根据您设备支持的种类进行清晰度切换。                         |
   | 直播声音开关   | 该开关只控制手机上直播的音量，并不影响摄像头采集声音。       |
   | 直播录屏       | 从当前直播流上截取，您可以根据需求直播录屏（录制一段时间的直播录像），产生的文件可以在手机相册内查看。 |
   | 直播截图       | 从当前直播流上截取，您可以根据需求直播截图（获取当前直播画面的图片），产生的文件可以在手机相册内查看。 |
   | 语音对讲       | 您可以通过这个功能跟摄像头方人员进行语音聊天。               |
   | 摄像头转动控制 | 通过直播页面的转向盘，控制摄像头进行上下左右转动，由此您可以看到需要的直播画面。 |
   | 图库           | 内展示的设备报警产生的报警图片（具体的上报开关，灵敏度，频率以及时段在设置中“报警设置”中设置）。 |
   | 卡录像         | 展示了一定时间内的摄像头内存储卡保存的历史录像，您可以看到任意时段设备保存的卡录像 |
   | 云端录像       | 查看由设备端产生报警而生成并上传到云端的录像。               |
