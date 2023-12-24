# 前言

前不久趁着周末，拎着**DJI Mini 4 Pro**出去试飞。回来后，照例把视频素材传回手机上进行剪辑。可是，我很快就觉察到了，在手机里剪辑很不方便。  
突然瞥见角落里那个默默备份家里所有移动设备的数据，时常被灰尘洗礼的 NAS 设备，我一拍大腿，想起没准儿能用这个玩意儿，让我在电脑上直接剪辑。

# 准备工作

要解决这个问题，咱得先解决网络覆盖的问题。路由器一直是跟 NAS 设备连一块儿，由于大部分活动时间都在客厅和楼上，根本没咋关心无线信号咋样。  
但现在不行了，楼上小孩子要早睡觉，晚上就没太多时间在楼上，只好把电脑桌搬到了楼下后面那个犄角旮旯堆满杂物的小房间，5G 信号就够不着了，只能勉强用着 2.4G 信号。

> 哎，这偌大的屋子竟然没有我的容身之所。

回归正题，之前为了方便直接就把路由器天线都收起来了，将路由器贴墙上，使用的是**纳米无痕胶**贴上去的，许久未动，拆不下来了。

俗话说万事开头难啊！折腾了好一会儿，还是拆不下来，后来发现**红米AX6000**路由器的壳是可以分离，得用螺丝刀先把路由器的两颗隐藏螺丝拆掉（撕开路由器背面贴纸可以看到）。

**这里分享一个快速去除纳米无痕胶的生活小妙招**

> 拿吹风机对着吹，就可以把纳米无痕胶软化，然后用酒精或者疫情前没有用完的消毒液，喷在上面，就可以很快的把墙壁的胶弄掉，还不留痕迹。

不过也是费了好大劲才从墙上强行拆了下来，不得不说这纳米无痕胶效果还真的好。
## 解决 WIFI 信号问题

接下来咱们先把路由器组装回去，然后把天线摆正，下了个网速管家 App 来检测 WIFI 信号，争取弄到最好的信号覆盖。
![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/2eed910e5338f8ec34f280551094b6cb.png)

网速管家可以边走边测信号还是挺好的，到了小房间结果显示，调整天线后信号确实有改善。为了提高信号质量，我又把路由器往小房间那边挪了两三米，幸好当初买的网线够长。 为自己的机智点个赞！
![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/1c1ae06f5240d71d14bae7f94d6e96e8.png)

调整后，发现小房间那边的 WIFI 信号终于到了一个勉强能接受的信号值。

## 解决电脑直连 NAS 问题

接下来，把 NAS 设备挪到电脑桌这里。NAS 设备没有自带无线网卡，没办法直接连接 WIFI，还需要额外购买官方指定型号的无线网卡。为了省钱，我找了家里闲置的路由器搞了个无线信号扩展，再把网线从闲置路由器接到 NAS 设备上，完美搞定！

接下来做一些简单的配置

### 配置

1. 打开**绿联云 DX4600** 客户端进行设置，**设备管理**-**网络模式**-**桥接模式**
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/47b6c59b2f1d6b2fd5d66ea39e079a1f.png)

2. 在**网络服务**-配置**账号和密码**
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/5bb4a3a926803c3013e4bd4444a5b76f.png)
3. 开启**Samba**
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/83f2e5bcc46e8c80fb3739fccdb91d2d.png)
4. 高级设置选择 **SMB3**，启用Samba 多通道
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/93b8e6ae39fb71a3cb9bcdc7e745e33c.png)
5. 电脑开启**网络发现**配置
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/e0d99adc7901b4a74a00da478b796b99.png)

6. 打开电脑**文件资源管理器**-**网络**，就可以发现 NAS 设备，点击文件夹右键进行**映射网络驱动器**
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/22a672a78ad0922c34d8d27be2c54ae5.png)

7. 映射完毕后，在我的电脑就可以显示 NAS 设备的硬盘了
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/074fd8163d87cf94bf8ab494d0cdaa96.png)

8. 现在随便找个大文件来测试传输速度，速度直接达到了 **280MB/秒**，拉满
   ![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/09645eabdcde5919b62cd7b1372dc824.gif)

# 终极测试

打开剪影专业版来测试视频素材的拉取速度。
这下好了，我终于能用电脑痛痛快快地剪辑视频了。

# 总结

这次经历让我明白，有时候看起来特别麻烦的事儿，其实只要咱们巧妙运用身边的资源，稍微想想办法，日子就能过得精彩。

