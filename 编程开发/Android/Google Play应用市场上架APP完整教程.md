如果你的google play 是英文的，建议第一时间可以把翻译改一下。方便后续操作。



# 创建APP

![image-20240905163326805](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409051633650.png)

三项声明必须接受，否则无法创建APP.



## 创建内部测试版本

这里我们不使用google的签名

![image-20240905164921514](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409051649406.png)



![image-20240905165119062](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409051651762.png)



> 温馨提示：Java的jdk有两个版本一个是Oracle JDK另一个是OpenJDK ，谷歌要使用OpenJDK环境 才能生成签名，大佬说的不是很明确，在此补充了一下，避免大家掉坑

![image-20240905172329903](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409051723373.png)



```
java -jar pepk.jar --keystore=foo.keystore --alias=foo --output=output.zip --include-cert --rsa-aes-encryption --encryption-key-path=/path/to/encryption_public_key.pem

java -jar pepk.jar --keystore=htlcam.jks --alias=htlcam --output=output.zip --include-cert --rsa-aes-encryption --encryption-key-path=encryption_public_key.pem
```



发生报错：

```
PS C:\Users\Administrator\Desktop\APP上架\GooglePlay> java -jar pepk.jar --keystore=************  --alias=************ --output=output.zip --include-cert --rsa-aes-encryption --encryption-key-path=encryption_public_key.pem
Enter password for store '************':
Enter password for key '************':
Error: Unable to export or encrypt the private key
java.security.NoSuchAlgorithmException: Cannot find any provider supporting RSA/NONE/OAEPWithSHA1AndMGF1Padding
        at java.base/javax.crypto.Cipher.getInstance(Cipher.java:563)
        at com.google.wireless.android.vending.developer.signing.tools.extern.export.ExportEncryptedPrivateKeyTool.encryptPrivateKeyWithCkmRsaAesKeyWrapEncryption(ExportEncryptedPrivateKeyTool.java:284)
        at com.google.wireless.android.vending.developer.signing.tools.extern.export.ExportEncryptedPrivateKeyTool.run(ExportEncryptedPrivateKeyTool.java:213)
        at com.google.wireless.android.vending.developer.signing.tools.extern.export.ExportEncryptedPrivateKeyTool.main(ExportEncryptedPrivateKeyTool.java:165)
```

参考文献：[谷歌上传自己的签名zip，报错Unable to export or encrypt the private key（已解决）](https://blog.csdn.net/m0_57267951/article/details/131432919)

![image-20240905172834954](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409051728811.png)





## 填写应用内容



![image-20240906174234445](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409061742164.png)



![image-20240912145813700](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409121458375.png)

### 设置隐私权政策



### 应用访问权限

![image-20240912150015008](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409121500454.png)

### 广告

这个简单，一笔概况

![image-20240914152129313](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240914152129313.png)

### 内容分级

![image-20240912150801127](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409121508408.png)

### 目标受众群体

![image-20240914135603982](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409141356268.png)

### 新闻应用

这个简单，一笔概况

### 数据安全

![image-20240914141515491](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409141415478.png)

### 政府应用

这个简单，一笔概况

### 金融产品和服务

这个简单，一笔概况

### 健康

这个简单，一笔概况





## 填写应用发布国家



![image-20240914151701650](https://cdn.jsdelivr.net/gh/Arisono-h5/technical-resources-static@dev/imgs/202409141517738.png)