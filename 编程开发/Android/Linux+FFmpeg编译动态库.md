FFmpeg编译详细教程

[TOC]



# FFmpeg编译详细教程

> 本文原创：猿视野
>
> 原文地址：[https://developer.aliyun.com/article/1326862?source=5176.11533457](https://developer.aliyun.com/article/1326862?source=5176.11533457&userCode=ywqc0ubl)



## 详细步骤

1. Window系统安装虚拟机 VMware® Workstation 17 Pro  这里没有选择其它路线，是因为在linux系统上编译FFmpeg更加方便。坑相对少一点。
2. electerm   ssh工具，我这里用的是electerm，一款功能强大的开源ssh连接工具，本文用它来ssh连接我的虚拟机。
3. ffmpeg-5.1.3.tar.xz
4. android-ndkc-linux.zip

> 如果你是window系统，在进行本文之前，请先安装Linux虚拟机。我虚拟机安装的是CentOS6.5   建议大家虚拟机上安装CentOS7系列镜像。CentOS6系列版本在2020年的时候，官方不在支持了。影响你yum的使用。

### 下载文件

下载ndk25

> 官网下载：[ndk官网](https://developer.android.google.cn/ndk/downloads)
> 网盘下载：[android-ndk-r25c-linux.zip](http://share.vpssw.com/f/28426853-934783767-fab2be)
>
> 注意，这是linux环境下的ndk。

下载FFmpeg 5.1.3

> 官网下载：[FFmpeg官网](http://ffmpeg.org/download.html#releases)
> 网盘下载：[FFmpeg 5.1.3](http://share.vpssw.com/f/28426853-934783773-d940e8)

下载electerm

>  网盘下载：[electerm](http://share.vpssw.com/f/28426853-934783794-578979)
>
> ssh连接工具，用这个远程连接Linux虚拟机

下载VMware 17 pro

>  网盘下载：[VMware 17 pro破解版](http://share.vpssw.com/f/28426853-934784181-ad2b27)

下载CentOS6.5镜像或CentOS7镜像

> 下载地址：
>
> - Centos系统镜像地址：http://archive.kernel.org/centos-vault/7.8.2003/isos/x86_64/
>
> - Centos系统镜像地址汇总：http://isoredirect.centos.org/centos/7/isos/x86_64/
>
>   这是为了安装Linux虚拟机需要，推荐CentOS7系列版本

下载glibc-2.17

> 网盘下载：[glibc-2.17.tar.gz](http://share.vpssw.com/f/28426853-934783782-2383df)
>
> 这个文件提前下载好，后文会用到

文件下载好了，把FFmpeg 5.1.3和android-ndk-r25c-linux.zip 文件

先上传到你Linux虚拟机自定义的文件夹目录中，如图所示：

![](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309121126649.png)



### 解压文件

解压文件：

```

#解压ffmpeg-5.1.3.tar.xz 
tar -xf ffmpeg-5.1.3.tar.xz

#解压android-ndk-r25c-linux.zip 
unzip android-ndk-r25c-linux.zip 

```



### 编译检查



```
# 编译FFmpeg之前先检查下环境
[root@CentOS6 ffmpeg-5.1.3]# ./configure --disable-x86asm    
#报错,没有安装gcc编译器
```

```
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
ffmpeg-user@ffmpeg.org mailing list or IRC #ffmpeg on irc.libera.chat.
Include the log file "ffbuild/config.log" produced by configure as this will help
solve the problem.
```

#### 安装 gcc编译库

```
[root@CentOS6 yum.repos.d]# yum install -y  gcc

Loaded plugins: fastestmirror, refresh-packagekit, security
Loading mirror speeds from cached hostfile
YumRepo Error: All mirror URLs are not using ftp, http[s] or file.
 Eg. Invalid release/repo/arch combination/
removing mirrorlist with no valid mirrors: /var/cache/yum/x86_64/6/base/mirrorlist.txt
Error: Cannot find a valid baseurl for repo: base
```

#### yum源失效问题

根据日志得出，问题是由于CentOS 6.5 yum源失效导致的错误，我虚拟机安装的是CentOS6.5版本，官方已经不支持CentOS6系列了，所以需要更换yum源地址。

解决CentOS6 yum源失效的问题：

```
#先切换文件夹目录，找到目录下的文件CentOS-Base.repo
cd /etc/yum.repos.d
```

CentOS-Base.repo文件修改为如下：

我这里用的是阿里的镜像

```

# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#
#

[base]
name=CentOS-$releasever - Base
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/
#baseurl=https://vault.centos.org/6.10/os/x86_64/
#阿里云镜像
baseurl=http://mirrors.aliyun.com/centos-vault/6.5/os/x86_64/
gpgcheck=0
#enabled=0
gpgkey=https://vault.centos.org/6.10/os/x86_64/RPM-GPG-KEY-CentOS-6

#released updates 
[updates]
name=CentOS-$releasever - Updates
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
#baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/
#baseurl=https://vault.centos.org/6.10/updates/$basearch/
#阿里云镜像
baseurl=http://mirrors.aliyun.com/centos-vault/6.5/updates/x86_64/
gpgcheck=0
#enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
#baseurl=http://mirror.centos.org/centos/$releasever/extras/$basearch/
#baseurl=https://vault.centos.org/6.10/extras/$basearch/
#阿里云镜像
baseurl=http://mirrors.aliyun.com/centos-vault/6.5/extras/x86_64/
gpgcheck=0
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
#baseurl=http://mirror.centos.org/centos/$releasever/centosplus/$basearch/
#baseurl=https://vault.centos.org/6.10/centosplus/$basearch/
#阿里云镜像
baseurl=http://mirrors.aliyun.com/centos-vault/6.5/centosplus/x86_64/
gpgcheck=0
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6


#contrib - packages by Centos Users
[contrib]
name=CentOS-$releasever - Contrib
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib
#baseurl=http://mirror.centos.org/centos/$releasever/contrib/$basearch/
#baseurl=https://vault.centos.org/6.10/contrib/$basearch/
#阿里云镜像
baseurl=http://mirrors.aliyun.com/centos-vault/6.5/contrib/x86_64/
gpgcheck=0
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6


```

保存退出后，清除下缓存 yum clean all && yum makecache

> 其中gpgcheck改为  gpgcheck=0    否则会引发错误：GPG key retrieval failed: [Errno 14] problem making ssl connection

参考：[CentOS 6停止维护更新后 yum源失效问题的解决 ](https://www.cnblogs.com/liuyakai/p/14516445.html)

做完这一步，可以正确安装gcc了

```
# 安装gcc 编译库
yum install -y  gcc
```

确认您已经安装了正确版本的gcc和其他编译器工具。您可以使用以下命令来检查：

```
gcc --version make --version
```

```
 #执行命令之后，出现下图，没有报错的话，就可以进行下一步操作了。
 ./configure --disable-x86asm    
```

![image-20230912150231208](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309121502256.png)



### 编译脚本

> 安装好gcc编译库之后，现在可以来新建编译脚本了

在FFmpeg目录下新建build_android.sh，想了解详细配置参数请前往[这里](https://blog.csdn.net/zhaofuguang/article/details/122690534)。

```
# touch 新建文件
[root@CentOS6 ffmpeg-5.1.3]# touch build_android.sh
# vim 编辑build_android.sh
[root@CentOS6 ffmpeg-5.1.3]# vim build_android.sh
```

写入脚本内容：

```
#!/bin/bash
#特别注意： 以下路径需要修改成自己Linux系统中的NDK目录！前面上传的ndk解压文件当中
TOOLCHAIN=/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64
# 最低支持的android sdk版本
API=21
# --extra-cflags中添加'-DVK_ENABLE_BETA_EXTENSIONS=0', 防止引用vulkan_beta.h头文件
function build_android
{
echo "Compiling FFmpeg for $CPU"
./configure \
 --prefix=$PREFIX \
 --disable-neon \
 --disable-hwaccels \
 --disable-gpl \
 --disable-postproc \
 --enable-shared \
 --enable-jni \
 --disable-mediacodec \
 --enable-small \
 --enable-gpl \
 --disable-decoder=h264_mediacodec \
 --disable-static \
 --disable-doc \
 --disable-programs \
 --disable-ffmpeg \
 --disable-ffplay \
 --disable-ffprobe \
 --disable-avdevice \
 --disable-symver \
 --cross-prefix=$CROSS_PREFIX \
 --target-os=android \
 --arch=$ARCH \
 --cpu=$CPU \
 --cc=$CC \
 --cxx=$CXX \
 --enable-cross-compile \
 --sysroot=$SYSROOT \
 --extra-cflags="-DVK_ENABLE_BETA_EXTENSIONS=0 -mno-stackrealign -Os -fpic $OPTIMIZE_CFLAGS" \
 --extra-ldflags="$ADDI_LDFLAGS" \
 $ADDITIONAL_CONFIGURE_FLAG
make clean
make -j4
make install
echo "The Compilation of FFmpeg for $CPU is completed"
}

#armv8-a
ARCH=arm64
CPU=armv8-a
# r21版本的ndk中所有的编译器都在/toolchains/llvm/prebuilt/darwin-x86_64/目录下（clang）
CC=$TOOLCHAIN/bin/aarch64-linux-android$API-clang
CXX=$TOOLCHAIN/bin/aarch64-linux-android$API-clang++
# NDK头文件环境
SYSROOT=$TOOLCHAIN/sysroot
CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
# so输出路径
PREFIX=$(pwd)/android/$CPU
OPTIMIZE_CFLAGS="-march=$CPU"
build_android

# 交叉编译工具目录,对应关系如下
# armv8a -> arm64 -> aarch64-linux-android-
# armv7a -> arm -> arm-linux-androideabi-
# x86 -> x86 -> i686-linux-android-
# x86_64 -> x86_64 -> x86_64-linux-android-

# CPU架构
#armv7-a
ARCH=arm
CPU=armv7-a
CC=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang
CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang++
SYSROOT=$TOOLCHAIN/sysroot
CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
PREFIX=$(pwd)/android/$CPU
OPTIMIZE_CFLAGS="-mfloat-abi=softfp -mfpu=vfp -marm -march=$CPU "
build_android

# #x86
# ARCH=x86
# CPU=x86
# CC=$TOOLCHAIN/bin/i686-linux-android$API-clang
# CXX=$TOOLCHAIN/bin/i686-linux-android$API-clang++
# SYSROOT=$TOOLCHAIN/sysroot
# CROSS_PREFIX=$TOOLCHAIN/bin/i686-linux-android-
# PREFIX=$(pwd)/android/$CPU
# OPTIMIZE_CFLAGS="-march=i686 -mtune=intel -mssse3 -mfpmath=sse -m32"
# build_android

# #x86_64
# ARCH=x86_64
# CPU=x86-64
# CC=$TOOLCHAIN/bin/x86_64-linux-android$API-clang
# CXX=$TOOLCHAIN/bin/x86_64-linux-android$API-clang++
# SYSROOT=$TOOLCHAIN/sysroot
# CROSS_PREFIX=$TOOLCHAIN/bin/x86_64-linux-android-
# PREFIX=$(pwd)/android/$CPU
# OPTIMIZE_CFLAGS="-march=$CPU -msse4.2 -mpopcnt -m64 -mtune=intel"
# 方法调用
# build_android


```



赋权限755

在FFmpeg目录下的ffbuild目录中，将图中[sh文件](https://so.csdn.net/so/search?q=sh文件&spm=1001.2101.3001.7020)权限改为755，否则编译过程中可能报错无权限执行该文件。build_android.sh文件也赋权一下。

![image-20230912195014415](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309121950474.png)

```
chmod 755  build_android.sh
```

### 执行脚本

```
./ build_android.sh
```

发生报错：

```
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/aarch64-linux-android21-clang is unable to create an executable file.
C compiler test failed.
```

编译失败日志(日志信息位于ffbuild目录下的config.log文件)：

```
BEGIN /tmp/ffconf.YxWX1yPS/test.c
    1	int main(void){ return 0; }
END /tmp/ffconf.YxWX1yPS/test.c
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/armv7a-linux-androideabi21-clang --sysroot=/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/sysroot -DVK_ENABLE_BETA_EXTENSIONS=0 -mno-stackrealign -Os -fpic -mfloat-abi=softfp -mfpu=vfp -marm -march=armv7-a -march=armv7-a -c -o /tmp/ffconf.YxWX1yPS/test.o /tmp/ffconf.YxWX1yPS/test.c
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang: /lib64/libc.so.6: version `GLIBC_2.14' not found (required by /usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang)
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang: /lib64/libc.so.6: version `GLIBC_2.15' not found (required by /usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang)
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang: /lib64/libc.so.6: version `GLIBC_2.14' not found (required by /usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/../lib64/libc++.so.1)
/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/clang: /lib64/libc.so.6: version `GLIBC_2.17' not found (required by /usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64/bin/../lib64/libc++.so.1)
C compiler test failed.
```



**这个错误的原因是未安装2.17版本的glibc库。**

而在CentOS6上，使用`yum install glibc`命令，只能更新到2.12版本。需要手动下载编译安装。

查看当前版本：

```
[root@CentOS6 ffmpeg-5.1.3]# rpm -qa | grep glibc
glibc-common-2.12-1.132.el6.x86_64
glibc-devel-2.12-1.132.el6.x86_64
glibc-2.12-1.132.el6.x86_64
glibc-headers-2.12-1.132.el6.x86_64
```

升级glibc到2.17版本

升级教程参考：[Linux中提示：/lib64/libc.so.6: version `GLIBC_2.17' not found 的解决办法](https://www.jianshu.com/p/a10ffde6a4b1)



### 编译成功

再次编译FFmpeg:

```
./build_android.sh
```

编译成功，可以看到已经生成了.so动态库文件。接下来需要做动态库的裁剪，我们不需要这么大的文件。

![image-20230912170339286](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309121703337.png)



### 裁剪编译



![image-20230914105627544](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309141056663.png)

裁剪FFmpeg打包动态库：

> 注意：  \    后面的：中文注释，不要写进脚本。也不要有空格。

```
--disable-all \               ：禁用所有功能
--disable-everything \        ：禁用所有组件
--enable-jni  \
--enable-small \
--enable-cross-compile \
--enable-protocol=file \      ：启用 file 协议
--disable-encoders \
--enable-encoder=mpeg4 \
--enable-encoder=aac \
--enable-encoder=png \
--enable-encoder=libx264 \
--enable-encoder=libx265 \
--enable-encoder=gif \
--enable-encoder=pcm_alaw \
--enable-encoder=pcm_mulaw \

--disable-decoders \
--enable-decoder=mpeg4 \
--enable-decoder=h264 \
--enable-decoder=hevc \
--enable-decoder=aac \
--enable-decoder=gif \
--enable-decoder=pcm_alaw \       :G.711 alaw
--enable-decoder=pcm_mulaw \      :G.711 mu-law

--disable-parsers \
--enable-parser=h264 \
--enable-parser=hevc \
--enable-parser=aac  \
--enable-parser=aac_latm  \

--disable-muxers \
--enable-muxer=mp4  \           
--enable-muxer=h264 \         
--enable-muxer=hevc \

--enable-shared \               ：编译动态链接库
--disable-static \              ：禁止编译静态链接库
--enable-pthreads \             ：启用线程支持

--disable-doc \
--disable-ffmpeg \
--disable-ffplay \
--disable-ffprobe \
--disable-ffserver \
--disable-doc \
--disable-symver \
--target-os=android \



```



裁剪脚本配置：

>  --disable-all \
>  --disable-everything \
>
> 这两个配置，新手编译时先不要加。

```
#!/bin/bash
# 以下路径需要修改成自己的NDK目录
TOOLCHAIN=/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64
# 最低支持的android sdk版本
API=21
# --extra-cflags中添加'-DVK_ENABLE_BETA_EXTENSIONS=0', 防止引用vulkan_beta.h头文件
function build_android
{
echo "Compiling FFmpeg for $CPU"
./configure \
 --prefix=$PREFIX \
 --enable-shared \
 --enable-cross-compile \
 --enable-protocol=file \
 --enable-jni \
 --enable-gpl \
 --enable-neon \
 --enable-pthreads \
 --disable-encoders \
 --enable-encoder=aac \
 --enable-encoder=png \
 --enable-encoder=libx264 \
 --enable-encoder=libx265 \
 --enable-encoder=gif \
 --enable-encoder=pcm_alaw \
 --enable-encoder=pcm_mulaw \
 --disable-decoders \
 --enable-decoder=h264 \
 --enable-decoder=hevc \
 --enable-decoder=aac \
 --enable-decoder=gif \
 --enable-decoder=pcm_alaw \
 --enable-decoder=pcm_mulaw \
 --disable-parsers \
 --enable-parser=h264 \
 --enable-parser=hevc \
 --enable-parser=aac  \
 --enable-parser=aac_latm  \
 --disable-muxers \
 --enable-muxer=h264 \
 --enable-muxer=hevc \
 --disable-hwaccels \
 --enable-mediacodec \
 --enable-hwaccel=h264_mediacodec \
 --enable-decoder=h264_mediacodec \
 --enable-decoder=hevc_mediacodec \
 --enable-decoder=mpeg4_mediacodec \
 --disable-bsfs \
 --enable-bsf=h264_metadata \
 --enable-bsf=h264_mp4toannexb \
 --enable-bsf=hevc_metadata \
 --enable-bsf=hevc_mp4toannexb \
 --enable-bsf=aac_adtstoasc \
 --disable-filters \
 --disable-static \
 --disable-doc \
 --disable-htmlpages \
 --disable-manpages \
 --disable-podpages \
 --disable-txtpages \
 --disable-programs \
 --disable-ffmpeg \
 --disable-ffplay \
 --disable-ffprobe \
 --disable-avdevice \
 --disable-postproc \
 --disable-symver \
 --disable-indevs \
 --disable-outdevs \
 --disable-devices \
 --disable-asm \
 --cross-prefix=$CROSS_PREFIX \
 --target-os=android \
 --arch=$ARCH \
 --cpu=$CPU \
 --cc=$CC \
 --cxx=$CXX \
 --enable-cross-compile \
 --sysroot=$SYSROOT \
 --extra-cflags="-DVK_ENABLE_BETA_EXTENSIONS=0 -mno-stackrealign -Os -fpic $OPTIMIZE_CFLAGS" \
 --extra-ldflags="$ADDI_LDFLAGS" \
 $ADDITIONAL_CONFIGURE_FLAG
make clean
make -j4
make install
echo "The Compilation of FFmpeg for $CPU is completed"
}


 #armv8-a
 ARCH=arm64
 CPU=armv8-a
 CC=$TOOLCHAIN/bin/aarch64-linux-android$API-clang
 CXX=$TOOLCHAIN/bin/aarch64-linux-android$API-clang++
 SYSROOT=$TOOLCHAIN/sysroot
 CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
 PREFIX=$(pwd)/android/$CPU
 OPTIMIZE_CFLAGS="-march=$CPU"
 build_android


# 交叉编译工具目录,对应关系如下
# armv8a -> arm64 -> aarch64-linux-android-
# armv7a -> arm -> arm-linux-androideabi-
# x86 -> x86 -> i686-linux-android-
# x86_64 -> x86_64 -> x86_64-linux-android-

 # CPU架构
 #armv7-a
 ARCH=arm
 CPU=armv7-a
 CC=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang
 CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang++
 SYSROOT=$TOOLCHAIN/sysroot
 CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
 PREFIX=$(pwd)/android/$CPU
 OPTIMIZE_CFLAGS="-mfloat-abi=softfp -mfpu=vfp -marm -march=$CPU "
 build_android

 # #x86
 #ARCH=x86
 #CPU=x86
 #CC=$TOOLCHAIN/bin/i686-linux-android$API-clang
 #CXX=$TOOLCHAIN/bin/i686-linux-android$API-clang++
 #SYSROOT=$TOOLCHAIN/sysroot
 #CROSS_PREFIX=$TOOLCHAIN/bin/i686-linux-android-
 #PREFIX=$(pwd)/android/$CPU
 #OPTIMIZE_CFLAGS="-march=i686 -mtune=intel -mssse3 -mfpmath=sse -m32"
 #build_android

 # #x86_64
 #ARCH=x86_64
 #CPU=x86-64
 #CC=$TOOLCHAIN/bin/x86_64-linux-android$API-clang
 #CXX=$TOOLCHAIN/bin/x86_64-linux-android$API-clang++
 #SYSROOT=$TOOLCHAIN/sysroot
 #CROSS_PREFIX=$TOOLCHAIN/bin/x86_64-linux-android-
 #PREFIX=$(pwd)/android/$CPU
 #OPTIMIZE_CFLAGS="-march=$CPU -msse4.2 -mpopcnt -m64 -mtune=intel"
 # 方法调用
 #build_android



```

```java
# 这个原因是因为/后面有空格
Compiling FFmpeg for armv8-a
Unknown option "".
See ./configure --help for available options.
./build_android.sh: line 20: --disable-encoders: command not found
./build_android.sh: line 33: --enable-decoder=pcm_mulaw: command not found
./build_android.sh: line 35: --disable-parsers: command not found
./build_android.sh: line 41: --enable-muxer=h264: command not found
./build_android.sh: line 43: --enable-muxer=hevc: command not found
```



### 整合编译



#### fdk-acc整合编译

参考文献：[Android ndk(r22, clang)编译ffmpeg-4.2.1+fdk-aac+x264](https://zhuanlan.zhihu.com/p/342068431)

> 下载fdk-acc
>
> https://sourceforge.net/projects/opencore-amr/files/fdk-aac/   
>
> https://github.com/mstorsjo/fdk-aac/tags

![image-20230914150807396](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202309141508473.png)

选择下载人数最多的版本，这样遇到问题资料比较好找。

解压

```
[root@CentOS6 fdk-aac-2.0.2]# tar axvf fdk-aac-2.0.2.tar.gz
```

创建目录

```
mkdir output
```

获取绝对路径

```
[root@CentOS6 fdk-aac-2.0.2]# cd output && pwd && cd ..
/usr/local/src/ffmpeg5.1.3/fdk-aac-2.0.2/output
```



./configure --enable-static --host=arm-linux CC=/usr/local/linaro-aarch64-2020.09-gcc10.2-linux5.4/bin/aarch64-linux-gnu-gcc CXX=/usr/local/linaro-aarch64-2020.09-gcc10.2-linux5.4/bin/aarch64-linux-gnu-g++ --prefix=/usr/local/src/ffmpeg5.1.3/fdk-aac-2.0.2/output


编译脚本：

```
#!/bin/bash
# 这里需要替换成你本地的 NDK 路径，其他的不用修改
NDK=/usr/local/src/ffmpeg5.1.3/android-ndk-r25c 
HOST_TAG=linux-x86_64
TOOLCHAIN=$NDK/toolchains/llvm/prebuilt/$HOST_TAG
ANDROID_LIB_PATH="$(pwd)/android"

API=21

function build_android
{
echo "Build fdk-aac for android $CPU"
./configure \
--host=$HOST \
--disable-shared \
--enable-static \
--prefix="$ANDROID_LIB_PATH/$CPU" \
 CPPFLAGS="-fPIC"

make clean
make -j8
make install
echo "Build fdk-aac for android $CPU completed"
}

# armeabi-v7a
CPU=armv7-a
HOST=arm-linux-android
#export AR=$TOOLCHAIN/bin/arm-linux-androideabi-ar
##export AS=$TOOLCHAIN/bin/arm-linux-androideabi-as
###export LD=$TOOLCHAIN/bin/arm-linux-androideabi-ld
#export RANLIB=$TOOLCHAIN/bin/arm-linux-androideabi-ranlib
#export STRIP=$TOOLCHAIN/bin/arm-linux-androideabi-strip
export CC=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang
export CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang++
build_android

# arm64-v8a
CPU=armv8-a
HOST=aarch64-linux-android
#export AR=$TOOLCHAIN/bin/aarch64-linux-android-ar
#export AS=$TOOLCHAIN/bin/aarch64-linux-android-as
#export LD=$TOOLCHAIN/bin/aarch64-linux-android-ld
#export RANLIB=$TOOLCHAIN/bin/aarch64-linux-android-ranlib
#export STRIP=$TOOLCHAIN/bin/aarch64-linux-android-strip
export CC=$TOOLCHAIN/bin/aarch64-linux-android$API-clang
export CXX=$TOOLCHAIN/bin/aarch64-linux-android$API-clang++
build_android
```





```
#!/bin/bash
# 以下路径需要修改成自己的NDK目录
TOOLCHAIN=/usr/local/src/ffmpeg5.1.3/android-ndk-r25c/toolchains/llvm/prebuilt/linux-x86_64
# 最低支持的android sdk版本
API=21
# --extra-cflags中添加'-DVK_ENABLE_BETA_EXTENSIONS=0', 防止引用vulkan_beta.h头文件
function build_android
{
echo "Compiling FFmpeg for $CPU"
./configure \
 --prefix=$PREFIX \
 --enable-shared \
 --enable-cross-compile \
 --enable-protocol=file \
 --enable-jni \
 --enable-gpl \
 --enable-neon \
 --enable-pthreads \
 --disable-encoders \
 --enable-encoder=aac \
 --enable-encoder=png \
 --enable-encoder=libx264 \
 --enable-encoder=libx265 \
 --enable-encoder=gif \
 --enable-encoder=pcm_alaw \
 --enable-encoder=pcm_mulaw \
 --disable-decoders \
 --enable-decoder=h264 \
 --enable-decoder=hevc \
 --enable-decoder=aac \
 --enable-decoder=gif \
 --enable-decoder=pcm_alaw \
 --enable-decoder=pcm_mulaw \
 --disable-parsers \
 --enable-parser=h264 \
 --enable-parser=hevc \
 --enable-parser=aac  \
 --enable-parser=aac_latm  \
 --disable-muxers \
 --enable-muxer=h264 \
 --enable-muxer=hevc \
 --disable-hwaccels \
 --enable-mediacodec \
 --enable-hwaccel=h264_mediacodec \
 --enable-decoder=h264_mediacodec \
 --enable-decoder=hevc_mediacodec \
 --enable-decoder=mpeg4_mediacodec \
 --disable-bsfs \
 --enable-bsf=h264_metadata \
 --enable-bsf=h264_mp4toannexb \
 --enable-bsf=hevc_metadata \
 --enable-bsf=hevc_mp4toannexb \
 --enable-bsf=aac_adtstoasc \
 --enable-libfdk_aac \
 --enable-encoder=libfdk_aac \
 --enable-nonfree \
 --disable-filters \
 --disable-static \
 --disable-doc \
 --disable-htmlpages \
 --disable-manpages \
 --disable-podpages \
 --disable-txtpages \
 --disable-programs \
 --disable-ffmpeg \
 --disable-ffplay \
 --disable-ffprobe \
 --disable-avdevice \
 --disable-postproc \
 --disable-symver \
 --disable-indevs \
 --disable-outdevs \
 --disable-devices \
 --disable-asm \
 --cross-prefix=$CROSS_PREFIX \
 --target-os=android \
 --arch=$ARCH \
 --cpu=$CPU \
 --cc=$CC \
 --cxx=$CXX \
 --enable-cross-compile \
 --sysroot=$SYSROOT \
 --extra-cflags="-I$FDK_INCLUDE -DVK_ENABLE_BETA_EXTENSIONS=0 -mno-stackrealign -Os -fpic $OPTIMIZE_CFLAGS" \
 --extra-ldflags="-lm -L$FDK_LIB $ADDI_LDFLAGS" \
 $ADDITIONAL_CONFIGURE_FLAG
make clean
make -j4
make install
echo "The Compilation of FFmpeg for $CPU is completed"
}


 #armv8-a
 ARCH=arm64
 CPU=armv8-a
 CC=$TOOLCHAIN/bin/aarch64-linux-android$API-clang
 CXX=$TOOLCHAIN/bin/aarch64-linux-android$API-clang++
 SYSROOT=$TOOLCHAIN/sysroot
 CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
 PREFIX=$(pwd)/android/$CPU
 OPTIMIZE_CFLAGS="-march=$CPU"
 
 BASE_PATH=/usr/local/src/ffmpeg5.1.3
 # armv8-a  arm64-v8a
 LIB_TARGET_ABI=armv8-a
 
 #指定 fdk-aac 的头文件和静态库目录
 FDK_INCLUDE=$BASE_PATH/fdk-aac-2.0.2/android/$LIB_TARGET_ABI/include
 FDK_LIB=$BASE_PATH/fdk-aac-2.0.2/android/$LIB_TARGET_ABI/lib

 build_android


#第三方库
FDK_INCLUDE=$BASEPATH/fdk-aac/android/$CPU/include
FDK_LIB=$BASEPATH/fdk-aac/android/$CPU/lib

# 交叉编译工具目录,对应关系如下
# armv8a -> arm64 -> aarch64-linux-android-
# armv7a -> arm -> arm-linux-androideabi-
# x86 -> x86 -> i686-linux-android-
# x86_64 -> x86_64 -> x86_64-linux-android-

 # CPU架构
 #armv7-a
 ARCH=arm
 CPU=armv7-a
 CC=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang
 CXX=$TOOLCHAIN/bin/armv7a-linux-androideabi$API-clang++
 SYSROOT=$TOOLCHAIN/sysroot
 CROSS_PREFIX=$TOOLCHAIN/bin/llvm-
 PREFIX=$(pwd)/android/$CPU
 OPTIMIZE_CFLAGS="-mfloat-abi=softfp -mfpu=vfp -marm -march=$CPU "
 
 BASE_PATH=/usr/local/src/ffmpeg5.1.3
 #armv7-a
 LIB_TARGET_ABI=armv7-a
 
 #指定 fdk-aac 的头文件和静态库目录
 FDK_INCLUDE=$BASE_PATH/fdk-aac-2.0.2/android/$LIB_TARGET_ABI/include
 FDK_LIB=$BASE_PATH/fdk-aac-2.0.2/android/$LIB_TARGET_ABI/lib
 
 build_android



 # #x86
 #ARCH=x86
 #CPU=x86
 #CC=$TOOLCHAIN/bin/i686-linux-android$API-clang
 #CXX=$TOOLCHAIN/bin/i686-linux-android$API-clang++
 #SYSROOT=$TOOLCHAIN/sysroot
 #CROSS_PREFIX=$TOOLCHAIN/bin/i686-linux-android-
 #PREFIX=$(pwd)/android/$CPU
 #OPTIMIZE_CFLAGS="-march=i686 -mtune=intel -mssse3 -mfpmath=sse -m32"
 #build_android

 # #x86_64
 #ARCH=x86_64
 #CPU=x86-64
 #CC=$TOOLCHAIN/bin/x86_64-linux-android$API-clang
 #CXX=$TOOLCHAIN/bin/x86_64-linux-android$API-clang++
 #SYSROOT=$TOOLCHAIN/sysroot
 #CROSS_PREFIX=$TOOLCHAIN/bin/x86_64-linux-android-
 #PREFIX=$(pwd)/android/$CPU
 #OPTIMIZE_CFLAGS="-march=$CPU -msse4.2 -mpopcnt -m64 -mtune=intel"
 # 方法调用
 #build_android

```

#### libx264整合编译

#### libx265整合编译