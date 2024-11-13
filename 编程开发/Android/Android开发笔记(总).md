#  Android开发笔记(总)



[TOC]

## 基础知识

### Java



- [Java 运算符（操作符）&、&&、|、||、^、＜＜](https://blog.csdn.net/dd_Mr/article/details/123969634)
- [System.arraycopy()方法使用](https://blog.csdn.net/liuqinhou/article/details/127272556)

-   [Java 枚举：switch 支持枚举](https://blog.csdn.net/veryitman/article/details/7947640)

> JSON

- https://blog.csdn.net/weixin_40573757/article/details/80200758 JSON.toJSONString 后都变成了小写





### kotlin

#### 基本语法

-  Kotlin语言基础 https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/Kotlin%E8%AF%AD%E8%A8%80%E5%9F%BA%E7%A1%80

- kotlin面向对象：https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1
- Kotlin函数：https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/%E5%87%BD%E6%95%B0
- Kotlin集合框架：https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/%E9%9B%86%E5%90%88%E6%A1%86%E6%9E%B6

#### 高级语法

- [函数式编程](https://github.com/JackChan1999/Kotlin-Tutorials/blob/master/函数式编程/函数式编程概述.md)  https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BC%96%E7%A8%8B

-  深入理解Kotlin泛型: https://www.geekailab.com/doc/as/book/docs/Part1/Android%E5%BC%80%E5%8F%91%E5%BF%85%E5%A4%87Kotlin%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF/%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3Kotlin%E6%B3%9B%E5%9E%8B.html
- 泛型：in、out、where https://book.kotlincn.net/text/generics.html
- 协程：https://github.com/JackChan1999/Kotlin-Tutorials/tree/master/%E5%8D%8F%E7%A8%8B

#### 设计模式

-   Java 和 Kotlin 单例模式写法对比  https://blog.csdn.net/fesdgasdgasdg/article/details/139886966

#### 架构模式



#### 混合开发

-   [kotlin和java混合开发总结](https://www.jianshu.com/p/9220227cdfb3)


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
- https://blog.csdn.net/wangzhongshun/article/details/105321487 Android 拦截或屏蔽返回键

#### 帮助手册

- [Glide v4 学习手册](https://muyangmin.github.io/glide-docs-cn/doc/transitions.html)

#### 报错记录

> 经典错误：Channel is unrecoverably broken and will be disposed!

- [Android报错：Channel is unrecoverably broken and will be disposed!]()
- InputDispatcher          E  channel '90b1479 com.htl.app/com.htl.app.module.video.LiveVideoActivity (server)' ~ Channel is unrecoverably broken and will be disposed!   产生这个错误的原因很多。（内存泄漏+new对象太多+后台进程显示对话框）
- channel '8990903 com.htl.app/com.htl.app.module.home.MainActivity (server)' ~ Channel is unrecoverably broken and will be disposed!
- [Channel is unrecoverably broken and will be disposed!](https://blog.csdn.net/bai936780514/article/details/79804274)  部分手机不打印全错误，比如小米，换手机调试！
- java_vm_ext.cc:577] JNI DETECTED ERROR IN APPLICATION: JNI SetByteArrayRegion called with pending exception java.lang.OutOfMemoryError: Failed to allocate a 11328 byte allocation with 2480 free bytes and 2296B until OOM, target footprint 268435456, growth limit 268435456
- [Android NDK开发崩溃 signal 11 (SIGSEGV), code 1 (SEGV_MAPERR),解决方法](https://www.cnblogs.com/rocket-ban/p/14717425.html)

> Android系统版本兼容问题报错

-  [终极大法：android:exported needs to be explicitly specified for <xxxxx>. Apps targeting Android 12 and...](https://www.jianshu.com/p/0966c614e51a)   这个问题麻烦点在于，需要解决第三方库中的android exported问题。——Android12 API引发的问题。
- [解决Manifest merger failed : android:exported needs to be explicitly specified for ＜activity＞](https://blog.csdn.net/adojayfan/article/details/123243312)  ——Android12 API引发的问题。
-  [Android编译优化之Jetifier优化](https://blog.csdn.net/SOHU_TECH/article/details/135007860)   android有些第三库或者android老项目，Android X库与Support库混用，导致开启了 “android.enableJetifier=true”。导致编译项目速度变慢了。这个 Jetifier 插件每次编译运行，都会对构建速度产生影响。因此，关闭 Jetifier 有助于加快构建速度。
- https://blog.csdn.net/weixin_37639900/article/details/107488172  ListView 的Adapter刷新数据时出现IndexOutOfBoundsException: Index: 4, Size: 0 数组越界异常问题的解决方案





#### 开发问题

- android activity FLAG_ACTIVITY_CLEAR_TASK 跳转出现短暂的白屏或黑屏现象
- [解决 android 应用被强杀或应用被回收导致的空指针问题](https://juejin.cn/post/6844903450015186958)
- [Android NDK ANR问题分析处理](https://www.jianshu.com/p/03d9fbb5268b)
- [Android 使用shape实现虚线或者虚线框](https://blog.csdn.net/kongTy/article/details/82461972)
- [android APP闪退后如何屏蔽自启动](https://blog.csdn.net/wllovar/article/details/107692139)  统计闪退日志
- [Android中打开多个Activity，点击返回到第一个Activity](https://blog.csdn.net/qq_35091074/article/details/120014013)
- [返回上一层activity的实现方式(拓展：不同activity间的任意跳转)](https://blog.csdn.net/dsa63/article/details/17010887)
- [Android MulticastSocket 组播](https://www.jianshu.com/p/28eff2448a76)
- [Android上UDP组播无法接收数据的问题](https://www.cnblogs.com/Ralap/p/Android_udp_multcast_solution.html)
- [android 中获取所有有效网卡和对应的IP地址](https://blog.csdn.net/croop520/article/details/82380963)
- [自学Android开发 Fragment的onActivityCreated()被弃用](https://blog.csdn.net/Ym_quiet/article/details/121345411)

> 图片加载

- https://blog.csdn.net/u011814346/article/details/99585014  android listview使用glide异步加载图片错位，闪烁问题

> 开发技巧

- [Android开发小技巧-监听和判断应用在前台还是后台的几种方式](https://juejin.cn/post/7111516772141891620)   推荐方式三

> 辅助问题

- [Vivo手机调试 logcat 信息一堆星号问题](https://blog.csdn.net/qq910689331/article/details/119729298)

> 奇怪问题(神奇BUG)

-  [App点击Home键后，再次点击APP图标，APP重启回不到点击home键前的那个界面](https://blog.csdn.net/lpCrazyBoy/article/details/103928077)  
- [（完美解决）App点击Home键后，再次点击APP图标，APP重启回不到点击home键前的那个界面](https://blog.csdn.net/qq_38363506/article/details/101608622)
-  [Android开发遇到的坑-----App首次安装,退后台再返回前台时重新显示Splash页面](https://www.cnblogs.com/sweep/p/10468630.html)

> 自定义View+手势+滚动滑动

-  [Android 手势识别——单击/双击](https://www.cnblogs.com/NeilZhang/p/8149186.html) 
-  [Android自定义View-平移缩放旋转](https://ljd1996.github.io/2021/08/11/Android%E8%87%AA%E5%AE%9A%E4%B9%89View-%E5%B9%B3%E7%A7%BB%E7%BC%A9%E6%94%BE%E6%97%8B%E8%BD%AC/)





#### 知识笔记

> 版本适配

- https://github.com/getActivity/AndroidVersionAdapter 安卓版本适配全套指南

>  分区存储

- [Android存储之分区存储适配](https://blog.csdn.net/unreliable_narrator/article/details/127250034)

> FileProvider

- [Android FileProvider的使用](https://github.com/YoungBear/FileProviderLearn)
- [Android FileProvider 踩坑指北](https://www.cnblogs.com/ioriwellings/p/16198700.html)





#### 每日一问

- [为什么 Activity.finish() 之后 10s 才 onDestroy ？](https://juejin.cn/post/6898588053451833351)
- 为什么不能使用 Application Context 显示 Dialog？
- OutOfMemoryError 可以被 try catch 吗 ？
- [Android----onSaveInstanceState 的数据存在哪里？为什么限制了大小？](https://yishengma.github.io/2019/03/29/Android-onSaveInstanceState-%E7%9A%84%E6%95%B0%E6%8D%AE%E5%AD%98%E5%9C%A8%E5%93%AA%E9%87%8C%EF%BC%9F%E4%B8%BA%E4%BB%80%E4%B9%88%E9%99%90%E5%88%B6%E4%BA%86%E5%A4%A7%E5%B0%8F%EF%BC%9F/)
- [Android----Handler(HandlerA发送的消息HandlerB 能接收吗？)](https://yishengma.github.io/2019/01/01/Android-Handler-HandlerA%E5%8F%91%E9%80%81%E7%9A%84%E6%B6%88%E6%81%AFHandlerB-%E8%83%BD%E6%8E%A5%E6%94%B6%E5%90%97%EF%BC%9F/)







##  高级进阶

### 高频热点

#### 事件分发机制

​            [事件分发机制完整类图+流程图](https://www.processon.com/view/62bc3a77e0b34d075b156c94)

​            [Android | 彻底理解 View 的事件分发机制](https://juejin.cn/post/7067698735874539527)

​            [Android事件分发机制](https://gityuan.com/2015/09/19/android-touch/)

#### 消息处理机制

​            **[精选原创]Android系统Handler详解** https://blog.csdn.net/allen_xu_2012_new/article/details/131146087?spm=1001.2014.3001.5502

#### View绘制流程与原理



#### 自定义控件流程

​           [Android自定义控件进阶01-自定义控件开发套路与流程](https://github.com/733gh/HarmonyOS-Notes/blob/master/android/Android%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8E%A7%E4%BB%B6%E8%BF%9B%E9%98%B6%E7%B3%BB%E5%88%97/Android%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8E%A7%E4%BB%B6%E8%BF%9B%E9%98%B601-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8E%A7%E4%BB%B6%E5%BC%80%E5%8F%91%E5%A5%97%E8%B7%AF%E4%B8%8E%E6%B5%81%E7%A8%8B.md)



#### Activity启动流程

​         **[精选原创]Android Activity启动过程详解**  https://blog.csdn.net/allen_xu_2012_new/article/details/131167564  

​        android framework层源码解析 https://github.com/yipianfengye/androidSource/tree/master





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

  

#### Cmake编译

- [cmake-examples](https://github.com/ttroy50/cmake-examples)  +[文档教程](https://sfumecjf.github.io/cmake-examples-Chinese)  CMake详细教程

-  [CMake 入门实战](https://www.hahack.com/codes/cmake/)
- [NDK(三)：静态库和动态库](http://guidongyuan.cn/2018/09/25/NDK%28%E4%B8%89%29%EF%BC%9A%E9%9D%99%E6%80%81%E5%BA%93%E5%92%8C%E5%8A%A8%E6%80%81%E5%BA%93/)
- [android studio cmake生成.a文件(静态库)及调用(c c++)静态库.a](https://blog.csdn.net/qingfeng812/article/details/132674778)
- [Android jni引用第三方so动态库和.a静态库并且调用(c)方法](https://blog.csdn.net/qingfeng812/article/details/132688988?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132688988%22%2C%22source%22%3A%22qingfeng812%22%7D)
- [CMake添加外部动态/静态库到本地工程](https://zhuanlan.zhihu.com/p/544340082)



#### NDK闪退

- [Android稳定性系列-01-使用 Address Sanitizer检测原生代码中的内存错误](https://blog.csdn.net/xiangang12202/article/details/128979055)
- https://github.com/google/breakpad
- [Android在Windows下无需编译Breakpad源码就能使用](https://www.jianshu.com/p/0bfe7800bdef)  精选
- [Android Native Crash 捕获之 BreakPad](https://blog.csdn.net/yanbober/article/details/108586835)
-  [Android性能优化(1)-使用Breakpad捕获Android Native Crash](https://juejin.cn/post/6935472686655078414)
- [Android使用google breakpad捕获分析native cash](https://www.cnblogs.com/liqw/p/10616410.html)

- https://github.com/AndroidAdvanceWithGeektime/Chapter01 集成了[Breakpad](https://github.com/google/breakpad) 来获取发生 native crash 时候的系统信息和线程堆栈信息。
-  [崩溃日志收集框架方案选型调研](https://www.jianshu.com/p/4120639526ff)



#### JNI优化



[JNI中基本类型数组的传递方法（无需拷贝数据！！！）](https://blog.csdn.net/autumn20080101/article/details/8645480)





### 音视频

#### 资料汇总

-  [音视频开发系统学习的浪漫马车之总目录](https://juejin.cn/post/7033711226827833351/)
- [Android OpenGL ES 学习系列教程](https://blog.csdn.net/u011418943/article/details/128421098)



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

- [Android原生编解码接口 MediaCodec 之——踩坑](https://cloud.tencent.com/developer/article/2147516) 

  **经验之谈**：如果初始化MediaFormat视频流的预设宽高高于**当前手机支持的解码最大分辨率**那么在调用MediaCodec.configure的时候就会crash。把MediaFormat.createVideoFormat时候的宽高设置小一点就ok了，那么就会有另外一个问题，就是如果我设置`1080*720`的后，视频流来了一个`1920*1080`的会不会有影响？如果当前设备的最大分辨率高于这个值，就算预设值不一样，也还是可以正常解码并显示1920*1080的画面。那么如果低于这个值呢？**两种情况 `绿屏`／`MediaCodec.dequeueInputBuffer的值一直抛IllegalStateException`**

  Android手机硬解码支持最大分辨率查看：手机路径：/system/vendor/etc/media_codecs.xml

  所以Android手机必须支持软解码！



> AAC的音频文件格式有ADIF和ADTS：
>
> - ADIF：Audio Data Interchange Format 音频数据交换格式。这种格式的特征是可以确定的找到这个音频数据的开始，不需进行在音频数据流中间开始的解码，即它的解码必须在明确定义的开始处进行。故这种格式常用在磁盘文件中。
> - ADTS：Audio Data Transport Stream 音频数据传输流。这种格式的特征是它是一个有同步字的比特流，解码可以在这个流中任何位置开始。它的特征类似于mp3数据流格式。
>
> 简单来说，ADIF只有一个统一的头，所以必须得到所有的数据后解码，ADTS每一帧都有头信息，可以从任意帧开始解码，因此网络上的aac基本都是ADTS格式。



#### 视频编解码(直播)

注意事项：

1. 安卓部分低端机，硬解码支持的最大分辨率是2560x1440或者其它某个分辨率，视频流超过手机最大的分辨率之后，解码器解码的时候会报异常。无法解码，这种情况下需要走软解！故android一定要支持软解。
1. 难点：高分辨率条件下的软解码渲染性能问题。
1. 难点：FFmpeg软解码渲染RGB32数据，延迟0.5s的问题。

> 主要是H264,H265格式的硬解码和软解码播放。特别注意高清分辨率下的，软解码播放问题。
>
> 硬解码用系统解码器，软解码用FFmpeg

- [安卓硬解码性能问题](https://github.com/Bilibili/ijkplayer/issues/1954) 
- [Android视频播放器开发-渲染YUV图像](https://kason.site/posts/android-render-yuv)  H264格式的视频，一般从视频解码器解码出来的帧图像数据都是YUV格式的，如果使用`SurfaceView`渲染，需要先转换成RGB格式再渲染，效率会很低。这时候可以借助OpenGL强大的着色器语言，在GPU完成YUV到RGB转换，实现YUV图像的高效渲染。
- [使用FFmpeg解码并用swscale将YUV转为RGB](https://www.cnblogs.com/ichenwin/p/10772026.html)

> Android  视频软解码方案
>
> 解决硬解码无法解决的机型问题。无法播放超过手机自身分辨率的视频流。

1.  FFmpeg 解码H264 /H265 帧数据为YUV420     然后借助  libyuv 把YUV420转换为RGB格式。这样就能渲染了。
2.  FFmpeg 解码H264/ H265 帧数据为YUV420     然后借助  FFmpeg自带的swscale模块 把YUV420转换为RGB格式。这样就能通过渲染了。（技术打通，但是软解存在延迟0.5秒的问题）遗留问题。

-  [Android通过ffmpeg解码视频](https://www.jianshu.com/p/5c4608a72187)
-  [详解 YUV 格式（I420/YUV420/NV12/NV12/YUV422）](https://paaatrick.com/2020-01-26-yuv-pixel-formats/)
-  [YUV各种格式的详解](https://blog.csdn.net/weixin_44517656/article/details/117526561)
-  [图解YU12、I420、YV12、NV12、NV21、YUV420P、YUV420SP、YUV422P、YUV444P的区别.md](https://github.com/byhook/ffmpeg4android/blob/master/readme/%E5%9B%BE%E8%A7%A3YU12%E3%80%81I420%E3%80%81YV12%E3%80%81NV12%E3%80%81NV21%E3%80%81YUV420P%E3%80%81YUV420SP%E3%80%81YUV422P%E3%80%81YUV444P%E7%9A%84%E5%8C%BA%E5%88%AB.md)
-  [AVFrame 与 yuv420那些事](https://blog.csdn.net/lanxiaziyi/article/details/74139729)
-  [FFmpeg中AVFrame YUV420P格式分析](https://rumenz.com/rumenbiji/ffmpeg-avframe-yuv420p.html)
-   [Android MediaCodec硬解码、ffmpeg软解码，兼顾机型一致性和性能](https://juejin.cn/post/6997637274850721822)
-   [AVFrame的数据填充方式 ](https://www.cnblogs.com/lidabo/p/15843868.html)
-    [FFmpeg RGB转YUV ](https://www.cnblogs.com/linuxAndMcu/p/12127975.html)
-   [new、delete、指向连续空间的指针、数组、空间释放、空间申请[C++\][内存管理]](https://www.cnblogs.com/neworiginou/archive/2012/02/20/2359165.html)
-    [FFmpeg的H264解码实战](https://juejin.cn/post/7022653742029733925#heading-5)



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

-  [将AVFrame转换为指定格式的AVFrame](https://avmedia.0voice.com/?id=46772)

- [ffmpeg从AVFrame取出yuv数据到保存到char*中](https://blog.csdn.net/weixin_34252090/article/details/94602122)




### 自定义View

#### 案例

> 基础库封装

- https://github.com/kongpf8848/ViewWorld  About自定义View合集，展示各种自定义View/控件。项目包含了自定义Banner轮播图控件，自定义验证码输入框，自定义TabLayout等控件，持续更新中

- https://github.com/xinghongfei/awesome-view 自定义View有这些足够了

- https://github.com/Tim9Liu9/TimLiu-Android 自己总结的Android开源项目及库

- https://github.com/AbrahamCaiJin/CommonUILibrary

- https://github.com/HpWens/MeiWidgetView

- https://github.com/JaynmBo/StockDemo  Android 自定义View——实现股票自选列表滑动效果

  



> 矩形框(矩形框伸缩,矩形框标注)

- https://juejin.cn/post/7239881176679989307  Android自定义控件之算法标注框（图片上标注）
- https://blog.csdn.net/zz51233273/article/details/107629079   Android 自定义View实现可拖动边框缩放的矩形
- https://github.com/YinCanSheng/JaneB_CustomZoomBox  自定义可移动伸缩的矩形框
- https://github.com/wzgl5533/CropView 绘制裁剪框（设置圆形，椭圆和矩形）
- https://blog.csdn.net/Coo123_/article/details/90755157  Android自定义View之区块选择器



> 其它自定义案例

- https://github.com/385841539/HorizontalScrollSelectedView   横向滚动的，可以支持大量文本选择的 自定义View ，一行代码 ， 简单易用 ， 无OOM情况
- https://github.com/AnliaLee/BookPage Android自定义View实现翻页效果，并附带实现教程
- https://github.com/donkingliang/ConsecutiveScroller ConsecutiveScrollerLayout是Android下支持多个滑动布局(RecyclerView、WebView、ScrollView等)和普通控件(TextView、ImageView、LinearLayou、自定义View等)持续连贯滑动的容器,它使所有的子View像一个整体一样连续顺畅滑动。并且支持布局吸顶功能。
- https://github.com/chezi008/VideoSurveillance 视频监控，四宫格视图。双击放大，视频无缝衔接
- https://blog.csdn.net/yan13507001470/article/details/116530740 自定义viewGroup，动态增/删子view，及四/九宫格排版
- https://www.jb51.net/article/269729.htm Android自定义ViewGroup实现九宫格布局
- https://juejin.cn/post/6844903871777619981?from=search-suggest  Android 自定义View：实现一个 FM 刻度尺
- https://github.com/zfman/TimetableView 一款开源、完善、高效的Android课程表控件，支持添加广告、课程重叠自动处理、透明背景设置、空白格子点击事件处理等丰富的功能，并且有完善的开发文档、案例以供参考
- https://github.com/luojie1024/WeiFur 超级课程表 课程格子 教务系统抓取 SQLite Android Studio HttpWatch Jsoup解析网页
- https://github.com/huangyanbin/smartTable 一款android自动生成表格框架---An Android automatically generated table framework
- https://github.com/faith-hb/WidgetCase 自定义控件模块库：各种风格的自定义控件，拿来就用，API文档详细，持续集成，长期维护，有问必答；

  

> 视频剪辑

-  Android音视频剪辑器自定义View实战！https://juejin.cn/post/7236635197071802424
-  https://github.com/aserbao/AndroidCamera  自定义Android相机(仿抖音 TikTok)，其中功能包括视频人脸识别贴纸，美颜，分段录制，视频裁剪，视频帧处理，获取视频关键帧，视频旋转，添加滤镜，添加水印，合成Gif到视频，文字转视频，图片转视频，音视频合成，音频变声处理，SoundTouch，Fmod音频处理。



#### 教程

> 基础

-  https://blog.csdn.net/xjz729827161/article/details/82315577 android View移动的四种方式

- https://www.jianshu.com/p/6228d3a12da1 Canvas绘图PorterDuffXfermode使用

- https://juejin.cn/post/6844903446240296973  Android PorterDuffXferMode 防坑指南

- https://www.jianshu.com/p/2a967143f894 Android 图层混合模式PorterDuff.Mode
-  https://github.com/733gh/HarmonyOS-Notes/tree/master/android/Android%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8E%A7%E4%BB%B6%E8%BF%9B%E9%98%B6%E7%B3%BB%E5%88%97  Android自定义控件进阶系列

> 自定义View教程

1. https://blog.csdn.net/chaseDreamer_/article/details/97262581 Android 获取View的位置参数：x,y和相对父容器的偏移量以及中心点坐标
2. https://blog.csdn.net/qq_31339141/article/details/90109123  Android自定义View系列：事件拦截机制（触摸反馈机制）
3. https://blog.csdn.net/AND_YOU_with_ME/article/details/78646220 Android 手势检测---GestureDetector
4. https://www.gcssloop.com/customview/gestruedector.html 安卓自定义View进阶-手势检测(GestureDetector)
5. https://www.gcssloop.com/customview/scalegesturedetector.html  安卓自定义View进阶-缩放手势检测(ScaleGestureDecetor)
6. https://blog.csdn.net/hty1053240123/article/details/77866302 Android中onInterceptTouchEvent、dispatchTouchEvent及onTouchEvent的调用顺序及内部原理
7. Android自定义view触摸判断长按 事件 
8. https://blog.csdn.net/guolin_blog/article/details/48719871   Android Scroller完全解析，关于Scroller你所需知道的一切
9. https://blog.csdn.net/Coo123_/article/details/90755157  Android自定义View之区块选择器

> 刘望舒自定义View系列

-  [Android View体系（一）视图坐标系](https://blog.csdn.net/itachi85/article/details/50708391)   [个人博客](https://liuwangshu.cn/application/view/1-coordinate-system.html)
-  https://blog.csdn.net/u010126792/article/details/85238050   Android 绘图学习
-  https://www.gcssloop.com/customview/CoordinateSystem.html  安卓自定义View基础-坐标系

> 开源系列

-  https://github.com/xinghongfei/awesome-view







## 架构设计



### 架构方案

> [Android架构之MVC、MVP、MVVM详解](https://qwerhuan.gitee.io/2020/08/16/android/android-jia-gou-zhi-mvc-mvp-mvvm-xiang-jie/)

 关于MVC/MVP/MVVM的一些错误认识  https://juejin.cn/post/6844903938873901064



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

-  Jetpack Compose 架构比较：MVP & MVVM & MVI  https://blog.csdn.net/vitaviva/article/details/117433393

- https://github.com/jenly1314/MVVMFrame   MVVMFrame for Android 是一个基于Google官方推出的Architecture Components dependencies（现在叫JetPack）{ Lifecycle，LiveData，ViewModel，Room } 构建的快速开发框架。有了MVVMFrame的加持，从此构建一个MVVM模式的项目变得快捷简单。
-  [Android之MVVM简单例子](https://blog.csdn.net/qq_17441227/article/details/120219584)



#### MVI架构

-  MVVM 进阶版：MVI 架构了解一下~  https://juejin.cn/post/7022624191723601928
-   [Android架构学习之路三-MVX](https://ljd1996.github.io/2022/01/11/Android%E6%9E%B6%E6%9E%84%E5%AD%A6%E4%B9%A0%E4%B9%8B%E8%B7%AF%E4%B8%89-MVX/)

#### 传统架构

> Java+RxJava+Okhttp+Retrofit+MVP
>
> kotlin+RxJava+Okhttp+Retrofit+MVP

   参考文献：

-  [Android MVP架构从入门到精通-真枪实弹](https://juejin.cn/post/6844903720036073480) +[github源码](https://github.com/serge66/MVPDemo)  Android MVP架构Demo--Android MVP架构从入门到精通-真枪实弹

> Java+RxJava+Okhttp+Retrofit+MVVM



#### 组件化架构

> Java+RxJava+Okhttp+Retrofit+MVP+组件化
>
> kotlin+RxJava+Okhttp+Retrofit+MVP+组件化

组件化架构是必须掌握的一种架构方式，必须掌握！



- [CyxbsMobile_Android](https://github.com/RedrockMobile/CyxbsMobile_Android?tab=readme-ov-file) 掌邮APP多模块组件化架构



#### 跨平台架构



- https://github.com/persilee/android_ctrip  Android Flutter 混合开发高仿大厂App



#### 多渠道架构

> 非常实用的一种架构方式。必须掌握。

​       何时会用的 flavor ? 
 一个产品，主体功能相同，但又存在差异。比如国内各个手机厂商众多。你的产品想使用各个厂商手机内置的钱包支付功能怎么办？
把所以厂商sdk集成，然后根据厂商品牌做条件判断，好像也是一种办法。缺点就是用户只有一种支付方式，却要把所以厂商钱包都集成进去🙄。 解决这样类似的需求，该 flavor 出场了。

  **[优秀原创]Android Gradle flavor —— 打造不同风味的app**  https://juejin.cn/post/7031399811173744648

 [android多渠道 依赖,android 不同渠道 添加不同依赖jar 使用不同代码](https://huaweicloud.csdn.net/64f988bb4cd6367bad133106.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6NTE3MjIwNywiZXhwIjoxNzExMzY2OTE1LCJpYXQiOjE3MTA3NjIxMTUsInVzZXJuYW1lIjoidnBzc2YifQ.i8wnNbXEpi1_K_nqwVUHjGNttndmvy5PicFAWpzBrsg)



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
- [Android 上传文件到 FTP 服务 器  ](https://www.cnblogs.com/renhui/p/7732143.html)  
- [retrofit 请求,BaseURL部分缺失，踩坑](https://blog.csdn.net/csdnzzu/article/details/78538596)

> 网络状态变化监听

- https://juejin.cn/post/7011004836590288933 Android进阶之路 - 实时监听网络状态

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

> 这里包含了Sqlite数据库存储，SD文件的操作。SP存储等

 [Android数据库框架该如何选？](https://juejin.cn/post/7020223144082276383)

##### Room(推荐)

> Sqlite ORM框架：ROOM(Google 官方)   也是目前Android主流的数据库ORM框架。
>
> 优势：缩减代码，节省时间和精力。**减少对 SQL 的直接操作，更加类型安全的读写数据库**。

处理大量结构化数据的应用可极大地受益于在本地保留这些数据。最常见的使用场景是缓存相关的数据，这样一来，当设备无法访问网络时，用户仍然可以在离线状态下浏览该内容。

Room 持久性库在 SQLite 上提供了一个抽象层，以便在充分利用 SQLite 的强大功能的同时，能够流畅地访问数据库。具体来说，Room 具有以下优势：

- 提供针对 SQL 查询的编译时验证。
- 提供方便注解，可最大限度减少重复和容易出错的样板代码。
- 简化了数据库迁移路径。

出于这些方面的考虑，我们强烈建议您使用 Room，而不是[直接使用 SQLite API](https://developer.android.com/training/data-storage/sqlite?hl=zh-cn)。

[Room版本更新历史官网查询](https://developer.android.com/jetpack/androidx/releases/room)

[Room开发指南官网](https://developer.android.com/training/data-storage/room?hl=zh-cn)

[Room 数据库升级技术：Schema、单个数据库版本升级和多个版本跨越升级)](https://blog.csdn.net/qq_24252589/article/details/131187588)

[Android——Jetpack之Room学习（java实现 附demo）](https://blog.csdn.net/The_onion/article/details/128066517)

[Android room条件查询 android room基本开发用法](https://blog.51cto.com/u_16099328/6988222)

 [将Room的使用方式塞到脑子里](https://juejin.cn/post/6992875656707211271#heading-23)

 [Room数据库 -- TypeConverter简单理解](https://juejin.cn/post/7006898548411203620)

 [Room-数据持久化存储(进阶)](https://www.cnblogs.com/mymy-android/p/14943884.html)

 [android room自动升级数据库](https://www.jianshu.com/p/7ce5b2c3c301)

[Android Room 数据库升级](https://juejin.cn/post/7295576148364328999)



#### 权限

-  [hook Android 权限请求， 插入权限目的dialog显示。](https://juejin.cn/post/7087084927249809415) 

#### 异常

- [xCrash](https://github.com/iqiyi/xCrash/blob/master/README.zh-CN.md) xCrash 能为安卓 app 提供捕获 java 崩溃，native 崩溃和 ANR 的能力。不需要 root 权限或任何系统权限。
- 

#### 动画

- https://github.com/kongpf8848/Animation  Android各种动画效果合集，项目包含了丰富的动画实例(逐帧动画，补间动画，Lottie动画，GIF动画，SVGA动画)，体验动画之美，让Android动起来
- https://github.com/REBOOTERS/AndroidAnimationExercise  Android 动画各种实现，包括帧动画、补间动画和属性动画的总结分享
- https://github.com/OCNYang/Android-Animation-Set  Android 所有动画系列详尽教程。 Explain all animations in Android.



#### 多语言

- https://github.com/getActivity/MultiLanguages  Android 多语种适配框架，兼容高版本，适配第三方库语种


#### Fragment

- [Fragment 可见性监听方案](https://www.jianshu.com/p/75efeede8a95)

- [Fragment可见性及懒加载终极解决方案](https://www.jianshu.com/p/de332ecdd14d) 

- [Fragment 可见性监听方案 - 完美兼容多种 case](https://cloud.tencent.com/developer/article/1937901)





### 业务组件

#### 推送

​       Java服务端集成Google FCM推送的注意事项和实际经验  https://blog.csdn.net/qq_35683545/article/details/129100871

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
-  https://juejin.cn/post/6844903936910950407  [Android]微信h5支付的正确打开方式

#### 下载

https://www.jianshu.com/p/3b269082cbbb  使用 Okhttp 下载文件和更新进度条

#### 表单

https://github.com/edhlily/blockview  Android动态格子布局（淘宝，京东等首页）



### UI组件



#### 开源收藏

- https://github.com/zincPower/UI2018      用于结合“江澎涌”公众号分享 Android 高级 UI 知识点，形成知识体系

 

#### 公共组件

> 样式

 https://github.com/getActivity/ShapeView  Shape 支持在布局中直接定义啦，支持设置阴影，文字渐变色，状态选择器





#### 布局

> 底部导航栏

- [Android通过RadioGroup+Fragment实现底部导航及切换](https://blog.csdn.net/FRYAN28/article/details/101367478) 

> 基础知识

-  [Fragment的生命周期以及onActivityCreated()被弃用](https://blog.csdn.net/Ym_quiet/article/details/121345411)

> 嵌套滚动

- https://github.com/donkingliang/ConsecutiveScroller  ConsecutiveScrollerLayout是Android下支持多个滑动布局(RecyclerView、WebView、ScrollView等)和普通控件(TextView、ImageView、LinearLayou、自定义View等)持续连贯滑动的容器,它使所有的子View像一个整体一样连续顺畅滑动。并且支持布局吸顶功能。



#### 列表

> 基础列表

- [GirdView网格列表的使用](https://www.jianshu.com/p/68bf875214d6)

- https://github.com/jdsjlzx/LRecyclerView RecyclerView下拉刷新，自动加载更多；仿IOS侧滑Item删除菜单（盼望大家扩展更多功能）

  

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
-  https://github.com/tjek/zoomlayout
-  https://github.com/yinxuming/VideoTouchScaleRotate Android视频播放画面双指旋转、缩放、平移以及回弹动效实现（二）



##### TimeRuler

> 复杂的自定义View

https://blog.csdn.net/Coo123_/article/details/90755157  Android自定义View之区块选择器

https://github.com/zjun615/RulerView 卷尺系列控件，包含：普通卷尺（如：体重）、金额尺、时间尺

https://github.com/dingyongxiang/TimeRulers  一个视频时间轴 仿萤石云录像时间轴

https://github.com/wangliu1994/VideoTimeRuler 视频播放进度 时间尺

https://github.com/huangdali/TimeRuler  时间轴、时间刻度尺   参考教程：android自定义view，时间刻度尺，时间轴，视频轴 https://blog.csdn.net/qq137722697/article/details/78118306

https://github.com/huangdali/RulerView  时间轴、时间刻度尺

 https://github.com/qianquanQutman/TimeRuler   仿萤石云视频时间轴, 时间选择  ios

https://github.com/Liberations/TimeRuler   可以缩放平移的时间刻度尺，方便自定义UI需求。仿萤石云历史录像时间轴

https://juejin.cn/post/6844903437843300366  可缩放时间轴和录像片段选择器的实现

https://github.com/qiangzhouliang/QATimeRule   时间刻度尺插件封装

https://github.com/chan106/JCTimeLineView   仿萤石时间轴控件

https://gitee.com/wzy901213145499/Tunlview  一个完美的视频播放条控件（刻度尺），可以将控件与时间对应起来，也可以对控件进行移动和缩放,把时间戳和位置对应起来

https://github.com/ljfxyj2008/ScalableTimebar ----->参考教程：可缩放时间轴和录像片段选择器的实现 https://ljfxyj2008.github.io/2015/12/09/%E5%8F%AF%E7%BC%A9%E6%94%BE%E6%97%B6%E9%97%B4%E8%BD%B4%E5%92%8C%E5%BD%95%E5%83%8F%E7%89%87%E6%AE%B5%E9%80%89%E6%8B%A9%E5%99%A8%E7%9A%84%E5%AE%9E%E7%8E%B0.html#





##### Banner



- https://github.com/OCNYang/PageTransformerHelp



##### 短信验证码



- https://github.com/kongpf8848/ViewWorld



#### 加载框

- https://github.com/maning0303/MNProgressHUD
- https://github.com/Kaopiz/KProgressHUD/tree/master  采用



#### 进度条

- https://github.com/Ccapton/Collection-Android-Progress 进度条大全 安卓自定义Progressbar控件汇总
- https://github.com/lyx0206331/CircleProgressBar  简单环形进度条实现，带进度显示，可设置居中图片，可显示进度值，可选择进度样式，可选择动画效果，也可当按下时带进度的按钮使用
- https://github.com/glassLake/SmoothRoundProgressbar/tree/master  圆环进度条，首尾交接处圆润,自带动画，可自定义渐变，环厚度，转动速度
- https://github.com/zhongruiAndroid/Ring 圆环进度条,环形进度条



#### 对话框

- https://github.com/kongzue/DialogX?tab=readme-ov-file  DialogX对话框组件库，更加方便易用，可自定义程度更高，扩展性更强，轻松实现各种对话框、菜单和提示效果，更有Material You、iOS、MIUI等主题扩展可选



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



#### SeekBar

- https://github.com/woxingxiao/BubbleSeekBar  A beautiful Android custom seekbar, which has a bubble view with progress appearing upon when seeking. 自定义SeekBar，进度变化更以可视化气泡样式呈现



#### Shadow

-  Android进阶之路 - 背景阴影、阴影背景 https://juejin.cn/post/7256999484801187899

#### 裁剪

> 区域选择，区域裁剪，区域拖拉

- https://github.com/igreenwood/SimpleCropView  A simple image cropping library for Android.
-   https://github.com/jdamcd/android-crop
-  https://github.com/Yalantis/uCrop
-  https://github.com/ArthurHub/Android-Image-Cropper
-  https://github.com/CanHub/Android-Image-Cropper
-  https://github.com/steelkiwi/cropiwa
- https://github.com/lyrebirdstudio/Croppy

- [CropImageView android上的一个图片裁剪控件](https://blog.csdn.net/aaa111/article/details/75212872)

- https://github.com/minminaya/CropViewDemo 裁剪旋转的自定义View（Custom View Of Crop and Rotate）

-  https://blog.csdn.net/qq_42545144/article/details/119536339  Andriod 自定义view可拉伸缩放移动矩形框（详解）

#### 其它

- https://github.com/RuffianZhong/RWidgetHelper  Android UI 快速开发，专治原生控件各种不服
- https://github.com/EHENJOOM/ShadowCardView  自定义阴影颜色的CardView
- https://github.com/donkingliang/RadarView  Android雷达效果自定义View.  Android自定义View 雷达扫描效果。可以根据自己的需求配置View的主题颜色、扫描颜色、扫描速度、圆圈数量、是否显示水滴等。
- https://blog.csdn.net/weixin_39541600/article/details/117588057  android 雷达坐标系,自定义view之雷达搜索扩散圆从无到有
- https://github.com/ly-sun/CircleTimePicker  这是一款仿IOS10(就寝功能)的圆盘时间选择器
- https://github.com/gzu-liyujiang/AndroidPicker  安卓选择器类库，包括日期及时间选择器（可用于出生日期、营业时间等）、单项选择器（可用于性别、民族、职业、学历、星座等）、二三级联动选择器（可用于车牌号、基金定投日期等）、城市地址选择器（分省级、地市级及区县级）、数字选择器（可用于年龄、身高、体重、温度等）、日历选日期择器（可用于酒店及机票预定日期）、颜色选择器、文件及目录选择器、图片选择器等




## 开发辅助



### 项目环境

#### android studio

[解决Android logcat: Unexpected EOF!方法指南](https://huaweicloud.csdn.net/65095fed993dd34278ee3e50.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MjE4MjExLCJleHAiOjE2OTYzMTgwOTksImlhdCI6MTY5NTcxMzI5OSwidXNlcm5hbWUiOiJxaW5nZmVuZzgxMiJ9.9DJl_9A1KKflSE3nwuQZTDyqZLfYUp0gMf6-c9muRec)

[android studio中文乱码各种情况的解决办法](https://cloud.tencent.com/developer/article/1931701)

[新版Android Studio火烈鸟 在新建项目工程时 无法选java的语言模板解决方法](https://blog.csdn.net/Life_s/article/details/131044320)

[Android BuildConfig不生成的解决办法](https://blog.csdn.net/yuzhiqiang_1993/article/details/130431271)

#### gradle

- [GradleX](https://github.com/yechaoa/GradleX)  一份关于Gradle的学习路线

- [掘金专栏一览](https://juejin.cn/column/7123935861976072199)
- [【Gradle-1】入门Gradle，前置必读](https://juejin.cn/post/7155109977579847710)
- [【Gradle-2】一文搞懂Gradle配置](https://juejin.cn/post/7160337743552675847)
- [【Gradle-3】Gradle中的DSL，Groovy & Kotlin](https://juejin.cn/post/7166638852503765006)
- [【Gradle-4】Gradle的生命周期](https://juejin.cn/post/7170684769083555877)
- [【Gradle-5】Gradle常用命令与参数](https://juejin.cn/post/7171493698243395597)
- [【Gradle-6】一文搞懂Gradle的依赖管理和版本决议](https://juejin.cn/post/7215579793261117501)
- [【Gradle-7】Gradle构建核心之Task指南](https://juejin.cn/post/7248207744087277605)
- [【Gradle-8】Gradle插件开发指南](https://juejin.cn/post/7267091810380136508)
- [【Gradle-9】Gradle插件发布指南](https://juejin.cn/post/7280062870669246525)
- [【Gradle-10】不可忽视的构建分析](https://juejin.cn/post/7282150745164005432)
- [【Gradle-11】动态修改VersionName和VersionCode](https://juejin.cn/post/7282691800858705957)
- [【Gradle-12】分析so文件和依赖的关系](https://juejin.cn/post/7287429638019448888)
- [【Gradle-13】SNAPSHOT版本检查](https://juejin.cn/post/7292416512333840438)
- [【Gradle-14】编译优化之Gradle最佳配置实践](https://juejin.cn/post/7344625554529730600)



#### adb

​    [解决'ADB' 不是内部或外部命令，也不是可运行的程序 或批处理文件](https://www.cnblogs.com/handsomefa9527/articles/13030403.html)



### 版本控制



#### git

- [Failed to connect to github.com port 443: Connection refused问题解决](https://zhuanlan.zhihu.com/p/642910282)

#### svn

 [SVN设置忽略文件和文件夹](https://blog.csdn.net/qq_31772441/article/details/100930840)

 [TortoiseSVN 安装、使用教程](https://blog.csdn.net/ZYS10000/article/details/106543931)

 [解决SVN文件不显示绿色小钩图标问题](https://www.cnblogs.com/ftx3q/p/15340096.html)

 [‘D:\Program‘ 不是内部或外部命令，也不是可运行的程序 idea配置svn路径空格问题](https://blog.csdn.net/chedanquestion/article/details/119103761)

![image-20240307144318350](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202403071443463.png)



### 打包发布

#### jar/aar打包

> 目前AGP8.0以上的时候，使用id 'maven-publish' 打包到JitPack存在问题。需要打包的情况下，先使用AGP8.0以下版本。

  记录一次发布jitpack  https://blog.xxin.xyz/2024/01/29/%E8%AE%B0%E5%BD%95%E4%B8%80%E6%AC%A1%E5%8F%91%E5%B8%83jitpack/

  android studio2022.3.1 ,gradle8 打包aar、sources.jar 遇到的问题   https://juejin.cn/post/7322305256171913256

  android将library上传到JitPack图文教程  https://juejin.cn/post/7137694434682109988

#### 更改包名

   Android Studio修改项目名称和包名的步骤   https://blog.csdn.net/qq_34205684/article/details/114401402





### 开发工具类



#### 上传下载

https://www.jianshu.com/p/205566de2adb 封装一个 OkHttp 的下载工具类

https://github.com/kongzue/BaseOkHttpV3?tab=readme-ov-file#%E6%96%87%E4%BB%B6%E4%B8%8B%E8%BD%BD OkHttp的二次封装库，提供各种快速使用方法以及更为方便的扩展功能。提供更高效的Json请求和解析工具以及文件上传下载封装，HTTPS和Cookie操作也更得心应手。



## 性能优化

### 内存泄漏

- [static静态方法中new的对象会被回收吗](https://juejin.cn/s/static%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95%E4%B8%ADnew%E7%9A%84%E5%AF%B9%E8%B1%A1%E4%BC%9A%E8%A2%AB%E5%9B%9E%E6%94%B6%E5%90%97)

### 超时响应

- [BlockCanary — 轻松找出Android App界面卡顿元凶](http://blog.zhaiyifan.cn/2016/01/16/BlockCanaryTransparentPerformanceMonitor/).  [github源码](https://github.com/markzhai/AndroidPerformanceMonitor/blob/master/README_CN.md)
- https://github.com/SalomonBrys/ANR-WatchDog
- [ANR监控方案总结](https://www.jianshu.com/p/d08f4a3d536d) 
- [xCrash ANR 兼容性测试](https://www.dalvik.work/2021/11/29/xcrash-anr-compatibility/#)
- [Android ANR处理流程](https://sniffer.site/2017/06/25/android-anr%E5%A4%84%E7%90%86%E6%B5%81%E7%A8%8B/#/%E8%BE%93%E5%85%A5%E6%97%A0%E5%93%8D%E5%BA%94)



### 性能检测

- [Android常用的性能分析工具](https://sniffer.site/2023/10/20/android常用的性能分析工具使用简介/#)
- 

## 源码解读



## 行业大佬

> 学习它人，更能激励自己。随时了解与大佬们的差距，持续学习



> OCNYang   杭州涂鸦信息技术有限公司

- https://github.com/OCNYang/AndroidBang  《Android 江湖花名册》
- https://github.com/OCNYang/OCNYang/blob/master/resume.md



## 笔试面试

- https://github.com/Shouheng88/Android-notes/tree/master    **[Android-notes](https://github.com/Shouheng88/Android-notes)**
- https://github.com/chiclaim/AndroidAll 
- https://github.com/Timdk857/Android-Architecture-knowledge-2-
- https://github.com/BlackZhangJX/Android-Notes   Android开发核心知识点笔记（不断更新中🔥）
-  https://github.com/AweiLoveAndroid/CommonDevKnowledge  ![:octocat:](https://github.githubassets.com/images/icons/emoji/octocat.png)🔥 🌟⭐⭐⭐ ⭐ 史上最全的BAT大厂Android面试题汇集，以及常用的Android开发的一些技能点，冷门知识点汇总，开发中遇到的坑汇总等干货。
-  https://github.com/pengxurui/AndroidFamily   🔥【Android 面经 + Android 学习指南】一份帮助 Android 开发者知识积累与能力进阶的学习路线
-  https://www.kancloud.cn/alex_wsc/android/1492055



## 应用发布

### 国内应用市场

> 国内应用商店

- 2024年App从备案到上架（国内各大应用市场）全过程  https://blog.csdn.net/u013700502/article/details/134657598
-  [面向中国独立开发者的移动应用备案流程](https://fanthus.github.io/2023/11/10/%E9%9D%A2%E5%90%91%E4%B8%AD%E5%9B%BD%E7%8B%AC%E7%AB%8B%E5%BC%80%E5%8F%91%E8%80%85%E7%9A%84%E7%A7%BB%E5%8A%A8%E5%BA%94%E7%94%A8%E5%A4%87%E6%A1%88%E6%B5%81%E7%A8%8B/)



### 国外应用市场

> 应用签名

- 签名获取错误（错误: java.io.IOException: Invalid keystore format）签名中没打印出MD5信息  https://blog.csdn.net/weixin_44669831/article/details/128416328
- java8以后版本的keytool不再输出md5指纹信息  https://www.cnblogs.com/architectforest/p/17318174.html

> 应用审核

-  GooglePlay 新包提审十几天！依旧在审，问题在哪？ https://blog.csdn.net/Jrchbxt2013/article/details/139114439
-  谷歌上架，为什么会触发填表单，可以避免吗？怎么填表单可以提高通过率？ https://blog.csdn.net/m0_72996522/article/details/138471461



### 第三方库发布

 





# 技术全栈领域

## 后端笔记

  [高并发| 小虾米之路](https://xiaoxiami.gitbook.io/xiami/gao-bing-fa)

 [后端程序员面试问题集锦: README](https://fungkao.gitbook.io/)

[系统架构 - litemall](https://linlinjava.gitbook.io/litemall/project)



### 上云教程

-  快速搭建个人博客 —— 保姆级教程  https://pdpeng.github.io/2022/01/19/setup-personal-blog/#%E5%BA%8F%E8%A8%80



## 前端笔记

[前端架构| fe-share](https://xiaobaiha.gitbook.io/fe-share/engineering/qian-duan-jia-gou)



## 底层技术



### 通信协议

服务器开发通信协议设计介绍：https://github.com/balloonwj/CppGuide/blob/master/articles/%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B/%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%BC%80%E5%8F%91%E9%80%9A%E4%BF%A1%E5%8D%8F%E8%AE%AE%E8%AE%BE%E8%AE%A1%E4%BB%8B%E7%BB%8D.md

https://github.com/Naixes/notes/blob/master/%E7%BD%91%E7%BB%9C%E5%8D%8F%E8%AE%AE.md  网络协议



## 直播技术



### 小程序直播



> 目前系统维护，暂时不支持新开通直播权限了（已有直播权限的账号不影响），具体恢复时间暂不清楚。
>
> 当前如果有直播的需求可以试试视频号直播，小程序内可以跳转视频号直播间，能力文档：https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/channels-live.html
>
> https://developers.weixin.qq.com/community/minihome/doc/000084c0dec2e8a3d2e06b3d36b400

- https://github.com/AJLoveChina/wechat-pusher-player  微信小程序live-pusher/live-player 示例, 使用本地搭建的RTMP服务



