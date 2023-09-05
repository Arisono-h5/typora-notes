#  Android开发笔记



[TOC]

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
- [＜整理总结＞H264/265码流数据包格式分析（带mp4v2封装H264/265为MP4的源码示例）](https://blog.csdn.net/n_i_n/article/details/114140581?spm=1001.2014.3001.5502)  精选文章
- https://github.com/Pandalzm/mp4v2-h265  mp4v2-h265   
- https://github.com/farrellpeng/mp4v2-h265/    mp4v2-h265
- https://github.com/TechSmith/mp4v2  
- [MP4V2 封装h265到MP4文件 及解包MP4](https://blog.csdn.net/manyanhua/article/details/112026968)



#### 视频截图





#### 回音消除





### FFmpeg

#### FFmpeg入门

- [FFmpeg原理介绍](https://ffmpeg.xianwaizhiyin.net/)



## 架构设计



### 架构方案

#### 传统架构

- Java+RxJava+Okhttp+Retrofit+MVP
- kotlin+RxJava+Okhttp+Retrofit+MVP

#### 组件化架构

- Java+RxJava+Okhttp+Retrofit+MVP+组件化
- kotlin+RxJava+Okhttp+Retrofit+MVP+组件化

#### 跨平台架构







### 基础组件

#### 网络

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



