- PS:**之前写过Ubuntu下的安装方法，[点击这里](http://www.jianshu.com/p/cc5c35ae7009)**

###1. 下载并安装适用于Windows的[Python](https://www.python.org/downloads/windows/)，您可以在64位Windows中下载x86-64 MSI安装程序。

###2. 在安装过程中应该安装 *pip*
![](http://upload-images.jianshu.io/upload_images/3235837-54ac4e912c84ef6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###3. 安装Windows的[OpenSSL](https://slproweb.com/products/Win32OpenSSL.html)。如果你安装64位Python，你应该安装64位OpenSSL。
####注：
- **下载非*    Light v1.0.2   *版，也就是开发人员版本**
- **OpenSSL 需要 Visual C++ 2008 Redistributables 支持，[32位系统点我](http://www.microsoft.com/downloads/details.aspx?familyid=9B2DA534-3E03-4391-8A4D-074B9F2BC1BF) | [64位系统点我](http://www.microsoft.com/downloads/details.aspx?familyid=bd2a6171-e2d6-4230-b809-9a8d7548c1b6)**

###4. 接下来就是像使用Linux一样安装Shadowsocks服务端啦！使用这段命令：
``` pip install shadowsocks ```
![](http://upload-images.jianshu.io/upload_images/3235837-650d94352b48a955.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###5. 如果要使用salsa20或chacha20加密，请下载[libsodium](http://download.libsodium.org/libsodium/releases/)并将dll文件（无路径）放入
***C:\Windows\System32或C:\Windows\SysWOW64（64位Windows上的32位Python）。***

###6. 现在去配置服务器设置。你在任意地方建立一个文件，比如叫config.json，然后填入你的服务器配置。比如我想要在8388端口创建一个密码为123456的加密方式为aes-256-cfb的一个服务器，那么这么写：
```
{
    "server":"0.0.0.0",
    "server_port":8388,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"123456",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open":false
}
```
###然后保存在C:\Python27\Scripts\config.json。执行以下命令运行：
```ssserver -c C:\Python27\Scripts\config.json```
>**如果它报错**
Exception: libcrypto(OpenSSL) not found

###就去OpenSSL的安装目录复制
***libeay32.dll, libssl32.dll, ssleay32.dll到C:\Python27\Scripts\ ***
**注：OpenSSL v1.02才有以上三个文件**
###可以看到我的服务已经启动成功了！好了享用Windows下的Shadowsocks服务器吧！
![](http://upload-images.jianshu.io/upload_images/3235837-3da4f7cfffa7c366.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
