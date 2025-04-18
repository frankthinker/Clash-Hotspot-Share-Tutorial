# 通过电脑端Clash共享代理到其他设备 2025年教程

![image](https://github.com/user-attachments/assets/85c9051b-c38a-42c3-ac18-390348a90959)

## **导言**：

**本文讲述如何在Windows系统（以Windows 11 24H2为例）中，通过CFW(Clash for Windows)共享代理到其他设备。**

**这里的【其他设备】，指的是连接到同一WiFi下的其他设备。若是代理给非同一局域网下的其他远程设备，本文并不关心，请自行类推解决。**

**要解决的痛点：其他很多教程都没法解决问题，只有我自己瞎鼓捣出来了。**

## 我为什么希望解决这个问题？

我遇到的问题背景是，

如今是2025年了，随着技术的发展，VR设备逐渐走向成熟，走向千家万户，若干年前我买了一个旧的VR设备，三星的玄龙MR+，没什么网络问题。如今，我购置了新的设备，Meta公司旗下的Quest3S，它的性价比和闻名度是较高的。然而众所周知在“等国”，其网络连接会遇到问题，可能连初始化都困难。别说，你选择激活VR设备后后下载第三方的代理App到VR设备上，这个步骤要开启【开发者模式】不说，还可能导致设备卡顿（你的VR是一个移动设备，记住这一点，它不是高性能电脑）-->4.18更新：对不起，VR设备上即使能运行这类App，也无法真正实现代理，这和底层硬件的差距或者系统组件的差异性有关。

因此，一个亟待解决的问题是：如何把一个已经拥有代理的电脑，其代理状态分享到其他设备？

这里我们不用（x 手机上或其它设备上打开WLAN选项，手动配置代理）的方法。我也不用路由器上进行配置，这样较为麻烦。

## 步骤一
先确定好自己要拿哪台电脑进行共享，这台电脑必须可以本身开启代理。

找到自己电脑的IP地址：

这个IP地址，**指的是WLAN即WiFi的IP地址（而非其他适配器的地址！）**

获取方法一，在cmd中输入

ipconfig /all

然后找到这里，IPV4地址：
![image](https://github.com/user-attachments/assets/d0df430a-5d6b-447b-8174-cfc7a2750263)


获取IP地址的方法二是，找到Clash中允许局域网旁边的三叉形按钮，点击。
![image](https://github.com/user-attachments/assets/9dccabdd-868e-42ac-b507-1a36b597eceb)



然后找到WLAN这一项，
![image](https://github.com/user-attachments/assets/e46129ef-119c-4b4a-8e5d-a578615acf74)



**记住地址是多少，我们这里是192.168.0.2**

## 步骤二
转到Clash

1. 打开Clash的【Allow Lan /允许局域网】，这一步是为了让Clash允许局域网连接。

2. 确认自己的 【Service Mode/服务模式】旁边的地球是绿色的，即服务模式开启了。所谓服务模式，是为了让你在不以管理员身份运行Clash时，依然可以正常共享。

3. 看看Clash界面的【Port/端口】是多少，例如，Port设置成1080。**记住这个数字，1080。**

![image](https://github.com/user-attachments/assets/44d88f13-68e8-4d01-b357-8adb14724292)


## 步骤三
下载SSTap并转到SSTap，
![image](https://github.com/user-attachments/assets/c53c9d9e-e497-49ed-8f46-735941767f7e)


在 SSTap 主界面中，点击“添加HTTP/SOCKS4/SOCKS5”

然后设置一下这里的参数，**协议为 socks5，IP 为 192.168.0.2，端口是1080（请根据自己电脑的实际情况来填写，这两个标红的参数在上面讲了怎么获得，若不知道，再重新返回之前的步骤）**

**其他的都不用管，都不填写。**

保存设置，在主界面中选择“不代理中国IP”，然后连接

![image](https://github.com/user-attachments/assets/55f04556-e6fe-43a0-87c8-bcb26cd5d59b)


必须启用SSTap的连接，且打开了Clash的连接，才能进入下一步！

## 步骤四
单击Windows键，搜索“网络连接”，打开下面界面
![image](https://github.com/user-attachments/assets/0ad329ec-f161-410c-aead-e3ca2e4ad97e)


**确保Clash和SSTap适配器都是打开的状态，没有红叉。**

然后右键SSTAP进行设置：

![image](https://github.com/user-attachments/assets/8c6b8892-54dd-42c8-8b2d-6d119f5d5637)


## 步骤五
下载，并打开Connectify （全称Connectify Hotspot)。

第一次安装完毕后，电脑必须重启。

然后打开Connectify的设置，【要共享的Internet】是TAP-Windows开头的那一串适配器，即SSTAP对应的适配器。
![image](https://github.com/user-attachments/assets/40e0749d-e2b2-4780-b596-ddc5032bd217)


开启热点后，把其他设备连到这个热点即可，可以扫描二维码连接（如果其他设备支持的话）

**接下来就可以尽情冲浪了！妈妈再也不用担心我的学习！**


注意，

1，若在这一步遇到Connectify提示【Javascript 已禁用。请为 Internet Explorer 启用 Javascript 或在您的防火墙中取消阻止 Javascript，然后再激活。】，可以点击超链接，按照它提示的步骤来操作！
2， 若不为Connectify启用Javascript，则无法继续操作。
3，无需为Connectify充值，无需寻求破解版。我们使用到的仅仅是基础免费功能，这就足够了。
4，免费版本，只需先后点击紫色按钮【免费试用】、【开始使用Lite版】即可。
5，退出Connectify，或者点击设置菜单，停止热点，即可停止共享。


备注
Q：可以不用步骤五里的Connectify吗？
A：步骤五不能跳过，如果你用Windows系统自带的热点，那么，电脑默认的热点共享行为会把WiFi共享出去，而不是把代理状态共享出去。

Q：为什么要用SSTAP，不可以直接共享Clash吗？
A：有的教程让你先建立电脑自带的热点，然后在【网络连接】面板里，让Clash共享到新冒出来的【本地连接】适配器里，这一操作，或许可以让你在其他设备（连接了电脑热点后）代理部分App如TG，但是大多数软件无法正常代理！请严格遵循我的步骤来操作！


**补充：手机上我最近尝试成功的一个方法，是下载https://github.com/Mygod/VPNHotspot/releases/tag/v2.18.4。这个方法仅对root后的手机有效。在手机开启代理、进入VPN Hotspot app后打开第一个选项（wifi中转选项），将开启一个新的Wifi连接，此时你就可以畅玩了！这一方法对Clash有效，甚至对很多闭源app也有效！缺点是网速较慢，优点是配置简单。**
