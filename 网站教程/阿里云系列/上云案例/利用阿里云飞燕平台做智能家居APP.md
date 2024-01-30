最近飘易开发完成了一款利用阿里云飞燕平台实现智能家居控制的APP项目，在实现的过程中有一些心得体会，把它总结记录下来，供自己和感兴趣的朋友日后参考。



先总体来说一下架构的事，飘易做的这款APP最终要控制的是家里的门窗，通过APP调用阿里云飞燕平台实现家里门窗的开、关、锁（支持百分比的开关），那这里就涉及到了硬件、平台、APP端。



**硬件**

硬件方面，智能设备需要上网，连接阿里云，那么就需要选择对应的上网模组，我们项目里选择了庆科的

EMW3080的wifi模组，EMW3080是单3.3V供电的、集成Wi-Fi和Cortex-M4F MCU的嵌入式Wi-Fi模块，最高支持133M主频和256K RAM，强大的浮点运算，分为A（硬件加密版）/B（标准版）2个版本。

![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401271053728.png)

我们选择的是 EMW3080（BP）标准版、PCB天线。



wifi模组选择之后，要对接的是控制门窗开关的电机厂商，电机的mcu需要和wifi模组进行对接，将阿里云平台的发送的指令执行下去，以及mcu需要将门窗的状态及时反馈给阿里云平台，这里涉及到的是硬件开发的事，咱略过不谈。



知识点：**SecureCRT软件怎么刷飞燕平台的AT固件到设备里**

[http://docs.mxchip.com/#/docs/AT/3.%E9%80%9A%E7%94%A8%E6%8C%87%E4%BB%A4%E4%BD%BF%E7%94%A8%E7%94%A8%E4%BE%8B](http://docs.mxchip.com/#/docs/AT/3.通用指令使用用例)



如何通过模块用户串口，在boot模式下，烧录bin文件？



准备：

PC端安装软件：SecureCRT。

模块相关连线操作：模块上电，并通过“TTL转USB小板”，将用户串口接至PC端USB口，并打开该端口。



烧 all.bin:

1.用户串口，进boot模式，方法：boot拉低，按下RESET按键，波特率：921600bps

2.输入命令: 4 -dev 1 回车，菜单栏选择 Transfer -> Send ymodem，选择 all.bin, 更新即可。

3.调到产测模式，用户串口，921600bps，输入#，按下Reset按键，进QC log,确认固件版本及CRC值。



注意：银尔达小板，直接连接板上现成的usb接口（已经ttl转过了）。开发版大家可以买淘宝上的《银尔达EMW3080物联网WiFi核心板 USB转串口开发板2.4g无线模块》，链接就不放了，大家自行搜索吧，这家的技术支持还行。

![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401271053531.png)



知识点：**如何利用格西烽火软件烧录设备四元组信息**

TTL转USB小板（以下简称ttl板）rx接开发板的tx，ttl板tx接开发板的rx（交叉接线）

两种供电：

1，ttl板3.3v接开发板的3.3v，ttl板的gnd接开发板的gnd（地）；

2，调试串口usb接电脑的usb；



波特率115200bps



文档：

链接1：[http://docs.mxchip.com/#/docs/AT/4.%E7%9B%B4%E8%BF%9Eilop%E9%98%BF%E9%87%8C%E9%A3%9E%E7%87%95%E4%BA%91%E5%B9%B3%E5%8F%B0%E6%8C%87%E5%8D%97](http://docs.mxchip.com/#/docs/AT/4.直连ilop阿里飞燕云平台指南)

链接2：[http://docs.mxchip.com/#/docs/AT/2.%E6%8C%87%E4%BB%A4%E8%AF%B4%E6%98%8E?id=atilopstop](http://docs.mxchip.com/#/docs/AT/2.指令说明?id=atilopstop)



通过 AT 指令烧录至模组中，具体参见指令：AT+ILOPSET,需要设置的参数包括 ：

AT+ILOPSET=<product_key>,<product_secret>,<device_secret>,<device_name>\r







**平台**

云端平台选择的是阿里云智能生活平台：[https://living.aliyun.com/](https://help.aliyun.com/product/123207.html#index.html?source=5176.11533457&userCode=ywqc0ubl ) 。除了阿里云的物联网平台，其实市面上还有挺多家其他的，比如机智云、百度天工智能物联网平台、腾讯QQ物联智能硬件开放平台、移动OneNET平台、京东智能云、庆科云FogCloud等，具体怎么选择，就要看项目的需求和甲方的意向了。



除了选择市面上常见的平台外，如果项目规模可控，我们还有其他的选择，可以自建云端，灵活性更高，但成本要略高的。



阿里云生活物联网平台的文档开发前一定要仔细的阅读：[https://living.aliyun.com/doc#index.html](https://help.aliyun.com/product/123207.html#index.html?source=5176.11533457&userCode=ywqc0ubl)（官网技术文档，一定要查看清楚）



![img](http://www.piaoyi.org/upimg/file071127_08/02/201915112459.png)

阿里云平台架构如上图



需要留意的是阿里云在产品量产之后需要为每个产品购买一个设备激活码，费用是2.8元一个，按每台设备数收费（设备日均上下行消息数小于3000条）。

> 如果贵公司还需要用到阿里云的服务器，云数据库，Redis数据库，消息中间件，短信或者其它任何云产品，都可以先点击领取  [阿里云专属内部优惠券](https://www.aliyun.com/activity?source=5176.11533457&userCode=ywqc0ubl)  (很多人还不知道阿里云有内部代金券,领取可减免不少现金)
>
> 这个内部代金券是云产品通用红包，可以叠加官网常规优惠使用。这个代金券是新用户专享的，如果你还没有注册阿里云账号，可以先[注册阿里云账号](https://help.aliyun.com/zh/account/user-guide/ali-cloud-account-registration-process?source=5176.11533457&userCode=ywqc0ubl)，然后再领取这个代金券。注册账号需要实名认证，请参考官方文档：[阿里云账号注册流程说明](https://help.aliyun.com/zh/account/user-guide/ali-cloud-account-registration-process?source=5176.11533457&userCode=ywqc0ubl)



**APP端开发**

阿里云智能生活开放平台自带了免开发的公版APP，所有接入阿里云平台的设备厂商都可以共用这个APP，这个公版APP“智能家居”，不带特殊品牌。



公版APP用途：

- 适合对个性化和差异化要求较低的客户。该方案完全免开发，您只需进行硬件端的开发，无需开发云端、PC端或App端，即可快捷、低成本地交付一套完整解决方案。将该APP二维码直接印刷在商品说明书上，消费者即可直接扫码下载，快速使用您的智能设备。
- 用于调试设备、模组，在自己的品牌APP尚未完成前，可以验证设备的配网、控制、OTA链路是否正常。



自有品牌APP（需开发）：

- 适合希望定制化自己的品牌APP，自己去开发各种个性化功能和业务逻辑的客户。

其中物联的部分，可以基于平台提供的SDK、API和插件，对产品进行配网、控制和场景自动化配置。


我们在项目中选择的是自有品牌APP开发，因为客户需要定制较多个性化的界面。



在开发之前，下载官方提供的demo，是一个比较好的方式，当自己开发过程中遇到一些门槛的时候，看看demo的实现方式可以节省一些思考的时间。



本文重点说的也是APP开发过程中遇到的一些问题。



**安卓版**



首先需要集成的是安全图片，下载后的安全图片的文件名为 yw_1222_xxxx.jpg ,请放到工程根目录,如下图所示

1、安全图片，请放置于Android工程目录中的 res/drawable 下

![img](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202401271053616.png)



2、签名配置, 因为 Android 端上，安全图片是需要和签名搭配使用的，所以要正确的配置签名：

```
android{
    signingConfigs {
        debug {
            storeFile file("./debug.keystore")
            storePassword '123456'
            keyAlias 'android'
            keyPassword '123456'
        }
    }
    buildTypes{
        debug {
            signingConfig signingConfigs.debug
        }
    }
}
```



然后就是按部就班的集成各种SDK，下面的6个SDK是必须集成的：

1. API 通道 SDK
2. 长连接通道 SDK
3. 账号及用户 SDK
4. BoneMobile 容器 SDK
5. 身份认证 SDK
6. 配网 SDK



还有2个SDK是可选的，如果项目里用到就集成：

1. 移动应用推送 SDK
2. 设备模型 SDK



飘易就直接放出集成的实例代码，请留意我使用的是HTML 5+ SDK 离线打包的方式，就是把iot所有的功能封装成一个库，抛给上层的js调用（http://ask.dcloud.net.cn/article/103）：



```
package com.plugin.ilop;
import ...

public class ilop extends StandardFeature
{
    String TAG = "iLOP";
    android.content.Context curContext;
    private static final String app_key = "25263xxx";// 从飞燕平台获取
    // 长连接通道使用的全局变量
    IWebview pWebviewLong;
    String CallBackIDLong;

    public void onStart(Context pContext, Bundle pSavedInstanceState, String[] pRuntimeArgs) {
        /**
         * 如果需要在应用启动时进行初始化，可以继承这个方法，并在properties.xml文件的service节点添加扩展插件的注册即可触发onStart方法
         * <service name="ilop" value="com.plugin.ilop.ilop"/>
         * */
        Log.w(TAG, "ilop onStart");
        curContext = pContext;
        // 阿里云sdk初始化
        sdk_init();
    }

    // API通道SDK 初始化
    private void api_init(){
        // 初始化无线保镖
        android.content.Context app = curContext;
        try {
            SecurityInit.Initialize(app);
        } catch (JAQException ex) {
            Log.w(TAG, "security-sdk-initialize-failed");
        } catch (Exception ex) {
            Log.w(TAG, "security-sdk-initialize-failed");
        }
        // 初始化 IoTAPIClient
        IoTAPIClientImpl.InitializeConfig config = new IoTAPIClientImpl.InitializeConfig();
        // 国内环境
        config.host = "api.link.aliyun.com";
        // 海外环境，请参考如下设置
        //config.host = “api-iot.ap-southeast-1.aliyuncs.com”;
        config.apiEnv = Env.RELEASE; //只支持RELEASE
        IoTAPIClientImpl impl = IoTAPIClientImpl.getInstance();
        impl.init(app, config);
    }

    // 账号和用户SDK 初始化
    private void login_init(){
        android.content.Context app = curContext;
        //如果com.aliyun.iot.aep.sdk:account 为0.0.2以及以上，请使用如下代码完成初始化
        OALoginAdapter adapter = new OALoginAdapter(app);
        //如果需要切换到海外环境，请执行下面setDefaultOAHost方法，默认为大陆环境
        //adapter.setDefaultOAHost("sgp-sdk.openaccount.aliyun.com");
        adapter.init("online","114d");
        LoginBusiness.init(app, adapter, "online");

        //打开调试，会有详细日志输出
        OpenAccountSDK.turnOnDebug();
    }

    // BoneMobile容器SDK 初始化
    private void bonemobile_init(){
        String serverEnv = "production";//仅支持"production",即生产环境
        String pluginEnv = "release";//仅支持“release”
        String language = "zh-CN";//语言环境，目前仅支持“zh-CN”，“en-US”
        android.content.Context app = curContext;
        // 初始化 BoneMobile RN 容器
        InitializationHelper.initialize(app, pluginEnv, serverEnv, language);
        // 添加基于 Fresco 的图片组件支持
        RNGlobalConfig.addBizPackage(new FrescoPackage());

        //集成账号能力
        BonePluginRegistry.register(BoneUserAccountPlugin.API_NAME, BoneUserAccountPlugin.class);
        //集成设备模型能力
        BonePluginRegistry.register("BoneThing", BoneThing.class);
        //集成配网能力
        BonePluginRegistry.register("BoneAddDeviceBiz",BoneAddDeviceBiz.class);
        BonePluginRegistry.register("BoneLocalDeviceMgr",BoneLocalDeviceMgr.class);
        BonePluginRegistry.register("BoneHotspotHelper",BoneHotspotHelper.class);
        //集成长连接能力
        BonePluginRegistry.register("BoneChannel", BoneChannel.class);
    }

    // 长连接-下行通道监听器
    private IMobileDownstreamListener listener = new IMobileDownstreamListener() {
        @Override
        public void onCommand(String method, String data) {
            Log.w(TAG,"接收到Topic="+method+", data="+data);
            try {
                String json = "{\"topic\":\""+method+"\",\"data\":"+data+"}";
                JSONObject obj = new JSONObject(json);
                JSUtil.execCallback(pWebviewLong, CallBackIDLong, obj, JSUtil.OK, true);//回调通知js层，最后一个参数true，持续输出
            } catch (JSONException e) {
                Log.w(TAG, e.getMessage());
            }
        }
        @Override
        public boolean shouldHandle(String method) {
            // method 即为Topic，如果该Topic需要处理，返回true后onCommand才会回调。
            return true;
        }
    };

    // 长连接通道sdk-绑定用户账号
    private void long_bind(){
        // 长连接通道与账号绑定, 绑定前需要确认账号已经登录
        //String iotToken = IoTCredentialManageImpl.getInstance((Application) curContext).getIoTToken();
        //Log.w(TAG, "iotToken:"+iotToken);
        IoTCredentialManage ioTCredentialManage = IoTCredentialManageImpl.getInstance((Application) curContext);
        if (ioTCredentialManage != null) {
            final String[] iotToken = {ioTCredentialManage.getIoTToken()};
            if(iotToken[0].isEmpty()) {
                // 调用异步刷新接口重新获取用户认证信息
                ioTCredentialManage.asyncRefreshIoTCredential(new IoTCredentialListener() {
                    @Override
                    public void onRefreshIoTCredentialSuccess(IoTCredentialData ioTCredentialData) {
                        Log.w(TAG, "refresh IoTCredentailData success :" + ioTCredentialData.toString());
                        iotToken[0] = ioTCredentialData.iotToken;
                        // 绑定账号
                        MobileChannel.getInstance().bindAccount(iotToken[0], new IMobileRequestListener() {
                            @Override
                            public void onSuccess(String jsonData) {
                                Log.w(TAG, "bindAccount ok");
                            }
                            @Override
                            public void onFailure(AError error) {
                                Log.w(TAG, "bindAccount fail");
                            }
                        });
                    }
                    @Override
                    public void onRefreshIoTCredentialFailed(IoTCredentialManageError ioTCredentialManageError) {
                        Log.w(TAG, "refresh IoTCredentailData failed ");
                        if (ioTCredentialManageError != null) {
                            Log.w(TAG, "error code is:" + ioTCredentialManageError.errorCode);
                        }
                    }
                });
            }else{
                // 绑定账号
                MobileChannel.getInstance().bindAccount(iotToken[0], new IMobileRequestListener() {
                    @Override
                    public void onSuccess(String jsonData) {
                        Log.w(TAG, "bindAccount ok");
                    }
                    @Override
                    public void onFailure(AError error) {
                        Log.w(TAG, "bindAccount fail");
                    }
                });
            }
        }
    }
    // 长连接通道sdk- 解除绑定用户账号
    private void long_unbind(){
        // 取消长连接通道与账号关联 - 取消关联需要在用户退出前进行操作
        MobileChannel.getInstance().unBindAccount(new IMobileRequestListener() {
            @Override
            public void onSuccess(String s) {
                Log.w(TAG, "unBindAccount ok");
            }
            @Override
            public void onFailure(AError aError) {
                Log.w(TAG, "unBindAccount fail");
            }
        });
    }

    // 长连接通道SDK 初始化
    private void long_link_init(){
        //打开Log 输出
        //ALog.setLevel(ALog.LEVEL_DEBUG);
        MobileConnectConfig config = new MobileConnectConfig();
        // 设置 appKey 和 authCode(必填)
        config.appkey = app_key;
        config.securityGuardAuthcode = "114d";//设置安全图片的auth code
        // 设置验证服务器（默认不填，SDK会自动使用“API通道SDK“的Host设定）
        //config.authServer = "";
        // 指定长连接服务器地址。 （默认不填，SDK会使用默认的地址及端口。默认为国内华东节点。）
        //config.channelHost = "{长连接服务器域名}";
        // 开启动态选择Host功能。 (默认false，海外环境建议设置为true。此功能前提为ChannelHost 不特殊指定。）
        config.autoSelectChannelHost = false;

        //先取消之前的监听
        //MobileChannel.getInstance().unRegisterDownstreamListener(listener);

        // 开始连接
        MobileChannel.getInstance().startConnect(curContext, config, new IMobileConnectListener() {
            @Override
            public void onConnectStateChange(MobileConnectState mobileConnectState) {
                Log.w(TAG, "长连接通道状态变化，MobileConnectState=" + mobileConnectState);
                if(mobileConnectState == MobileConnectState.CONNECTED){
                    // 长连接通道sdk-绑定用户账号
                    long_bind();// 若用户未登录，绑定失败，需在登录时再绑定
                }
            }
        });
        // 下行通道监听器
        MobileChannel.getInstance().registerDownstreamListener(true, listener);//第1个参数：是否要在UI线程里回调，建议为YES
    }

    // 推送sdk 初始化
    private void push_init(){
        PushServiceFactory.init(curContext);
        CloudPushService pushService = PushServiceFactory.getCloudPushService();
        // 设置安全图片的auth code
        pushService.setSecurityGuardAuthCode("114d");
        pushService.register(curContext, new CommonCallback() {
            @Override
            public void onSuccess(String response) {
                Log.w(TAG, "init cloudchannel success");
            }
            @Override
            public void onFailed(String errorCode, String errorMessage) {
                Log.w(TAG, "init cloudchannel failed -- errorcode:" + errorCode + " -- errorMessage:" + errorMessage);
            }
        });
    }

    // 登录后的操作
    private void after_login(){
        // 长连接通道SDK 绑定用户账号
        long_bind();
        //先取消之前的监听
        MobileChannel.getInstance().unRegisterDownstreamListener(listener);
        // 下行通道监听器
        MobileChannel.getInstance().registerDownstreamListener(true, listener);//第1个参数：是否要在UI线程里回调，建议为YES
    }
    // 退出登录前的操作
    private void before_logout(){
        long_unbind();// 长连接通道sdk- 解除绑定用户账号
        MobileChannel.getInstance().unRegisterDownstreamListener(listener);// 取消长连接下行通道监听
        DeviceManager.getInstance().clearAccessTokenCache();//账号退出时需要清理设备缓存的数据
    }

    // 阿里云sdk初始化
    private void sdk_init(){
        // API通道SDK 初始化
        api_init();
        // 账号和用户SDK 初始化
        login_init();

        // 身份认证SDK 初始化
        // 务必注意在调用之前，保证完成了【用户和账号SDK】的初始化
        IoTCredentialManageImpl.init(app_key);
        // 初始化IoTCredentialProviderImpl模块代码如下：
        IoTAuthProvider provider = new IoTCredentialProviderImpl(IoTCredentialManageImpl.getInstance((Application) curContext));
        IoTAPIClientImpl.getInstance().registerIoTAuthProvider("iotAuth", provider);
        // 处理认证失败
        // 目前服务端逻辑不支持同一个账号多端登录，如果一个账号在多个设备登录，那么只有最后一个登录的账号才可以正常访问IoT服务，其他账号则会返回认证错误
        IoTCredentialManageImpl.getInstance((Application) curContext).setIotCredentialListenerList(new IoTTokenInvalidListener() {
            @Override
            public void onIoTTokenInvalid() {
                // 当onIotTokenInvalid被触发时，需要提示用户当前会话已失效，需要重新登录
                
                // 仅仅把通知发出去 - 让业务层调用退出逻辑
                try {
                    String json = "{\"topic\":\"IotTokenInvalid\",\"data\":null}";
                    JSONObject obj = new JSONObject(json);
                    JSUtil.execCallback(pWebviewLong, CallBackIDLong, obj, JSUtil.OK, true);//回调通知js层，最后一个参数true，持续输出
                } catch (JSONException e) {
                    Log.w(TAG,e.getMessage());
                }
            }
        });

        // BoneMobile容器SDK 初始化
        bonemobile_init();
        // 配网SDK 的初始化依赖 身份认证SDK 模块的初始化

        // 长连接通道SDK 初始化
        long_link_init();

        // 设备模型SDK 初始化 - 依赖 API 通道 SDK，以及长连接通道 SDK
        TmpSdk.init(curContext, new TmpInitConfig(TmpInitConfig.ONLINE));
        // 调用发现本地设备接口 - 在网络情况发生变化时同样需要调用该接口。网络情况发生变化包括切换连接的路由器，从 WiFi 切换到 4g 网络等
        TmpSdk.getDeviceManager().discoverDevices(null,5000,null);

        // 推送sdk 初始化
        push_init();
    }
    
    // 测试
    public void test(IWebview pWebview, JSONArray array){
        final String CallBackID = array.optString(0);//回调通知id
        // 调用方法将原生代码的执行结果返回给js层并触发相应的JS层回调函数
        JSUtil.execCallback(pWebview, CallBackID, "test is ok", JSUtil.OK, true);
        // 调用方法将原生代码的执行结果返回给js层并触发相应的JS层回调函数
        JSUtil.execCallback(pWebview, CallBackID, "test is fail", JSUtil.ERROR, false);
    }

    //  长连接通道 - 实时监测状态 - 全局
    public void longlink(IWebview pWebview, JSONArray array){
        pWebviewLong = pWebview;
        CallBackIDLong = array.optString(0);//回调通知id
    }

    // 撞墙测试
    public void ping(final IWebview pWebview, JSONArray array){
        final String CallBackID = array.optString(0);//回调通知id
        //String time =  String.valueOf(System.currentTimeMillis());
        SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String time =format.format(new Date());
        // 构建请求-撞墙测试接口
        IoTRequest request = new IoTRequestBuilder()
                .setScheme(Scheme.HTTPS)
                .setPath("/kit/debug/ping") // 参考业务API文档，设置path
                .setApiVersion("1.0.0")  // 参考业务API文档，设置apiVersion
                .addParam("input", "测试撞墙数据 " + time) // 参考业务API文档，设置params,也可使用setParams(Map<Strign,Object> params)
                .build();
        // 获取Client实例，并发送请求
        IoTAPIClient ioTAPIClient = new IoTAPIClientFactory().getClient();
        ioTAPIClient.send(request, new IoTCallback() {
            @Override
            public void onFailure(IoTRequest request, Exception e) {
                // 根据 e， 处理异常
                Log.w(TAG, e.getMessage());
                JSUtil.execCallback(pWebview, CallBackID, e.getMessage(), JSUtil.ERROR, false);//回调通知js层
            }
            @Override
            public void onResponse(IoTRequest request, IoTResponse response) {
                int code = response.getCode();
                // 200 代表成功
                if(200 != code){
                    String mesage = "[" + String.valueOf(code) + "] " + response.getMessage() + " " + response.getLocalizedMsg();
                    Log.w(TAG, mesage);
                    JSUtil.execCallback(pWebview, CallBackID, mesage, JSUtil.ERROR, false);//回调通知js层
                    return;
                }
                Object data = response.getData();
                // 解析 data
                Log.w(TAG, data.toString());
                JSUtil.execCallback(pWebview, CallBackID, data.toString(), JSUtil.OK, false);//回调通知js层
            }
        });
    }
    
    
    ......
}
```



接下来就是把需要的iot功能逐步封装成一个个方法，以便抛给上层的js调用。





**iOS苹果版集成：**



阿里云iOS的技术文档明显没有安卓的完善，我们来逐步说说。



1、给项目工程里面添加Podfile配置文件，以及CocoaPods的简单使用

IOS的SDK 采用 cocoapods 管理依赖，建议采用 1.1.1 以上版本，SDK 的集成请参考以下步骤：



应用依赖描述文件

请将下载的IOS SDK Podfile 文件放到工程文件夹根目录, 并将 Podfile 文件中的 target 名称修改成和 xcode 工程的设置一致。

api level我选择了4，生成podfile文件如下：

```
# SDK 最低支持版本为 iOS 8.0
platform:ios, '8.0'
# github 官方 pod 源
source 'https://github.com/CocoaPods/Specs.git'
# 阿里云 pod 源
source 'https://github.com/aliyun/aliyun-specs.git'
# 需要替换下述 "IMSDemoApp" 为开发者 App 的 target 名称
target "IMSDemoApp" do
    pod 'AlicloudALBBOpenAccount', '3.4.0.30'
    pod 'IMSApiClient', '1.2.0'
    pod 'IMSAuthentication', '1.1.0'
    pod 'IMSBreezeSDK', '1.4.0'
    pod 'IMSBoneKit', '1.2.6'
    pod 'AKReactNative', '0.41.2'
    pod 'MJRefresh', '3.1.15'
    pod 'ZipArchive', '1.4.0'
    pod 'IMSOtaBusinessSdk', '1.4.0'
    pod 'SSZipArchive', '2.1.2'
    pod 'IMSDeviceGateway', '1.4.0'
    pod 'IMSDeviceCenter', '1.3.2'
    pod 'CocoaAsyncSocket', '7.4.2'
    pod 'Reachability', '3.2'
    pod 'IMSThingCapability', '1.4.1'
    pod 'AlicloudPushIoT', '1.9.5.3'
    pod 'IMSMobileChannel', '1.4.0'
end
```



然后执行命令

```
pod update
```



关于cocoapods管理依赖，可参考：https://blog.csdn.net/cc1991_/article/details/76686991





2、启动图片设置不当导致ios下字体变大的原因：

http://ask.dcloud.net.cn/question/16328



3、pod update安装依赖后出的问题：

```
[!] The `HBuilder [Debug]` target overrides the `GCC_PREPROCESSOR_DEFINITIONS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
[!] The `HBuilder [Debug]` target overrides the `LIBRARY_SEARCH_PATHS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
[!] The `HBuilder [Debug]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.debug.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
[!] The `HBuilder [Release]` target overrides the `GCC_PREPROCESSOR_DEFINITIONS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
[!] The `HBuilder [Release]` target overrides the `LIBRARY_SEARCH_PATHS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
[!] The `HBuilder [Release]` target overrides the `OTHER_LDFLAGS` build setting defined in `Pods/Target Support Files/Pods-HBuilder/Pods-HBuilder.release.xcconfig'. This can lead to problems with the CocoaPods installation
    - Use the `$(inherited)` flag, or
    - Remove the build settings from the target.
```



这种警告是不能忽视的，它带来的直接后果就是无法通过编译。

```
* 项目 Build Settings - Other Linker Flags 里，增加 $(inherited)，如果原来有 -ObjC ，不要删除，保留，如果删除会出错。
* 项目 Build Settings - Library Search Paths 里，增加 $(inherited)
* 项目 Build Settings - Preprocessor Macros 里，增加 $(inherited)
```

然后 pod update 更新pod资源。





4、错误汇总



【错误】：**Multiple commands produce**

```
Multiple commands produce '/Users/CCMAC/Library/Developer/Xcode/DerivedData/HBuilder-Hello-blanjdkvalzanccxhlqgkzbgoirb/Build/Products/Debug-iphoneos/HBuilder.app':
1) Target 'HBuilder' has create directory command with output '/Users/CCMAC/Library/Developer/Xcode/DerivedData/HBuilder-Hello-blanjdkvalzanccxhlqgkzbgoirb/Build/Products/Debug-iphoneos/HBuilder.app'
2) That command depends on command in Target 'HBuilder': script phase “[CP] Copy Pods Resources”
```



解决方法：

File - Workspace Settings - Build System 里，选项值均改为 Legacy Build System (有2个)





【错误】：**duplicate symbol _kReachabilityChangedNotification in:**

```
    /Users/CCMAC/Library/Developer/Xcode/DerivedData/HBuilder-Hello-blanjdkvalzanccxhlqgkzbgoirb/Build/Products/Debug-iphoneos/Reachability/libReachability.a(Reachability.o)
    /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/libASIHttpRequest.a(Reachability.o)
```



原因是引用的2个第三方库都包含了同样的 Reachability.o ，需要删掉其中一个：

由于阿里云sdk需要使用到 Reachability.o，不能删除，因此我们删除 5+SDK里的 Reachability.o：

打开终端输入如下命令： 

```
cd /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/
lipo -info libASIHttpRequest.a
返回：Architectures in the fat file: libASIHttpRequest.a are: armv7 armv7s i386 x86_64 arm64
```



分离出5种静态库：

```
lipo -extract_family armv7 -output libASIHttpRequest_armv7.a libASIHttpRequest.a
lipo -extract_family arm64 -output libASIHttpRequest_arm64.a libASIHttpRequest.a
lipo -extract_family i386 -output libASIHttpRequest_i386.a libASIHttpRequest.a
lipo -extract_family x86_64 -output libASIHttpRequest_x86_64.a libASIHttpRequest.a
```



armv7 和 armv7s 是特殊的架构，实际上是同一种架构，分不同苹果手机：

```
lipo libASIHttpRequest_armv7.a -thin armv7 -output libASIHttpRequest_armv7_final.a
lipo libASIHttpRequest_armv7.a -thin armv7s -output libASIHttpRequest_armv7s_final.a
```



因为提示重复“3 duplicate symbols for architecture arm64” 只有arm64架构的，我们需要删除 libASIHttpRequest_arm64.a 里的重复定义：

```
ar -d libASIHttpRequest_arm64.a Reachability.o
```



在正式打包的时候 Product - Archive 的时候还会提示 duplicate symbols for architecture armv7 错误，这个错误正式打包的时候 armv7 架构里也重复了，同理去掉armv7 架构的。

```
ar -d libASIHttpRequest_armv7_final.a Reachability.o
ar -d libASIHttpRequest_armv7s_final.a Reachability.o
```



先合并arm架构的：

```
lipo -create -output libASIHttpRequest_armv7.a libASIHttpRequest_armv7_final.a libASIHttpRequest_armv7s_final.a
```



合并新文件：

```
lipo -create -output libASIHttpRequest.a libASIHttpRequest_armv7.a libASIHttpRequest_arm64.a libASIHttpRequest_i386.a libASIHttpRequest_x86_64.a
```



执行后，可以看到 libASIHttpRequest.a 文件大小减少了。







【错误】：**duplicate symbol _OBJC_CLASS_$_ZipArchive in:**

```
    /Users/CCMAC/Library/Developer/Xcode/DerivedData/HBuilder-Hello-blanjdkvalzanccxhlqgkzbgoirb/Build/Products/Debug-iphoneos/ZipArchive/libZipArchive.a(ZipArchive.o)
    /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/libcoreSupport.a(ZipArchive.o)
```



解决方法（由于阿里云sdk需要用到ZipArchive解压缩，删除会报错，因此我们删除5+sdk里的重复定义的 ZipArchive.o）：

```
cd /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/
lipo -info libcoreSupport.a
返回：Architectures in the fat file: libcoreSupport.a are: i386 armv7 x86_64 arm64
```



分离出4种静态库：

```
lipo -extract_family armv7 -output libcoreSupport_armv7.a libcoreSupport.a
lipo -extract_family arm64 -output libcoreSupport_arm64.a libcoreSupport.a
lipo -extract_family i386 -output libcoreSupport_i386.a libcoreSupport.a
lipo -extract_family x86_64 -output libcoreSupport_x86_64.a libcoreSupport.a
```



因为提示重复“6 duplicate symbols for architecture arm64” 只有arm64架构的，我们只需要删除 libcoreSupport_arm64.a 里的重复定义：

```
ar -d libcoreSupport_arm64.a ZipArchive.o
```



在正式打包的时候 Product - Archive 的时候还会提示 duplicate symbols for architecture armv7 错误，这个错误正式打包的时候 armv7 架构里也重复了，同理去掉armv7 架构的。

```
ar -d libcoreSupport_armv7.a ZipArchive.o
```



合并生成新的a文件：

```
lipo -create -output libcoreSupport.a libcoreSupport_armv7.a libcoreSupport_arm64.a libcoreSupport_i386.a libcoreSupport_x86_64.a
```



重新编译就通过了。



【错误】：**duplicate symbol _OBJC_CLASS_$_AidManager in:**

```
    /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/HBuilder-Hello/Pods/AlicloudUTDID/utdid/UTDID.framework/UTDID(AidManager.o)
    /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/AlipaySDK.framework/AlipaySDK
```



解决方法(先备份AlipaySDK文件)：

```
cd /Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/SDK/Libs/AlipaySDK.framework/
lipo -info AlipaySDK
返回：Architectures in the fat file: AlipaySDK are: i386 x86_64 armv7 arm64
```



发现这个文件对应4种不同的CPU架构，需要先分离静态库：

```
lipo -extract_family armv7 -output AlipaySDK_armv7 AlipaySDK
lipo -extract_family arm64 -output AlipaySDK_arm64 AlipaySDK
lipo -extract_family i386 -output AlipaySDK_i386 AlipaySDK
lipo -extract_family x86_64 -output AlipaySDK_x86_64 AlipaySDK
```



删除分离出的静态库，由于报错里只是提示“34 duplicate symbols for architecture arm64”，因为我们只需要处理 arm64 架构下的静态库 UTDID_arm64 就可以了：

ar -d AlipaySDK_arm64 AidManager.o

所有重复的 o文件都需要删除：

```
AidManager.o
AidRequester.o
AidStorage.o
UTDIDAES.o
UTDIDBaseUtils.o
UTDIDGTMBase64.o
UTDIDHelper.o
UTDIDIntUtils.o
UTDIDKeychainItemWrapper.o
UTDIDMain.o
UTDIDOpenUDID.o
UTDIDPersistentConf.o
UTDIDPersistentFile.o
UTDIDStringUtils.o
UTDIDTypeConvert.o
UTDevice.o
```



正常的是删除o文件即可，但我这里报错：ar: AlipaySDK_arm64: Inappropriate file type or format

因此转换思路，直接不要 arm64架构的文件。



在正式打包的时候 Product - Archive 的时候还会提示 duplicate symbols for architecture armv7 错误，这个错误正式打包的时候 armv7 架构里也重复了，同理去掉armv7 架构的。



最后合成新的静态库(合并除arm64、armv7架构之外的3个)：

```
lipo -create -output AlipaySDK AlipaySDK_i386 AlipaySDK_x86_64
```



再次编译，报错：

```
Undefined symbols for architecture arm64:
  "_OBJC_CLASS_$_AlipaySDK", referenced from:
      objc-class-ref in libalixpayment.a(PGAlixPay.o)
      objc-class-ref in libpingpp.a(Pingpp.o)
```

到 Build Phases - Link Binary With Libraries 里，删除：

```
libalixpayment.a
libpingpp.a
libpingpppay.a
```





【错误】：**Include of non-modular header inside framework module**

```
'IMSThingCapability.IMSDiscoveryRegistry': '/Users/CCMAC/Desktop/ios_app/5plus-ruizhi/SDK/HBuilder-Hello/Pods/AKTBJSONModel/iot-sdk-jsonmodel/TBJSONModel.framework/Headers/TBJSONModel.h'
```

解决：

Build Setting ― Allow Non-modular Includes In Framework Modules

设置为YES，则可以在Framework中使用模块外的Include





【错误】：**Undefined symbols for architecture arm64:**

```
  "_OBJC_CLASS_$_LKIoTMobileGateway", referenced from:
      objc-class-ref in IMSThingCapability(IThingCloudChannel.o)
      objc-class-ref in IMSThingCapability(IMSSubDeviceService.o)
      objc-class-ref in IMSThingCapability(SubdeviceAdapter.o)
```



解决方法：

阿里云的 API level 4里面 LKIoTMobileGateway 类定义到了蓝牙设备接入框架里了，依赖以下2个sdk：

```
    pod 'IMSBreezeSDK', '1.4.0'
    pod 'IMSDeviceGateway', '1.4.0'
```





【错误】：**调用boneMobile插件报错的信息**

```
#00x00000001057c3170 in jk_encode_add_atom_to_buffer at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2599
#10x00000001057c3dcc in jk_encode_add_atom_to_buffer at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2778
#20x00000001057c3dcc in jk_encode_add_atom_to_buffer at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2778
#30x00000001057c3d18 in jk_encode_add_atom_to_buffer at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2811
#40x00000001057c2d1c in -[JKSerializer serializeObject:options:encodeOption:block:delegate:selector:error:] at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2876
#50x00000001057c2a84 in +[JKSerializer serializeObject:options:encodeOption:block:delegate:selector:error:] at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:2831
#60x00000001057c4758 in -[NSDictionary(JSONKitSerializing) JSONStringWithOptions:error:] at /Users/xufeng/projects/third-party/JSONKit/JSONKit/JSONKit.m:3023
#70x0000000104e673c0 in _RCTJSONStringifyNoRetry at /Users/yuanzhan/.jenkins/jobs/MUPP_2384528/workspace/AKReactNative/React/React/Base/RCTUtils.m:51
#80x0000000104e67250 in RCTJSONStringify at /Users/yuanzhan/.jenkins/jobs/MUPP_2384528/workspace/AKReactNative/React/React/Base/RCTUtils.m:79
#90x0000000104e9a9e0 in -[RCTBatchedBridge moduleConfig] at /Users/yuanzhan/.jenkins/jobs/MUPP_2384528/workspace/AKReactNative/React/React/Base/RCTBatchedBridge.m:476
#100x0000000104e98c64 in __25-[RCTBatchedBridge start]_block_invoke.67 at /Users/yuanzhan/.jenkins/jobs/MUPP_2384528/workspace/AKReactNative/React/React/Base/RCTBatchedBridge.m:146
```



解决方法：

Build Phases 删除库： **libJSONKit.a**

注意，这个库是Hbuilder sdk里带的，这个库引入的太失败了，居然还指向Hbuilder开发人员电脑的路径上。我在这个问题上耗费了不少时间。开始我以为是阿里云的sdk引用的**libJSONKit**出的问题，发工单排查，经过繁琐的排查之后，才定位到html 5 + sdk里的这个库。





【错误】：**ios配网插件打开，没有wifi的ssid填入**

解决方法：XCODE - Target - Capabilities - Access WiFi Infomation - ON

同时需要在苹果的开发者中心 App IDs 里面 把 “Access WiFi Infomation” 勾上。





**XCODE的一些必要设置**（请先将MAC OS系统和XCODE升级到最新）：



```
项目 Build Settings 设置：
No Common Blocks 里，把值从 Yes 改为 No
Enable Testability 里，把 Debug 的值从 Yes 改为 No

项目描述文件设置：
General 里设置（不要勾选 Automatically manage signing ）：
Signing(Debug) 导入开发描述文件；
Signing(Release) 导入发布描述文件。

Build Settings里设置：
Code Signing Identity 里分别设置 Debug 和 Release 使用的开发者证书。
```



**启动图片**：

新版的5+SDK里，展示启动图片之前会有hbuilder自带的开屏广告，如果不需要可删除：

```
在Appdelegate.m文件中注释如下部分，并删除ad库文件 liblibAdSupport.a ,即可关闭广告
#define ENABLEAD
```



**IOS沉浸式状态栏设置**：

iOS11以上系统当启用沉浸式式状态栏后顶部有灰条的问题解决

可以在meta(name="viewport")节点的content属性值中添加viewport-fit=cover



**设备上报频次**

关于设备上报频次问题，因为阿里云这边有限制，每天每台设备3000条上行下行消息，需要商定上报策略：

1，设备开机联网时上报1次属性值；

2，待机时当设备属性变化时上报一次；

3，当云端发送指令给设备时，在设备完成动作之前，每秒钟上报一次（比如云端发送平开80%指令，在设备从0%打开到80%的过程中，设备每秒钟上报当前的属性值，当完成该指令的时候停止上报属性值）。



**特殊情况记录**：

1，从心跳包丢失到云端更新设备为离线状态，需要1分钟27秒钟。

2，设备刚上线，但是还未上报属性的情况下，获取设备属性获取不了。

3，设备配网成功后，获取token时可能耗时比较长，慢的可能需要40几秒，拿到token后绑定用户就可以秒绑了。



如果你也有智能硬件的项目，或者希望实现智能硬件 + 平台（云端） + APP（微信或小程序）终端等一整套



其它物联网设备上云案例参考：

- [安防摄像头IPC如何快速对接阿里云生活物联网？](https://developer.aliyun.com/article/1429311?source=5176.11533457&userCode=ywqc0ubl)