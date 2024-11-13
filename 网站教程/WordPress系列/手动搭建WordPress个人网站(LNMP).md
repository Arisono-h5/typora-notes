你现在所见到的这个网站，是我用 WordPress 搭建的，整个过程非常的顺利，体验非常地好，于是我就整个过程、以及其中的一些搭建心得，记录下来。

![img](http://image.iswbm.com/20201015003006.png)

如果你也正好有搭建个人网站的想法，那么本文会给你一个参考，也许看了这篇文章你就可以不用再百度、甚至谷歌了，因为我会写得 **足够的细致而系统**。

本篇教程是**基于 LNMP搭建WordPress个人网站详细图文教程**。

另外基于宝塔面板搭建WordPress个人网站教程请参考：[基于宝塔面板搭建WordPress个人网站](https://www.yundashi168.com/42.html)

基于宝塔面板建站适合纯小白新手，基于LNMP适合有一定计算机基础的人士。但是两篇文章实践下来，两种方式本质都是一样的，都很简单。建议大家一定要多动手，多实践。

## 1. 写在前面

注意：文章为早期写的，iswbm.com 的站点已从 wordpress 转到当前的 hugo，下图为 wordpress 的效果

![img](http://image.iswbm.com/image-20201012232521149.png)

## 2. 准备工作

### 一台 Linux 服务器

在开始搭建网站之前，当然第一步是购买一个属于自己的 『服务器』。

你可以选择如下渠道进行购买：

- 阿里云
- 腾讯云
- Ucloud

等的大厂服务器，不要贪图便宜去买国外的服务器厂商，因为速度很慢很多，很影响体验。

我的就是在 [阿里云官网](https://www.aliyun.com/minisite/goods?userCode=ywqc0ubl) 上购买的，刚开始买个最低配置的服务器（1核2G或者2核2G的配置）就行，以后不够用了，可以慢慢升级，扩容。另外想要关注阿里云最新的促销活动，可以关注 [阿里云云小站](https://www.vpssw.com/aliyun/index)  官网的促销活动基本都在这里，可以帮助你省钱。

------

可以先领个券，再购买更实惠：[点击领券](https://www.vpssw.com/aliyun/index)

**今年的双11，我被阿里云邀请成为推广大使，他们给了我 100 台的免费服务器，需要的可以联系我（gitbaike ），闲着也是闲着，我可以免费送给大家。**

------



### 一个专属的域名

买了服务器后，你就会拥有一个公网ip，如果网站搭建起来了，你完全可以使用这个 ip 去访问，但仅供开发、测试使用。

如果要真正运营起来，想要有流量，还得搞一个域名，方便你推广。

域名的购买建议和上面服务器使用同一个厂商，可以省去一些麻烦。比如阿里云购买的域名要备案是需要你在阿里云下有一台服务器的。

### 一个远程登陆软件

由于后面我使用的是手工部署的方式，所以要登陆服务器进行操作。

登陆的方法有两种：

1. 厂商提供的控制台界面登陆：Workbench 和 VNC

   ![img](http://image.iswbm.com/image-20201007102912673.png)

   这种方法对于不经常登陆服务器运维的人来说，还是挺香的。

   ![img](http://image.iswbm.com/image-20201007103330062.png)

2. 自己下载专业的远程登陆软件：Xshell 或者 CRTSecure。这里推荐使用Xshell8 

   附 [Xshell8下载地址](http://share.vpssw.com/f/28426853-1382217892-025e38?p=7569)

   ![img](http://image.iswbm.com/20201015000746.png)

在使用这些远程登陆软件时，你需要在服务器厂商控制台上面先获取到三个信息

- 服务器公网IP
- 服务器SSH端口
- 服务器远程连接密码

关于 Xshell 如何使用的，可以自行百度搜索，教程非常多。

可以到阿里云上去购买，选最低配置就足够啦，后续访问量起来了再扩容升级。

## 2. 部署方式选择

部署方式，可分为两种

1. 使用服务器管理软件，实现自动化部署，最著名的就是 [宝塔面板](https://www.bt.cn/?invite_code=MV9la3hmaXo=) 。
2. 手动登陆远程服务器，实现脚本化部署。

**那么如何选择呢？**

使用宝塔部署，门槛低，只要会界面点一点即可。

而使用脚本自己手工部署，需要你学会

- 远程登陆服务器：使用 Xshell 或者 直接使用厂商提供的在线SSH窗口
- 一些 Linux 的基本操作：比如 Vi/Vim 的使用，目录及文件的基本操作等

在这里建议大家跟着我使用第二种方法，也就是手工使用脚本进行部署。

原因有二：

1. 第一次接触，更精细的部署步骤会让你对 WordPress 的运作方式有更深的理解，比如使用了哪些软件，装了哪些包？
2. 自己搭建了网站，难免以后会碰到各种各样的服务器问题，尽早的接触 Linux，熟悉各项配置，对以后的运维工作会有很有帮助。

## 3. 部署 LNMP

### 3.1 什么是 LNMP

LNMP 是 Linux + Nginx + MySQL + PHP 组合的简写。

类似的组合还有：

- LAMP 的全称是 Linux + Apache + MySQL + PHP
- LNAMP 的全称是 Linux + Nginx + Apache + MySQL + PHP

其中：

- Linux 是类 Unix 计算机操作系统的统称，是目前最流行的免费操作系统。代表版本有：debian、centos、ubuntu、fedora、gentoo 等。
- Nginx 是一个高性能的 HTTP 和反向代理服务器，也是一个 IMAP/POP3/SMTP 代理服务器。
- Apache 是世界使用排名第一的Web服务器软件。 它可以运行在几乎所有广泛使用的计算机平台上，由于其跨平台和安全性被广泛使用，是最流行的Web服务器端软件之一。
- PHP 是一种在服务器端执行的嵌入 HTML 文档的脚本语言。
- MySQL 是一个关系型数据库管理系统。

这些软件一个一个安装比较费力，特别是数据库。

因此有人把这些软件的安装部署过程集成为一个 Shell 脚本，而你只要下载并执行它就可以了。简直不要太方便。

### 3.2 安装 LNMP

下载 LNMP 安装脚本（目前最新版本是 1.7 ，我安装的是 1.5，更多版本可查看: https://lnmp.org/download.html）

```shell
$ wget http://soft.vpser.net/lnmp/lnmp1.5.tar.gz -cO lnmp1.5.tar.gz
```

解压并执行它

```shell
$ tar zxf lnmp1.5.tar.gz &amp;&amp; cd lnmp1.5 &amp;&amp; ./install.sh lnmp
```

接下来会出现大量的选项，如果你不是很懂各个选项间的区别，按默认就行啦

运行脚本后，首先会让你选择数据库的版本：

![img](http://image.iswbm.com/20201007104606.png)

没有特殊需要，建议使用默认配置，直接回车或输入序号再回车。

选好数据库，会让你设置数据库 root 用户的密码，此时如果你直接回车，会默认设置为 `lnmp.org#随机数字`，

![img](http://image.iswbm.com/20201007104643.png)

在输入密码的时候，对于新手有一点注意：如果输入有错误需要删除，需要按住Ctrl再按Backspace键进行删除。

密码输好后，回车进入下一步

![img](http://image.iswbm.com/20201007104714.png)

询问是否需要启用 MySQL InnoDB，InnoDB引擎默认为开启，一般建议开启，直接回车或输入 y 。

如果确定确实不需要该引擎可以输入 n，(MySQL 5.7+版本无法关闭InnoDB),输入完成，回车进入下一步：选择 PHP 版本，建议安装 PHP 7+的版本

![img](http://image.iswbm.com/20201007104727.png)

回车进入下一步，选择是否安装内存优化：

![img](http://image.iswbm.com/20201007105120.png)

可以选择不安装、Jemalloc或TCmalloc，输入对应序号回车，直接回车为默认为不安装。

如果是LNMPA或LAMP的话还会提示设置邮箱和选择Apache：

![img](http://image.iswbm.com/20201007105137.png)

“Please enter Administrator Email Address:”，需要设置管理员邮箱，该邮箱会在报错时显示在错误页面上。再选择Apache版本：

![img](http://image.iswbm.com/20201007105150.png)

按提示输入对应版本前面的数字序号，回车。

提示"Press any key to install…or Press Ctrl+c to cancel"后，按回车键确认开始安装。 LNMP脚本就会自动安装编译Nginx、MySQL、PHP、phpMyAdmin等软件及相关的组件。

安装时间可能会几十分钟到几个小时不等，主要是机器的配置网速等原因会造成影响。

如果显示Nginx: OK，MySQL: OK，PHP: OK

![img](http://image.iswbm.com/20201007105021.png)

表明安装成功。

最后几行的输出

- 3306 端口是 MySQL 监听的
- 80 是 HTTP 端口
- 22 是 SSH 端口

### 3.3 配置 Nginx

安装好后，使用如下指令查看nginx配置文件（如果你的服务器上找不到该文件，那请使用 `find / -name nginx.conf` 搜索一下）

```shell
$ cat /usr/local/nginx/conf/nginx.conf
```

你会看到如下内容：

![img](http://image.iswbm.com/20201007105202.png)

上图表明，安装好的nginx将网站的根目录设置为/home/wwwroot/default，这个可以根据自己的喜好进行修改。

用浏览器打开`http://ip`，可以看到如下内容：

![img](http://image.iswbm.com/20201007104831.png)

其实这就是一个简单的网页demo了，自己随便修改index.html，就会有不同的内容。

## 4. 安装 WordPress

[WordPress](https://iswbm.com/)是使用PHP语言（这也是我们上面为什么要安装 PHP 的原因）开发的博客平台，也就是一个博客框架。

上一步安装的 LNMP，只是保证了 WordPress 的基本运行环境。

想要把你的个人网站跑起来，咱还需要安装 WordPress 。

方法也很简单，下面跟着操作就行。

第一步：安装 wordpress 安装包并解压到 `/home/wwwroot`

```shell
$ wget https://cn.wordpress.org/latest-zh_CN.zip &amp;&amp; unzip latest-zh_CN.zip -d /home/wwwroot
```

第二步：登录MySQL（密码在前面 部署LNMP 时你设置过），创建wordpress表，创建完后输入exit退出。

```shell
$ mysql -u root -p
Enter password: 
MySQL > create database wordpress;
```

第三步：使用 vim 修改 nginx 配置文件（不会vim的自行百度）

```shell
$ vim /usr/local/nginx/conf/nginx.conf
```

找到网站根目录位置，如下图所示：

![img](http://image.iswbm.com/20201007110554.png)

修改成如下内容：

![img](http://image.iswbm.com/20201007110611.png)

随后，使用wq保存配置退出即可。

验证nginx是否有配置错误：

```shell
$ nginx -t
```

如果出现ok，successful字样，说明没有错误。没有错误，重新加载nginx：

```shell
$ nginx -s reload
```

修改wordpress目录权限：

```shell
$ cd /home/wwwroot &amp;&amp; chown -R www wordpress/ &amp;&amp; chgrp -R www wordpress/
```

用浏览器打开http://ip/wp-admin/setup-config.php，你可以看到如下内容：

![img](http://image.iswbm.com/20201007110628.png)

现在就开始，进行安装。填写信息如下：

![img](http://image.iswbm.com/20201007110649.png)

其中，*** 改为你设置的MySQL数据库密码。点击提交，出现如下内容：

![img](http://image.iswbm.com/20201007110709.png)

在/home/wwwroot/wordpress下，创建并编写wp-config.php文件：

```shell
$ vim wp-config.php
```

将上图内容复制进去并wq保存退出，然后点击现在安装。最后就是配置用户信息了，这个是你登录wordpress用户后台的，要记住：

![img](http://image.iswbm.com/20201007110841.png)

最后点击安装WordPress，安装成功会出现如下界面：

![img](http://image.iswbm.com/20201007110859.png)

点击登录，输入账户密码，就可以登录自己的 wordpress 后台了。

![img](http://image.iswbm.com/image-20201014205746752.png)

这时候你使用浏览器去访问 http://ip ，就可以看到你搭建的第一个网站了。

此时你看到的这个网站，是 wordpress 默认为你安装的免费主题（应该有三个），可能并不是那么的好看，但没关系，后面我会教大家如何挑选一个自己合适的主题，把你的网站装扮得有模有样。

## 5. 装扮你的网站

到这里，你的网站部署已经全部完成，但是还差最后一步，也是使用 WordPress 最为核心的一步：让你的网站看起来更加专业，更加成熟。

为此我们需要做两件事：

1. 安装主题：让网站变得好看
2. 安装插件：丰富网站的功能

### 5.1 安装主题

同样都使用的 WordPress 的网站，外观上却天差地别。有的很酷炫，有点很简约，这是因为选了不同的主题（可以理解为皮肤）。

在你安装完 WordPress 后，本身就自带了几个免费的主题。

几乎没人会使用它们，因为实在没什么亮点（就是丑）。

在 WordPress 的自带了主题商店，里面有大量的免费主题，各式各样的都有，可能有你喜欢的。

![img](http://image.iswbm.com/image-20201014210919205.png)

在这里要说明一点，我的主题不是在商店里安装的，而是我通过搜索引擎找到了一个比较清爽的主题，很符合我的审美，我装扮过后的效果如下。

![img](http://image.iswbm.com/image-20201007112159757.png)

如果你想和我用一样的主题，我已经将安装包打包好了（需要的添加我微信领取: stromwbm），直接下载后，按下图的方式上传到你的 WordPress 后台安装就行。

![img](http://image.iswbm.com/image-20201007112442478.png)

### 5.2 安装插件

目前我安装的插件比较少，但是基本够用啦，下面列举一下，如果你有什么好插件介绍，可以评论区推荐一下：

**1. WP User Avatar**

原生 WordPress 默认使用 Gravatar头像，用户（包括访客评论）的头像调取都是根据所留邮箱匹配的 Gravatar 头像。

没有 Gravatar 怎么办？

只要装上 `WP User Avatar` 这个插件就能可以使用 WordPress 媒体库中的图片作为默认头像了。

**2. WP-PostViews**

安装了 WP-PostViews，就可以统计你文章的浏览次数。

需要两步配置

第一步：设置显示的文字

![img](http://image.iswbm.com/image-20201014220218693.png)

第二步：在你要显示的位置写入如下代码

![img](http://image.iswbm.com/image-20201014220510843.png)

效果如下

![img](http://image.iswbm.com/image-20201014220652829.png)

**3. Post Views Counter**

咦，上面已经安装了一个统计阅读量的插件，怎么这边又推荐一个。

上面那个统计阅读量的插件，其实做的比较粗糙。

这是什么意思。

比如同一个 ip 连续连刷10次，WP-PostViews 的阅读量会 `+10`，但如果你使用 Post Views Counter，这个规则可以由你来定，可以只显示一次。

![img](http://image.iswbm.com/image-20201014214127315.png)

安装完这个插件后，同样需要进行一些配置

![img](http://image.iswbm.com/image-20201014214110056.png)

为什么这里选择手动呢？

![img](http://image.iswbm.com/image-20201014214217099.png)

因为我发现不管在内容之前，还是在内容之后，显示的位置都比较尴尬（它会换行）。

如果你和我用一样的主题，想和我有一样的效果，那么你选择**手动**之后，还要按下图指示修改下代码，新增如下一段代码。

![img](http://image.iswbm.com/image-20201014214436969.png)

效果如下

![img](http://image.iswbm.com/image-20201014213834821.png)

**4. WP Editor.md**

或许这是一个WordPress中最好，最完美的Markdown编辑器。

可以像 md2all 和 mdnice 那样，即时显示 Markdown 的渲染效果，喜欢在后台写文章的可以安装（其实我是先本地 Typora 写好了再复制上去的）。

![img](http://image.iswbm.com/image-20201014221844359.png)

**5. Simple Custom CSS**

在修改 WordPress主题时，CSS修改是最经常用到的方法，比如调整字体、调整颜色、边距之类的都需要用到自定义的CSS代码。

虽然说 WordPress 本身提供了CSS修改的功能，不过使用起来有很多的弊端，其中最麻烦的一点就是每次更换或者更新主题之前的修改都会消失，需要重复的添加。

使用 `Simple Custom CSS` 这个插件可以避免这种尴尬，安装后他会在 `外观` 下新增一个 `自定义CSS` 的选项。

![img](http://image.iswbm.com/image-20201014213322238.png)

**6. LuckyWP Table of Contents**

使用我这个主题，在文章页面是没有目录索引的，对于读者来说，其实挺不方便的。

因此我安装了 LuckyWP Table of Contents，可以在我的文章中生成一个目录。目录默认是隐藏的（当然你也可以设置默认展示），需要的话再点击展开。

![img](http://image.iswbm.com/image-20201014214735971.png)

点击目录可以直接跳转到对应位置。

但可能是我这个主题的原因，我的网站无法跳转，如果有人知道原因，还请留言区评论一下。

**7. 百度搜索推送管理**

百度搜索推送管理插件是一款针对WP开发的功能非常强大的百度和Bing搜索引擎收录辅助插件。

利用该插件，站长可以快速实现百度搜索资源平台和Bing站长平台URL数据推送及网站百度收录数据查询等。

目的在于进一步提升网站的百度和Bing搜索引擎收录效率，提升网站SEO优化效果；及帮助站长通过该插件了解网站百度收录数据情况，基于数据统计参考进一步对网站内容进行调整与优化。

具体使用方法比较复杂，自己百度一下吧

**8. Smart SEO Tool**

Smart SEO Tool是一款专门针对WordPress开发的智能SEO优化插件，与众多WordPress的SEO插件不一样的是，Smart SEO Tool更加简单易用，帮助站长快速完成WordPress博客/网站的SEO基础优化。

我在生成 sitemap 时，报这个错误

![img](http://image.iswbm.com/20210112140017.png)

Google 了半天，网上说的解决方法有很多，但是好像对我没啥用。

最后我无意中发现在你的主题目录下的 `functions.php` 文件最后多了很多空格，于是就把这些空格给清理了下，没想到还真的好了。
![img](http://image.iswbm.com/20210112140423.png)

## 6. 优化你的网站

### 6.1 使用固定链接

先在后台按如下图示进行设置

![img](http://image.iswbm.com/image-20201014222135425.png)

但是这样不够，要使用固定链接，服务器还需要开启 rewrite 的功能。

如果你和我使用的是 nginx ，那么只要登陆服务器，在

`/usr/local/nginx/conf/nginx.conf` 里的 server 里加上这一段（我放在倒数第二段）

```
location / {
		if (!-e $request_filename) {
				rewrite (.*) /index.php;
		}
}
```

然后重启一下 nginx

```shell
$ systemctl restart nginx
```

### 6.2 网站添加备案号

如果你的域名已经备案了，最好将你的备案号放到底部（好像会有检查）。

![img](http://image.iswbm.com/image-20201014224157459.png)

### 6.3 美化文章的排版

一个好的排版，能够极大提升阅读体验，因此定制一个好的排版非常有必要。

```css
#write a.md-toc-inner {
    line-height: 1.6;
    white-space: pre-line;
    border-bottom: none;
}

#write a:hover {
    border-bottom: 2px solid #f22f27;
    color: #cc1616;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    position: relative;
    margin-top: 1rem;
    margin-bottom: 1rem;
    font-weight: bold;
    line-height: 1.4;
    cursor: text;
}

h1:hover a.anchor,
h2:hover a.anchor,
h3:hover a.anchor,
h4:hover a.anchor,
h5:hover a.anchor,
h6:hover a.anchor {
    text-decoration: none;
}

h1 tt,
h1 code {
    font-size: inherit !important;
}

h2 tt,
h2 code {
    font-size: inherit !important;
}

h2.uptop {
	border-bottom: 1px green;
}


.uptop::before {
    content: ' '!important;
    color: #f22f27;
}

h3 tt,
h3 code {
    font-size: inherit !important;
}

h4 tt,
h4 code {
    font-size: inherit !important;
}

h5 tt,
h5 code {
    font-size: inherit !important;
}

h6 tt,
h6 code {
    font-size: inherit !important;
}

h2 a,
h3 a {
    color: #34495e;
}


h2 {
    margin: 2em auto 1.4em;
    /* padding-left: 10px; */
    /* display:inline-block; */
    line-height: 1.4;
    font-size: 1.8em;
    /* border-left: 9px solid var(--main-6); */
    /* border-bottom: 1px solid #ddd; */
    border-bottom: 1px solid #f22f27;
}

h2::before {
    content: '# '!important;
    color: #f22f27;
}

h3 {
    font-size: 1.4em;
    line-height: 1.43;
    margin: 1.6em auto 1.2em;
    padding-left: 9px;
    border-left: 5px solid #f22f27;
}


/* 三级四级标题点击后左边的提示图标 */

#write>h3.md-focus:before,



/* 引用文字 */
.view-content blockquote p {
    color: #353535;
    font-size: 16px;
    margin: 0 10px;
    display: block;
}

.view-content .blockquote:after {
    content: "”";
    float: right;
    display: block;
    font-size: 2em;
    color: rgb(248, 57, 41);
    font-family: Arial, serif;
    line-height: 1em;
    font-weight: 700;
}

/* 二维码显示 */
header .gongzhonghao {
    color: #fff;
    font-size: 14px;
    position: absolute;
    bottom: 30px;
}

header .weixinhao {
    color: #fff;
    font-size: 14px;
    position: absolute;
    bottom: 180px;
}


/* 表格样式 */
table {
    padding: 0;
    word-break: initial;
}

table tr {
    border-top: 1px #f22f27;
    margin: 0;
    padding: 0;
}

table tr:nth-child(2n),
thead {
    background-color: #fafafa;
}

table tr th {
    font-weight: bold;
    border: 1px solid #f22f27;
    border-bottom: 0;
    text-align: left;
    margin: 0;
    padding: 6px 13px;
}

table tr td {
    border: 1px solid #f22f27;
    text-align: left;
    margin: 0;
    padding: 6px 13px;
}

table tr th:first-child,
table tr td:first-child {
    margin-top: 0;
}

table tr th:last-child,
table tr td:last-child {
    margin-bottom: 0;
}

/* 代码框 */
#write .md-fences {
    border: 1px solid #7a7a7a;
    -webkit-font-smoothing: initial;
    margin: 2rem 0 !important;
    /* padding: 0.3rem 0 !important; */
    padding: 3px 5px;
    line-height: 1.55rem;
    border-radius: 10px;
    font-family: 'Roboto Mono', 'Source Sans Pro', 'Microsoft YaHei', '微软雅黑' !important;
    font-size: 0.9rem;
    word-wrap: normal;
}

#write [mdtype="math_block"] {
    font-size: 1.2rem;
}

#write .CodeMirror-wrap .CodeMirror-code pre {
    padding-left: 12px;
    line-height: 1.55rem;
}

.cm-s-inner .CodeMirror-linenumber {
    width: 2ch !important;
    color: rgba(128, 128, 255, 0.8);
}

#write .CodeMirror-cursors .CodeMirror-cursor {
    border-left: 2px solid #ff887a;
}
```

进入 WP Editor.md 插件配置文章的 markdown 渲染：

**第一：开启目录**

![img](http://image.iswbm.com/20210618085435.png)

安装完 Table of Contents Plus 插件后，可以设置目录的显示位置

![img](http://image.iswbm.com/20210618085803.png)

**第二：设置代码主题**

![img](http://image.iswbm.com/20210618085544.png)

### 6.4 部署 HTTPS

关于如何部署 HTTPS ，我在之前的文章里讲过一种。

今天再介绍另外一种：使用宝塔。

注册并登陆宝塔（https://bt.cn），然后进入控制面板，进行实名认证。

![img](http://image.iswbm.com/image-20200929123223096.png)

点击申请证书

![img](http://image.iswbm.com/image-20200929123355037.png)

选择免费的就好

![img](http://image.iswbm.com/image-20200929123418789.png)

填写你的域名后，支付订单（其实不要钱）。

![img](http://image.iswbm.com/image-20200929123459545.png)

然后点击详情，需要验证该域名是归你所有。

方法它会告诉你，登陆我的阿里云域名解析，根据如下提示去添加 DNS解析规则

![img](http://image.iswbm.com/image-20200929123956070.png)

然后静待一段时间验证成功了，就可以点击如下按钮，下载数据证书。![img](http://image.iswbm.com/image-20200929194100905.png)

下载到本地后，你会得到一个 zip 包，解压一下，就可以看到证书文件及私钥。

![img](http://image.iswbm.com/image-20200929201114297.png)

因为我的博客使用的是 Nginx，因此我该 Nginx 下的两个文件上传到我的服务器上的 nginx 目录下.

具体怎么上传呢？你可以使用远程拷贝软件，例如 WinSCP，也可以使用 `lrzsz` （推荐使用）。

传到哪个目录下呢？

先使用 find 命令查找一下你的 nginx.conf 路径

```shell
$ find / -name nginx.conf
/usr/local/nginx/conf/nginx.conf
```

你的证书文件可以和 nginx.conf 放在同一目录下

```shell
/usr/local/nginx/conf
```

接下来使用 vim 编辑该文件，找到 server，添加如下行（ server 原本的内容 我使用 `...` 表示，意思是不需要去动。 ）

```shell
server
    {
        listen 443 ssl;
        # 注释掉该行
				# listen 80 default_server reuseport;

        #证书文件名称
        ssl_certificate 1_iswbm.com_bundle.pem;
        #私钥文件名称
        ssl_certificate_key 0_iswbm.com.key;

				...
    }
```

最后重启 nginx

```shell
$ systemctl restart nginx
```

尝试用 https 访问一下我的网站 `https://iswbm.com`，非常顺利。

![img](http://image.iswbm.com/image-20201014223409827.png)

到这里，事情其实还没有结束，你还需要做两件事情：

**第一件事**：在后台进行一些配置，不然从网站跳转的时候还是会使用 http

![img](http://image.iswbm.com/image-20201014223547198.png)

**第二件事**：将 http 重定向到你 https，不然有人在浏览器输入 iswbm.com 时，访问的还是 http。

使用 vim 编辑 /usr/local/nginx/conf/nginx.conf，在原本 server 的前面加入下面这么一段代码

```
server {
        listen 80;
        server_name iswbm.com;
        rewrite ^(.*) https://$server_name$1 permanent;
        }
```

然后再重启 nginx

```shell
$ systemctl restart nginx
```

### 6.5 图床开启HTTPS

由于我之前的 markdown 文章，使用的图床都是 七牛云，当时并没有开启 https，现在网站开启了 https 后，自然图片也要开启，不然浏览器会显示有部分不安全的资源。

登陆七牛云，然后进入 [证书管理](https://portal.qiniu.com/certificate/ssl ) 上传证书（注意这个证书得另外申请，不能使用先前申请的 iswbm.com 证书）。

![img](http://image.iswbm.com/image-20200929210645477.png)

进入对象存储 -> 域名管理，找到 HTTPS 配置的位置，点击 `修改配置`。

![img](http://image.iswbm.com/image-20200929205400898.png)

将按钮置为开启状态，选择我们刚刚上传的证书。

![img](http://image.iswbm.com/image-20200929205611442.png)

设置完后，并不能立马使用

![img](http://image.iswbm.com/image-20200929210431735.png)

域名的升级需要一定时间，等待即可。

![img](http://image.iswbm.com/image-20200929210900562.png)

以上就是我搭建网站的全部总结，写了两个晚上，直到昨晚才完成。