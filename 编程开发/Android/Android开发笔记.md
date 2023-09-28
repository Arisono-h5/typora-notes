#  Android开发笔记



[TOC]

## 基础知识

### Java



- [Java 运算符（操作符）&、&&、|、||、^、＜＜](https://blog.csdn.net/dd_Mr/article/details/123969634)



### kotlin



### C/C++



- [C语言指针变量的定义和使用（精华）](http://c.biancheng.net/view/1991.html)



### Android



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

-  [关于音频帧率与采样率](https://www.suninf.net/2023/01/audio-framerate-and-sample.html)
-  [libfdk_aac编码AAC](https://blog.csdn.net/u010140427/article/details/127765173)
-  [采样个数(样本数)的概念及计算一帧音频的大小](https://blog.csdn.net/weixin_44517656/article/details/117849297)  音频通道数、采样率、采样个数(样本数)、采样位数的概念和计算一帧音频的大小、每秒播放的音频字节大小、一帧音频的播放时长

- [FFmpeg 音频编码](https://octalzero.com/article/88a0d789-5f79-46d9-8706-2c5f063a5157)
- [FFmpeg 解封装 MP4 媒体文件](https://octalzero.com/article/91b62969-d088-46e3-a500-b6b8a3e5278f)



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





## 架构设计



### 架构方案

#### 传统架构

> Java+RxJava+Okhttp+Retrofit+MVP
>
> kotlin+RxJava+Okhttp+Retrofit+MVP

   参考文献：

-  [Android MVP架构从入门到精通-真枪实弹](https://juejin.cn/post/6844903720036073480) +[github源码](https://github.com/serge66/MVPDemo)

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



>  Rxjava2

-  [RxJava 2.x 使用详解(一) 快速入门](https://maxwell-nc.github.io/android/rxjava2-1.html)



#### 图片

#### 日志

#### 存储

#### 权限



### 业务组件

#### 埋点

#### 统计



### UI组件

#### 列表

#### 日历

#### 自定义View

要点：

1.自定义可滚动的四分屏播放控件，支持32路或者不限制。  安防app需要用到。(复杂)

2.自定义时间轴控件，云录像和SD录像需要用到。(复杂)

#### 对话框

#### Toast

#### WebView

#### 输入框

#### 按钮





## 开发辅助



### 项目环境



-  [解决Android logcat: Unexpected EOF!方法指南](https://huaweicloud.csdn.net/65095fed993dd34278ee3e50.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MjE4MjExLCJleHAiOjE2OTYzMTgwOTksImlhdCI6MTY5NTcxMzI5OSwidXNlcm5hbWUiOiJxaW5nZmVuZzgxMiJ9.9DJl_9A1KKflSE3nwuQZTDyqZLfYUp0gMf6-c9muRec)
