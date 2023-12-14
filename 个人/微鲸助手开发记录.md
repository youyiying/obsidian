# 起因

家里的电视是微鲸的，它有一个配套的微鲸助手App，可以用手机来遥控电视。可惜微鲸已经倒闭了，自然微鲸助手也不再维护了，现在不支持最新的Android 14，刚买的新手机安装不了。  
作为程序员，这能忍？于是决定自己动手开发一个遥控器App，来替换微鲸助手。  
说干就干。
# 准备工作

在动手开发之前，需要先弄清楚电视和手机之间是如何通信的。我用旧手机安装了微鲸助手和 Proxybin 抓包工具，然后在同一 WIFI 网络下，用微鲸助手操作电视，并用 Proxybin 抓取网络请求。  
经过分析，发现电视和手机之间是通过 HTTP 协议进行通信的。  
这就好办了，接下来就把所有按键通通点一遍，把请求数据都抓取下来。  
![](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312121725059.png)

# 代码开发

我选择了 Flutter 来开发Android，因为它可以同时支持 iOS 和Android平台，而且有很多优秀的第三方库可以使用。  
重点来了，在AI时代，当然是使用AI来帮我实现代码编写。  
使用ChatGPT进行提问。  
使用Github Copilot辅助编码。  
不得不说，智能编程的时代已经到来。  
> AI不会取代人类，但会使用AI的人将取代不使用AI的人
## 界面开发

回到正题，我参考了微鲸助手 App 的界面设计，搭建了连接设备和操控屏幕两个界面。  
连接设备界面可以扫描当前网络下的可用电视，并显示其 IP 地址和名称。  
操控屏幕界面可以模拟遥控器上的各种按键，并发送相应的 HTTP 请求给电视。  

![微鲸助手UI](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312121725649.png)

![AI辅助生成的UI](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312121723597.png)
## 关键代码

这里我展示一些关键代码片段，以供参考。

```dart
  static _deviceSearchIsolate(Map<String, dynamic> context) {
    final messenger = HandledIsolate.initialize(context);
    messenger.listen((wifiIP) async {
      List<String> deviceList = [];
      if (wifiIP != null) {
        final String subnet = wifiIP!.substring(0, wifiIP!.lastIndexOf("."));
        for (int i = 1; i < 256; i++) {
          var activeHost = await PortScannerFlutter.isOpen(
            "$subnet.$i",
            _port,
            timeout: const Duration(milliseconds: 100),
          );
          if (activeHost != null) {
            deviceList.add(activeHost.address);
            break;
          }
        }
      } else {
        print("failed to retrieve IP");
      }
      messenger.send(deviceList);
    });
  }

  static Future<List<String>> findLocalDevices() {
    return NetworkInfo().getWifiIP().then((ip) async {
      List<String> foundDevices = [];
      final isolateHandler = IsolateHandler();
      final receiverPort = ReceivePort();
      isolateHandler.spawn(_deviceSearchIsolate,
          onReceive: (List<String> deviceList) {
            foundDevices = deviceList;
            receiverPort.sendPort.send("exit");
            isolateHandler.kill("DeviceSearch", priority: Isolate.immediate);
          },
          name: "DeviceSearch",
          onInitialized: () => isolateHandler.send(ip, to: "DeviceSearch"));
      await receiverPort.first;
      return foundDevices;
    });
  }
```

```dart
  // 获取设备名称
  static Future<String> getDeviceName() async {
    final response = await _makeRequest(
      WhaleyRoutes.get,
      payload: {
        "Action": "getDeviceName",
      },
      timeout: const Duration(seconds: 60),
    );
    return response.body;
  }

  // 获取已安装的应用列表
  static Future<String> getTvAppList() async {
    final response = await _makeRequest(
      WhaleyRoutes.get,
      payload: {
        "Action": "getTvAppList",
      },
      timeout: const Duration(seconds: 60),
    );
    return response.body;
  }

  // 发送按键
  static Future<String> sendKeyEvent(int event) async {
    final response = await _makeRequest(
      WhaleyRoutes.get,
      payload: {
        "Action": "SentKey",
        "Event": event,
      },
      timeout: const Duration(seconds: 60),
    );
    return response.body;
  }

  // 截屏
  static Future<String> screenshot() async {
    final response = await _makeRequest(
      WhaleyRoutes.get,
      payload: {
        "Action": "ScreenShot",
        "VersionCode": 200,
      },
      timeout: const Duration(seconds: 60),
    );
    return response.body;
  }

  // 打开应用
  static Future<String> openApp(String packageName) async {
    final response = await _makeRequest(
      WhaleyRoutes.get,
      payload: {
        "Action": "openApp",
        "packageName": packageName,
      },
      timeout: const Duration(seconds: 60),
    );
    return response.body;
  }
```

## 使用工具

- `Proxybin`：抓包工具，用于分析网络请求
- `Flutter`：跨平台移动应用开发框架
## 关键依赖包

- `network_info_plus`：用于获取设备网络信息，比如当前 WiFi 名称、连接的热点 BSSID、当前 IP 地址等。
- `network_tools_flutter`：提供了网络发现、端口扫描等功能。
- `http`：Dart 的 HTTP 客户端，用来发起 HTTP 网络请求。
# 成果展示

经过一番努力，我终于完成了遥控器 App 的开发。现在我可以用新手机来控制电视了。下面是 App 的运行截图。

# 总结

通过这次开发，我感受了 AI 编程助手的强大功能。ChatGPT 帮助我解决了一些编程问题，比如如何选择合适的依赖包，如何实现某个功能等。Github Copilot 帮助我生成了一些高质量的代码和界面布局。这些都让我的开发更加轻松和高效。