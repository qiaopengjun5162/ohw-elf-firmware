# 如何使用

本文假设您已经完成[主页](https://github.com/butterfly-communtiy/ohw-elf-firmware)的开发教程或者按照[固件快速写入指南](https://github.com/butterfly-communtiy/ohw-elf-firmware/tree/master/doc/board)已经把最新版本固件写入开发板。

首先点击打开 ohw 官方测试页[ https://ohw-app.vercel.app](https://ohw-app.vercel.app/) ，[点击此处打开](https://ohw-app.vercel.app)。

### 演示视频

这里有一个演示视频，是下方文字图片的视频版本。

[![Open Hardware Wallet - Task 3](https://res.cloudinary.com/marcomontalbano/image/upload/v1736601213/video_to_markdown/images/youtube--Tk8S3mavd5I-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=Tk8S3mavd5I "Open Hardware Wallet - Task 3")

## 检查版本

点击左上角 Connect 按钮应该从灰色的 Connect 变为绿色的 **Connected**，如果未变更则有其他标签页或者 App 打开了连接，请确认关闭。

OHW Status 栏应显示绿色的固件版本号，例为 **OK Version: 0.0.2**。如果显示 Not Found ohw firmware, Please [check the manual](https://github.com/butterfly-communtiy/ohw-elf-firmware)! 请确认按照说明写入固件。

如果您已经完成[固件快速写入指南](https://github.com/butterfly-communtiy/ohw-elf-firmware/tree/master/doc/board)，仍然出现该提示，🔴⚠️请按照指南描述**重新插拔**硬件钱包或者按压硬件钱包上的 **RST** 按钮以重启应用钱包固件⚠️🔴。

![ohw](../image/start/start-7.png)

## 助记词

ohw 支持导入或者生成助记词。

![ohw](../image/start/start-8.png)

### 生成助记词

点击 Generate 默认会生成 24 个单词的助记词，请抄写在纸上，请勿复制截图拍照等。

<br/>

### 导入助记词

空格分隔已有的助记词，点击导入，请注意当前版本只支持**英语**的助记词。

<br/>

### 注意

生成助记词只会显示一次，请注意抄写。刷新页面会**永久**消失，无法恢复。

<br/>

## 生成地址

默认从以太坊路径的第一个地址生成，即 **m/44'/60'/0'/0/0**，您可以选择其他路径。点击 **Get Address** 获取地址。

![ohw](../image/start/start-9.png)

## 签名

此处可对输入的文本进行签名，点击 **Sign Message**，不同的芯片性能不同 1-10 秒种后 **Signature** 显示对应地址的签名。

![ohw](../image/start/start-10.png)

## 直接连接

以 OpenBuild 为例，讲解如何使用 Web3 登陆以及和 App 交互。[点击此处](https://openbuild.xyz/)打开 OpenBuild。

### 建立连接

点击 OpenBuild 网站右上角进入登陆页，点击 **Wallet** 登陆。在弹出的窗口中选择 **WalletConnect**。此时可以识别二维码内容复制或者点击下方 **OPEN** 按钮。点击下图**标记处**复制连接。

![ohw](../image/start/start-11.png)

<br/>

接下来将获取到链接添加到 ohw 测试页的 **WalletConnect** 栏，并点击 **Add。**

![ohw](../image/start/start-12.png)

<br/>

此时弹出连接确认提示，点击确认即可建立与 OpenBuild 网站的链接。

![ohw](../image/start/start-13.png)

<br/>

### 交互

接下来 OpenBuild 请求对一个随机数**签名**，已验证对当前地址的所有权。

![ohw](../image/start/start-14.png)

<br/>

确认后等待 5-10 秒，即可登陆 OpenBuild。此时已连接 OpenBuild，您可以继续操作。

![ohw](../image/start/start-15.png)

## 客户端连接

ohw 的客户端还在开发中，暂时可以选择使用 onekey，onekey 是另一家知名的钱包厂商，ohw 可以接入提供完整体验。[点击前往 onekey 官网](https://onekey.so/)。

### 建立连接

拥有全平台客户端，此处以浏览器插件钱包为例讲解如何接入以及进行交易。浏览器安装钱包插件后点击扩展，打开此页，选择**连接钱包**。

![ohw](../image/start/start-16.png)

<br/>

依次点击 **EVM** -> **WalletConnect**，点击此处或者识别二维码获取链接。

![ohw](../image/start/start-17.png)

<br/>

回到 ohw 测试页**添加**链接，并**确认**连接。

![ohw](../image/start/start-18.png)

![ohw](../image/start/start-19.png)

<br/>

此时已经建立链接，浏览器插件应**显示持有的资产**列表。

![ohw](../image/start/start-20.png)

<br/>

### 发起交易

以在 Ethereum Sepolia Testnet 转账为例，点击**确认**。

![ohw](../image/start/start-21.png)

<br/>

ohw 测试页收到签名请求，**确认**。

![ohw](../image/start/start-22.png)

<br/>

回到插件钱包，交易成功。

![ohw](../image/start/start-23.png)

## 特别提醒

直接连接或者客户端连接使用的 WalletConnect 服务在中国境内连接不稳定，如果出现断联请重新连接。

**ohw 和 onekey 没有合作关系**。

### WeChat

![esp32-c3](../image/start/wechat.jpg)
