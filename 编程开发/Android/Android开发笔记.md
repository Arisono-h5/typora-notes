#  Android开发笔记



[TOC]

## 基础知识

### Java



- [Java 运算符（操作符）&、&&、|、||、^、＜＜](https://blog.csdn.net/dd_Mr/article/details/123969634)
- [System.arraycopy()方法使用](https://blog.csdn.net/liuqinhou/article/details/127272556)



### kotlin



### C/C++



- [C语言指针变量的定义和使用（精华）](http://c.biancheng.net/view/1991.html)
- [C语言指针知识点（一）：字符指针（char *）及其格式输出（%c%d%s等）](https://blog.csdn.net/Lemon_jay/article/details/82917000)



### Android

#### 干货笔记

- [Android干货笔记](http://lastwarmth.win/something/) 
- [Android基础知识库](https://docs.qq.com/doc/DSWdKRWh1VnVHYWFP)
- https://github.com/OCNYang/ConstraintLayout_Guide   全面讲解 ConstraintLayout 相关知识，目前最强大的布局控件，没有之一，不接受反驳。
- https://github.com/OCNYang/Flutter-Notes  收集学习 Flutter 不错的教程。
- https://blog.csdn.net/u010126792/article/details/85238050   Android 绘图学习 《系列教程》

#### 帮助手册

- [Glide v4 学习手册](https://muyangmin.github.io/glide-docs-cn/doc/transitions.html)

#### 报错记录

> 经典错误：Channel is unrecoverably broken and will be disposed!

- [Android报错：Channel is unrecoverably broken and will be disposed!]()
-  InputDispatcher          E  channel '90b1479 com.htl.app/com.htl.app.module.video.LiveVideoActivity (server)' ~ Channel is unrecoverably broken and will be disposed!   产生这个错误的原因很多。（内存泄漏+new对象太多+后台进程显示对话框）
-  channel '8990903 com.htl.app/com.htl.app.module.home.MainActivity (server)' ~ Channel is unrecoverably broken and will be disposed!

- [Channel is unrecoverably broken and will be disposed!](https://blog.csdn.net/bai936780514/article/details/79804274)  部分手机不打印全错误，比如小米，换手机调试！

- java_vm_ext.cc:577] JNI DETECTED ERROR IN APPLICATION: JNI SetByteArrayRegion called with pending exception java.lang.OutOfMemoryError: Failed to allocate a 11328 byte allocation with 2480 free bytes and 2296B until OOM, target footprint 268435456, growth limit 268435456

-  [Android NDK开发崩溃 signal 11 (SIGSEGV), code 1 (SEGV_MAPERR),解决方法](https://www.cnblogs.com/rocket-ban/p/14717425.html)



#### 开发问题

- android activity FLAG_ACTIVITY_CLEAR_TASK 跳转出现短暂的白屏或黑屏现象
- [解决 android 应用被强杀或应用被回收导致的空指针问题](https://juejin.cn/post/6844903450015186958)
-  [Android NDK ANR问题分析处理](https://www.jianshu.com/p/03d9fbb5268b)
-  [Android 使用shape实现虚线或者虚线框](https://blog.csdn.net/kongTy/article/details/82461972)
-   [android APP闪退后如何屏蔽自启动](https://blog.csdn.net/wllovar/article/details/107692139)  统计闪退日志
-   [Android中打开多个Activity，点击返回到第一个Activity](https://blog.csdn.net/qq_35091074/article/details/120014013)
-   [返回上一层activity的实现方式(拓展：不同activity间的任意跳转)](https://blog.csdn.net/dsa63/article/details/17010887)
-   [Android MulticastSocket 组播](https://www.jianshu.com/p/28eff2448a76)
-   [Android上UDP组播无法接收数据的问题](https://www.cnblogs.com/Ralap/p/Android_udp_multcast_solution.html)
-   [android 中获取所有有效网卡和对应的IP地址](https://blog.csdn.net/croop520/article/details/82380963)
-   [自学Android开发 Fragment的onActivityCreated()被弃用](https://blog.csdn.net/Ym_quiet/article/details/121345411)

> 辅助问题

- [Vivo手机调试 logcat 信息一堆星号问题](https://blog.csdn.net/qq910689331/article/details/119729298)

> 奇怪问题(神奇BUG)

-  [App点击Home键后，再次点击APP图标，APP重启回不到点击home键前的那个界面](https://blog.csdn.net/lpCrazyBoy/article/details/103928077)  
- [（完美解决）App点击Home键后，再次点击APP图标，APP重启回不到点击home键前的那个界面](https://blog.csdn.net/qq_38363506/article/details/101608622)
-  [Android开发遇到的坑-----App首次安装,退后台再返回前台时重新显示Splash页面](https://www.cnblogs.com/sweep/p/10468630.html)



#### 知识笔记



>  分区存储

- [Android存储之分区存储适配](https://blog.csdn.net/unreliable_narrator/article/details/127250034)



#### 每日一问

- [为什么 Activity.finish() 之后 10s 才 onDestroy ？](https://juejin.cn/post/6898588053451833351)
- 为什么不能使用 Application Context 显示 Dialog？
- OutOfMemoryError 可以被 try catch 吗 ？



##  高级进阶



###  JNI





#### JNI基础

> 要点：
>
> JNI静态注册和动态注册。
>
> Java调用C和C调用Java方法。
>
> JNI如何处理崩溃异常

- [Android NDK 从入门到精通（汇总篇）](https://blog.csdn.net/afei__/article/details/81290711)

- [unsigned char* 和 byte[] 互转](https://blog.csdn.net/zqx1205/article/details/97750260)

- [Android JNI 篇 - JNI回调的三种方法（精华篇）](https://www.jianshu.com/p/e576c7e1c403)

- [Android JNI和NDK学习(五)：JNI调用数组](https://juejin.cn/post/6844904183183736840)

- [JNI创建Java对象](https://juejin.cn/post/6934888365506428942)

- [NDK(二)：JNI与Java回调以及静动态注册](http://guidongyuan.cn/2018/09/15/NDK(%E4%BA%8C)%EF%BC%9AJNI%E4%B8%8EJava%E5%9B%9E%E8%B0%83%E4%BB%A5%E5%8F%8A%E9%9D%99%E5%8A%A8%E6%80%81%E6%B3%A8%E5%86%8C/)

- [FindClass android jni找不到对象](https://developer.android.com/training/articles/perf-jni?hl=zh-cn#faq_FindClass)  [参考文献](https://blog.csdn.net/chiduokui9989/article/details/100852397)

- [android jni 调用java类方法和成员变量](https://blog.csdn.net/zhangpengzp/article/details/89398772)

- [JNI内形参从C代码中获取返回值并返回到Java层使用](https://developer.aliyun.com/article/1112256)

- [JNI操作字符串](https://blog.csdn.net/Night_ZW/article/details/54342852)

- [JNI C语言jstring和char* 相互转换](https://www.jianshu.com/p/b78f39d36d78)

- [【NDK】【022】JNI DETECTED ERROR IN APPLICATION: use of deleted local reference](https://blog.csdn.net/u013718730/article/details/118436593)

- 

  

  

  

#### cmake

- [cmake-examples](https://github.com/ttroy50/cmake-examples)  +[文档教程](https://sfumecjf.github.io/cmake-examples-Chinese)  CMake详细教程

-  [CMake 入门实战](https://www.hahack.com/codes/cmake/)
- [NDK(三)：静态库和动态库](http://guidongyuan.cn/2018/09/25/NDK%28%E4%B8%89%29%EF%BC%9A%E9%9D%99%E6%80%81%E5%BA%93%E5%92%8C%E5%8A%A8%E6%80%81%E5%BA%93/)
- [android studio cmake生成.a文件(静态库)及调用(c c++)静态库.a](https://blog.csdn.net/qingfeng812/article/details/132674778)
- [Android jni引用第三方so动态库和.a静态库并且调用(c)方法](https://blog.csdn.net/qingfeng812/article/details/132688988?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132688988%22%2C%22source%22%3A%22qingfeng812%22%7D)
- [CMake添加外部动态/静态库到本地工程](https://zhuanlan.zhihu.com/p/544340082)





### 音视频

#### 资料汇总



#### 基础知识

-  [H.264/H265码流解析](https://www.cnblogs.com/wujianming-110117/p/12722286.html)
- [H264/265码流数据包格式分析](H264/265码流数据包格式分析)
- [Android MediaCodec编码后解析出H264/H265中vps sps pps帧](https://blog.csdn.net/zhichi202/article/details/105920432)

> 每帧PCM数据大小：**PCM Buffersize=采样率\*采样时间\*采样位数/8\*通道数（Bytes）**

- [关于音频帧率与采样率](https://www.suninf.net/2023/01/audio-framerate-and-sample.html)
- [libfdk_aac编码AAC](https://blog.csdn.net/u010140427/article/details/127765173)
- [采样个数(样本数)的概念及计算一帧音频的大小](https://blog.csdn.net/weixin_44517656/article/details/117849297)  音频通道数、采样率、采样个数(样本数)、采样位数的概念和计算一帧音频的大小、每秒播放的音频字节大小、一帧音频的播放时长
- [FFmpeg 音频编码](https://octalzero.com/article/88a0d789-5f79-46d9-8706-2c5f063a5157)
- [FFmpeg 解封装 MP4 媒体文件](https://octalzero.com/article/91b62969-d088-46e3-a500-b6b8a3e5278f)

- [Android音视频开发基础（五）：学习MediaCodec API，完成音频AAC硬编、硬解](https://juejin.cn/post/7067478839152246820)
- [android MediaCodec dequeueInputBuffer IllegalStateException](https://blog.51cto.com/u_16213403/7156563)    《经典问题，必须搞明白》



> AAC的音频文件格式有ADIF和ADTS：
>
> - ADIF：Audio Data Interchange Format 音频数据交换格式。这种格式的特征是可以确定的找到这个音频数据的开始，不需进行在音频数据流中间开始的解码，即它的解码必须在明确定义的开始处进行。故这种格式常用在磁盘文件中。
> - ADTS：Audio Data Transport Stream 音频数据传输流。这种格式的特征是它是一个有同步字的比特流，解码可以在这个流中任何位置开始。它的特征类似于mp3数据流格式。
>
> 简单来说，ADIF只有一个统一的头，所以必须得到所有的数据后解码，ADTS每一帧都有头信息，可以从任意帧开始解码，因此网络上的aac基本都是ADTS格式。



#### 视频流播放

> 主要是H264,H265格式的硬解码和软解码播放。特别注意高清分辨率下的，软解码播放问题。
>
> 硬解码用系统解码器，软解码用FFmpeg

- [安卓硬解码性能问题](https://github.com/Bilibili/ijkplayer/issues/1954) 



#### 监听与对讲

> Android 

- G711u转PCM  https://github.com/theeasiestway/android-g711-codec

- 音视频核心功能（录制视频）H264+aac或H265+aac录制mp4视频。

- Android MediaCodec编码后解析出H264/H265中vps sps pps帧  https://blog.csdn.net/zhichi202/article/details/105920432

  

#### 录制MP4

>  Android 音视频开发(五)：使用 MediaExtractor 和 MediaMuxer API 解析和封装 mp4 文件(硬解码的方式)
>
>  使用MP4v2将H264/H265码流以及AAC音频封装成MP4格式(软解码的方式)
>
>  使用FFmpeg将H264/H265码流以及AAC音频封装成MP4格式(软解码的方式)

- [YUV 格式详解，只看这一篇就够了（转）](https://zhuanlan.zhihu.com/p/384455058?utm_id=0)
- [Camera 仿微信相机 利用MediaCodec API 从录制MP4到解析播放](https://blog.csdn.net/qq_15893929/article/details/82706755)
- https://github.com/renhui/AndroidRecorder  音视频录制流程总结
- [利用MP4v2和MediaMuxer类去合成MP4文件](https://github.com/chezi008/mp4muxer)
- https://github.com/ChyengJason/SCamera (仿微信录像拍照)
- [＜整理总结＞H264/265码流数据包格式分析（带mp4v2封装H264/265为MP4的源码示例）](https://blog.csdn.net/n_i_n/article/details/114140581?spm=1001.2014.3001.5502)  **【精选文章】**
- https://github.com/Pandalzm/mp4v2-h265  mp4v2-h265   
- https://github.com/farrellpeng/mp4v2-h265/    mp4v2-h265
- https://github.com/TechSmith/mp4v2  
- [MP4V2 封装h265到MP4文件 及解包MP4](https://blog.csdn.net/manyanhua/article/details/112026968)
- [MediaMuxer编码h264流文件](https://www.cnblogs.com/lsy-2016/p/7374453.html)  获取sps+pps



使用MediaMuxer 合成mp4遇到的问题：

> "csd-0" 和 "csd-1" 是什么，对于 H264 视频的话，它对应的是 sps 和 pps，对于 AAC 音频的话，对应的是 ADTS，做音视频开发的人应该都知道，它一般存在于编码器生成的 IDR 帧之中。
>
> 创建并配置 codec。配置 codec 时，若手动创建 MediaFormat 对象的话，一定要记得设置 "csd-0" 和 "csd-1" 这两个参数。 "csd-0" 和 "csd-1" 这两个参数一定要和接收到的帧对应上。
>
> **offset：**表示缓冲区中有效数据的偏移量，通常为0；
> **size：**表示当前解码出来的视频帧数据大小，可以用于计算码率等相关指标。
> **presentationTimeUs：**表示当前解码出来的视频帧的展示时间戳，单位是微秒。通过该参数可以帮助我们在渲染视频帧时控制视频的播放速度和时序。
> **flags：**表示当前解码出来的视频帧的标志位，例如是否为关键帧、是否包含SEI信息等。flags包含如下取值：

- [E  Dumping Video track's last 10 frames' timestamps(pts, dts) and frame type :](https://stackoverflow.com/questions/60898170/mix-auido-to-video-when-stop-mediamuxer-get-a-issue)

> aac播放没有声音
>
> 平时如果你遇到了编码AAC裸流的时候，很有可能会出现写出来的AAC文件不能在PC端和手机上进行正常播放，这时候**可能的原因是你的AAC文件中的每一帧里面缺少了ADTS头信息文件的包装拼接**。 解决方法：只需要加⼊头⽂件ADTS即可。



#### 视频截图

> 这个比较简单，直接截控件的。



#### 回音消除





#### P2P直连

- [P2P中的NAT穿越(打洞)方案详解](https://www.cnblogs.com/xiugeng/p/12029388.html)



### FFmpeg

#### FFmpeg编译

> Linux和Mac系统编译FFmpeg相对简单一些，Window上编译需要借助额外的工具，麻烦点。
>
> 

- Android studio 编译FFmpeg5.1.3 
- [FFmpeg5.1 版本编译好的库—FFmpegDemo](https://github.com/Dragonxwl/FFmpegDemo)   如果你不想自己编译，就可以直接去拿编译好的动态库。
- [FFmpeg4.x版本编译好的库](https://github.com/Grechur/ffmpeg4.0.1-for-android) 如果你不想自己编译，就可以直接去拿编译好的动态库。
- [FFmpeg编译出来的库太大？试试这几招](https://blog.csdn.net/qq_29536949/article/details/108668847)
- [window 10 下安装 Ubuntu 22.04 使用 NDK r24 编译FFmpeg 5.1](https://www.jianshu.com/p/487f0e6d0e30)
- [Android 音视频FFmpeg5.1.1编译](https://blog.csdn.net/qq_35193677/article/details/126995780)
- [FFmpeg编译无坑版（Windows篇）](https://www.jianshu.com/p/53ecc4dbe7d0)
- [Linux NDK编译FFmpeg5.x](https://blog.csdn.net/qq_38502914/article/details/128134383)  简单易懂

> Window安装Linux虚拟机

-  [在VMware中安装CentOS7（超详细的图文教程）](https://www.cnblogs.com/tanghaorong/p/13210794.html)
- [Window安装虚拟机---VMware Workstation PRO 17.0.2正式版+激活密钥](https://www.isharepc.com/36181.html)
- Centos系统镜像地址：http://archive.kernel.org/centos-vault/7.8.2003/isos/x86_64/
- Centos系统镜像地址汇总：http://isoredirect.centos.org/centos/7/isos/x86_64/

> 提示：安装虚拟机的时候，报错“  this hardware is not supported by centos”     boss界面需要开启虚拟化技术开关+Centos更新到新版

-  [VMware安装Linux:hardware is not supported](https://blog.csdn.net/leer_/article/details/105229765)
- [VM安装系统时提示硬件不支持(unsupported hardware detected)](https://blog.51cto.com/u_14590988/3150723)

> FFmpeg编译裁剪

- [偶遇FFmpeg(番外)——FFmpeg花样编译入魔1之裁剪大小](https://cloud.tencent.com/developer/article/1358834)
- [FFmpeg – ./configure编译参数全部总结和整理](https://www.stubbornhuang.com/2053/)



#### FFmpeg入门

> 体系教程

- [ffmpeg_develop_doc](https://github.com/0voice/ffmpeg_develop_doc)   2023年，最新音视频学习资料整理，项目（调试可用），ffmpeg命令手册，文章，编解码论文，视频讲解，面试题全套资料

> 文献笔记

- [FFmpeg原理介绍](https://ffmpeg.xianwaizhiyin.net/)

- [FFmpeg 8个功能模块](https://www.jianshu.com/p/cb1b88d83bb9)

- [FFmpeg5开发入门系列索引_](https://feater.top/ffmpeg/ffmpeg-learning-indexes)

- [window10环境 android studio集成ffmpeg5.1 NDK r24](https://www.jianshu.com/p/da6049a1140a)

- [【音视频开发系列】fdk_aac 之 PCM 转 AAC](https://blog.csdn.net/weixin_44328568/article/details/125415360)

- [FFmpeg简单使用：音频编码 ---- pcm转aac](https://www.cnblogs.com/vczf/p/13599573.html)

- [AAC 音频编码格式分析](https://octalzero.com/article/ae661974-5f1a-4352-9ae6-38022679a90d)



### 自定义View

#### 案例

- https://github.com/385841539/HorizontalScrollSelectedView   横向滚动的，可以支持大量文本选择的 自定义View ，一行代码 ， 简单易用 ， 无OOM情况
- https://github.com/AnliaLee/BookPage Android自定义View实现翻页效果，并附带实现教程
- https://github.com/donkingliang/ConsecutiveScroller ConsecutiveScrollerLayout是Android下支持多个滑动布局(RecyclerView、WebView、ScrollView等)和普通控件(TextView、ImageView、LinearLayou、自定义View等)持续连贯滑动的容器,它使所有的子View像一个整体一样连续顺畅滑动。并且支持布局吸顶功能。
- https://github.com/chezi008/VideoSurveillance 视频监控，四宫格视图。双击放大，视频无缝衔接
- https://blog.csdn.net/yan13507001470/article/details/116530740 自定义viewGroup，动态增/删子view，及四/九宫格排版
- https://www.jb51.net/article/269729.htm Android自定义ViewGroup实现九宫格布局

#### 教程

> 刘望舒自定义View系列

-  [Android View体系（一）视图坐标系](https://blog.csdn.net/itachi85/article/details/50708391)   [个人博客](https://liuwangshu.cn/application/view/1-coordinate-system.html)
-  https://blog.csdn.net/u010126792/article/details/85238050   Android 绘图学习

> 开源系列

-  https://github.com/xinghongfei/awesome-view



## 架构设计



### 架构方案

#### MVP架构

> 使用 MVP 时，如何让同一个 P 服务多个 V？

- [使用 MVP 时，如何让同一个 P 服务多个 V？](https://github.com/android-cn/android-discuss/issues/468)
- [关于 MVP 模式的一点思考](http://lastwarmth.win/2017/04/25/mvp-1/)
- [Android学习之MVP模式](http://www.xsong.wang/2020/04/12/Android%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0%E4%B9%8BMVP%E6%9E%B6%E6%9E%84/#mvp-%E4%B8%8E-activityfragment-%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
- [android：MVP架构模式的优雅封装](https://www.jianshu.com/p/4e5c1fd007bf)  P层需要弱引用持有View层中的对象
- [带你动手实现 MVP+Clean架构！](https://juejin.cn/post/6844903667456294919) + [源码](https://github.com/JD-CP/MVP-Clean-Demo)

> 源码参考：

- https://github.com/iceCola7/MVPSamples  （Java 版）快速搭建 MVP + RxJava + Retrofit + EventBus 的框架，方便快速开发新项目、减少开发成本。



#### MVVM架构

- https://github.com/jenly1314/MVVMFrame   MVVMFrame for Android 是一个基于Google官方推出的Architecture Components dependencies（现在叫JetPack）{ Lifecycle，LiveData，ViewModel，Room } 构建的快速开发框架。有了MVVMFrame的加持，从此构建一个MVVM模式的项目变得快捷简单。



#### MVI架构

-  MVVM 进阶版：MVI 架构了解一下~  https://juejin.cn/post/7022624191723601928

#### 传统架构

> Java+RxJava+Okhttp+Retrofit+MVP
>
> kotlin+RxJava+Okhttp+Retrofit+MVP

   参考文献：

-  [Android MVP架构从入门到精通-真枪实弹](https://juejin.cn/post/6844903720036073480) +[github源码](https://github.com/serge66/MVPDemo)  Android MVP架构Demo--Android MVP架构从入门到精通-真枪实弹

> Java+RxJava+Okhttp+Retrofit+MVVM



#### 组件化架构

- Java+RxJava+Okhttp+Retrofit+MVP+组件化
- kotlin+RxJava+Okhttp+Retrofit+MVP+组件化

#### 跨平台架构







### 基础组件

#### 网络

> Retrofit2+OKhttp3+Rxjava2

要求点：

1. 基本的使用：get,post,post body,上传,下载

2. 公共请求头和请求参数。

3. 设置请求tag，并支持取消和全部取消。防止内存泄漏。
4. 打印日志
5. 支持缓存
6. 支持Cookie
7. 支持自定义服务器异常

- [RxEasyHttp](https://github.com/zhou-you/RxEasyHttp)  成熟的封装库 
- [Rx-Mvp](https://github.com/RuffianZhong/Rx-Mvp)  小众封装库，可以借鉴
- [封装一个属于自己的 RxJava、RxAndroid + Retrofit 网络框架](https://blog.csdn.net/qq_20451879/article/details/121657373)
- [Retrofit + OkHttp +RxJava 网络库构建及项目实践（上篇）](https://sq.sf.163.com/blog/article/176154140014993408) 自定义服务器异常
- [Retrofit + OkHttp +RxJava 网络库构建及项目实践（下篇）](https://sq.sf.163.com/blog/article/176154649350082560)
- [Rxjava2Retrofit2NetFrame](https://github.com/bigeyechou/Rxjava2Retrofit2NetFrame)  基于Retrofit+Rxjava+Okhttp的网络请求框架
- [RxJavaRetrofitOkhttpMvp](https://github.com/gslovemy/RxJavaRetrofitOkhttpMvp) RxJava+Retrofit+okhttp+mvp,现在流行这一套框架的封装,想着想着就自己封装了一套,并-且我们的项目的里面也这样用,方便以后的功能的迭代开发,产品需求的更改,有什么不足的地方,
- [【Android】RxJava+Retrofit+OkHttp的基础、封装和项目中的使用](https://juejin.cn/post/6844903772976578573)
- https://github.com/kongpf8848/RxHttp  基于RxJava2+Retrofit+OkHttp4.x封装的网络请求类库，亮点多多，完美兼容MVVM(ViewModel,LiveData),天生支持网络请求和生命周期绑定，天生支持多BaseUrl，支持文件上传下载进度监听，支持断点下载，支持Glide和网络请求公用一个OkHttpClient

>  Rxjava2

-  [RxJava 2.x 使用详解(一) 快速入门](https://maxwell-nc.github.io/android/rxjava2-1.html)

> socket websocket netty

- https://github.com/jenly1314/ANetty      ANetty 是基于Netty二次封装的Android链路通讯库，用以快速开发高性能，高可靠性的网络交互。在保证易于开发的同时还保证其应用的性能，稳定性和伸缩性。轻松实现长连接通讯。
- https://github.com/yetel/EasyChatAndroidClient  EasyChat是一个开源的社交类的App。主要包含消息、好友、群组等相关的IM核心功能。部分界面参照了QQ、微信等相关社交APP。EasyChat APP整体采用MVVM模式，基于JetPack(Lifecycle，LiveData，ViewModel，Room)构建
- https://github.com/jenly1314/ASocket ASocket 是一个TCP/UDP协议的封装库，方便快速实现TCP的长连接与UDP的单播、组播、广播等相关通信
- https://github.com/jenly1314/AWebSocket  AWebSocket一个基于okhttp封装的WebSocket，简洁易用。

#### 总线

方案

> EventBus 或 RxBus+RxLife

- https://github.com/Z-P-J/RxLife-AndroidX + [轻量级的RxJava生命周期管理库](https://github.com/Z-P-J/RxLife-AndroidX#轻量级的rxjava生命周期管理库)  [最近想找一个好用的RxJava生命周期管理库，找到一些比较好的开源项目，比如 ](https://github.com/Z-P-J/RxLife-AndroidX#最近想找一个好用的rxjava生命周期管理库找到一些比较好的开源项目比如-trellorxlifecycle--dhhandroidrxlife-liujingxingrxjava-rxlife-以及genius158rxlifehelpertrellorxlifecycle和dhhandroidrxlife貌似不支持监听view的生命周期liujingxingrxjava-rxlife库虽支持监听view-但是在使用过程中不能返回原类型的observable对象而genius158rxlifehelper是一个不错的库不仅支持监听view还拓展了根据tag管理生命周期和livedata但是该库是基于androidx的目前我所做的项目基本上是使用support库的项目所以fork了genius158rxlifehelper项目并对代码进行了修改和简化)[trello/RxLifecycle](https://github.com/trello/RxLifecycle) ， [dhhAndroid/RxLife](https://github.com/dhhAndroid/RxLife) ，[liujingxing/rxjava-RxLife](https://github.com/liujingxing/rxjava-RxLife) 以及[genius158/RxLifeHelper](https://github.com/genius158/RxLifeHelper)。trello/RxLifecycle和dhhAndroid/RxLife貌似不支持监听View的生命周期；liujingxing/rxjava-RxLife库虽支持监听View, 但是在使用过程中不能返回原类型的Observable对象；而genius158/RxLifeHelper是一个不错的库，不仅支持监听View，还拓展了根据Tag管理生命周期和LiveData，但是该库是基于androidx的，目前我所做的项目基本上是使用support库的项目，所以fork了genius158/RxLifeHelper项目并对代码进行了修改和简化。
- https://github.com/Z-P-J/RxBus  Event Bus By RxJava. 使用RxJava实现的事件发布/订阅框架，替代EventBus，支持Sticky Event,支持生命周期管理。

#### 图片

> Gilde

- [RecycleView或ListView 中使用glide加载图片如何防止加载错乱](https://cloud.tencent.com/developer/article/1931699)
- [Glide在禁用缓存功能时，刷新列表会闪一下](https://www.jianshu.com/p/572767d2a64a)
- [处理Glide刷新出现闪烁](https://blog.csdn.net/wbw522/article/details/71195249)
- [Glide加载相同URL时由于缓存无法更新图片的问题](https://blog.csdn.net/QasimCyrus/article/details/76408338)
- [Glide 加载相同路径图片不更新问题](https://juejin.cn/post/7019529323455447071)
- [Android 加载图片占用内存分析](https://juejin.cn/post/6865492162445606925)
- [Canvas: trying to draw too large bitmap 问题](https://okhcy.com/23.html)
- [Glide4.x使用总结](https://www.linz.tech/2020/12/16/2020-12-8-glide%E5%A4%8D%E4%B9%A0/)
- [使用glide加载未知尺寸图片导致OOM问题的解决方案](https://blog.csdn.net/Crab0314/article/details/85102422)
- [android glide加载本地图片不显示 glide加载大图片防止oom](https://blog.51cto.com/u_16213566/7174819)

#### 日志

- xlog

#### 存储

#### 权限



#### 动画

- https://github.com/kongpf8848/Animation  Android各种动画效果合集，项目包含了丰富的动画实例(逐帧动画，补间动画，Lottie动画，GIF动画，SVGA动画)，体验动画之美，让Android动起来
- https://github.com/REBOOTERS/AndroidAnimationExercise  Android 动画各种实现，包括帧动画、补间动画和属性动画的总结分享
- https://github.com/OCNYang/Android-Animation-Set  Android 所有动画系列详尽教程。 Explain all animations in Android.



### 业务组件

#### 埋点

#### 统计

- https://github.com/zhengcx/MethodTraceMan 用于快速找到高耗时方法，定位解决Android App卡顿问题。通过gradle plugin+ASM实现可配置范围的方法插桩来统计所有方法的耗时，并提供友好的界面展示，支持耗时筛选、线程筛选、方法名筛选等。(A Tool for Discovering High Time-consuming Methods for Android App)

#### 扫码

> zxing库需要进行优化，不想折腾直接用华为的统一扫码服务

- https://developer.huawei.com/consumer/cn/doc/HMSCore-Guides/android-customized-view-0000001050042012      华为的统一扫码服务。

- https://github.com/yuzhiqiang1993/zxing zxing 二维码扫码和生成。基于zxing的扫一扫，优化了扫描二维码速度，集成最新版本的jar包（zxing-core.jar 3.3.3），集成简单，速度快，可配置颜色，还有闪光灯，解析二维码图片，生成二维码等功能
- https://github.com/ailiwean/NBZxing   这个扫码识别率还可以。速度也行。
- https://github.com/jenly1314/ZXingLite  ZXing的精简极速版，优化扫码和生成二维码/条形码，内置闪光灯等功能。扫描风格支持：微信的线条样式，支付宝的网格样式。几句代码轻松拥有扫码功能 ，ZXingLite让集成更简单。（扫码识别速度快如微信）
- https://github.com/jenly1314/ViewfinderView  ViewfinderView 是一个取景视图：主要用于渲染扫描相关的动画效果。其样式主要分为两大类：classic：经典样式（带扫描框）、popular：流行样式（不带扫描框）；可任意定制。

#### 支付

- https://github.com/jenly1314/AppPay  AppPay专注于App支付的库，几句代码轻松搞定微信支付、支付宝支付、银联支付。集成更简单。

### UI组件



#### 布局

> 底部导航栏

- [Android通过RadioGroup+Fragment实现底部导航及切换](https://blog.csdn.net/FRYAN28/article/details/101367478) 

> 基础知识

-  [Fragment的生命周期以及onActivityCreated()被弃用](https://blog.csdn.net/Ym_quiet/article/details/121345411)



#### 列表

> 基础列表

- [GirdView网格列表的使用](https://www.jianshu.com/p/68bf875214d6)

  

> 刷新组件

- [Android几种强大的下拉刷新库](https://zhuanlan.zhihu.com/p/36334257)
- https://github.com/chrisbanes/Android-PullToRefresh
- https://github.com/WenkaiZhou/Android-PullToRefresh  扩展了控件RecyclerView ViewPager
- [Android PullToRefresh 分析之五、扩展刷新加载样式](https://blog.csdn.net/xuehuayous/article/details/50394640)  

> 悬浮分组列表

- [RecyclerView实现收缩分组悬浮列表](https://blog.csdn.net/wuyuxing24/article/details/80021069)

> 组合列表

- https://github.com/385841539/RecycleviewStaggered  recycleview进阶用法，实现复杂页面，包含瀑布流，同时解决复杂布局嵌套卡顿，内存泄漏情况

#### 日历

- https://github.com/huanghaibin-dev/CalendarView  这款日历控件很强大，定制性强  [教程文献](https://juejin.cn/post/6844903554688221191)
- https://github.com/maning0303/MNCalendar [暂停维护] 简单的日历控件，水平方向日历支持手势滑动切换，跳转月份；垂直方向日历选取区间范围。

#### 自定义View

要点：

1.自定义可滚动的四分屏播放控件，支持32路或者不限制。  安防app需要用到。(复杂)

2.自定义时间轴控件，云录像和SD录像需要用到。(复杂)

##### 移动缩放

- https://github.com/natario1/ZoomLayout
- https://github.com/guangmomo/ZoomLayout
-  [android-view-实现双指平移、缩放、旋转](https://juejin.cn/post/6844904162744860685)

##### Banner



- https://github.com/OCNYang/PageTransformerHelp



##### 短信验证码



- https://github.com/kongpf8848/ViewWorld



#### 加载框

- https://github.com/maning0303/MNProgressHUD
- https://github.com/Kaopiz/KProgressHUD/tree/master  采用



#### 进度条

- https://github.com/Ccapton/Collection-Android-Progress 进度条大全 安卓自定义Progressbar控件汇总



#### 对话框

#### Toast



#### PopupWindow



- [Android PopupWindow下拉筛选局部阴影效果](https://blog.csdn.net/qq_24293111/article/details/81020637)



#### WebView

#### 选项卡

- https://github.com/H07000223/FlycoTabLayout   An Android TabLayout Lib

#### 输入框

#### 按钮



#### StepView

- https://github.com/baoyachi/StepView
- https://github.com/shuhart/StepView
- https://github.com/zhangxuyang321/StepView   流程步骤指示器 stepview
- https://github.com/params-ing/StepViewAndroid 
- https://github.com/sorgs/StepView
- https://github.com/dcq123/StepView
- https://github.com/chencanlin/StepView







#### 其它

- https://github.com/RuffianZhong/RWidgetHelper  Android UI 快速开发，专治原生控件各种不服
- https://github.com/EHENJOOM/ShadowCardView  自定义阴影颜色的CardView
- https://github.com/donkingliang/RadarView  Android雷达效果自定义View.  Android自定义View 雷达扫描效果。可以根据自己的需求配置View的主题颜色、扫描颜色、扫描速度、圆圈数量、是否显示水滴等。
- https://blog.csdn.net/weixin_39541600/article/details/117588057  android 雷达坐标系,自定义view之雷达搜索扩散圆从无到有




## 开发辅助



### 项目环境



-  [解决Android logcat: Unexpected EOF!方法指南](https://huaweicloud.csdn.net/65095fed993dd34278ee3e50.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MjE4MjExLCJleHAiOjE2OTYzMTgwOTksImlhdCI6MTY5NTcxMzI5OSwidXNlcm5hbWUiOiJxaW5nZmVuZzgxMiJ9.9DJl_9A1KKflSE3nwuQZTDyqZLfYUp0gMf6-c9muRec)







## 性能优化

### 内存泄漏

- [static静态方法中new的对象会被回收吗](https://juejin.cn/s/static%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95%E4%B8%ADnew%E7%9A%84%E5%AF%B9%E8%B1%A1%E4%BC%9A%E8%A2%AB%E5%9B%9E%E6%94%B6%E5%90%97)

### 超时响应

- [BlockCanary — 轻松找出Android App界面卡顿元凶](http://blog.zhaiyifan.cn/2016/01/16/BlockCanaryTransparentPerformanceMonitor/).  [github源码](https://github.com/markzhai/AndroidPerformanceMonitor/blob/master/README_CN.md)
- https://github.com/SalomonBrys/ANR-WatchDog

## 源码解读



## 行业大佬

> 学习它人，更能激励自己。随时了解与大佬们的差距，持续学习



> OCNYang   杭州涂鸦信息技术有限公司

- https://github.com/OCNYang/AndroidBang  《Android 江湖花名册》
- https://github.com/OCNYang/OCNYang/blob/master/resume.md
