### 起因

前几天一位朋友提出了一个问题，能否通过AI生成相应的代码。于是我决定演示一下如何提问AI，引导它生成符合我们需求的Python脚本。
> 这里我拿一个日常生活中的例子，有一天决定明天晚上去鹭江夜游。然后就打开厦门旅游年卡小程序，准备预约。然而，让我没想到的是竟然已经预约满了。但是想到明天可能会有一些人退票，于是，我思考着是否可以写一个脚本的念头，用来定时查询余票，有余票时即时通知我。

### 准备工作

为了实现这个自动查询的脚本，需要使用Proxypin抓包工具，获取所需数据。打开厦门旅游年卡小程序，进行了一次请求包的抓取，成功地获取了一份请求包的详细内容。
这里我们导出cURL命令格式
![632shots_so.png](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312150000181.png)

### 分析抓包数据

通过Proxypin抓包工具获取到的数据包含了大量信息，但我们主要关注的是JSON数据。其中，关键字段如班次（showTime）、余票数量（remainCount），将成为我们编写脚本的基础数据。
```json
[
    {
        "seqId": 50098,
        "dataState": "1",
        "sendState": "0",
        "createTime": "20231213162050",
        "updateTime": "20231214160503",
        "showId": "cd208ab48c3a5ed2e45f4a0d6ebe281a",
        "showCode": "19：05班次",
        "showName": "19：05班次",
        "wareApptId": "914BDC495F1C4E88BAF40DB4BF168B9F",
        "sceneId": "DF3810BA57DE42DEA1953107F01F937A",
        "programmeId": "64D3205C266846149C11DEE4A9D6CAC5",
        "apptDate": "20231215",
        "showTime": "1905",
        "apptCount": 70,
        "reservedCount": 3,
        "remainCount": 67,
        "weekDay": "周五",
        "apptShowType": "2",
        "version": "20231214160503525",
        "wareId": "439F42CDA4024D9B843DF43E14897EA8",
        "showEndTime": "2015",
        "checkTicketStartTime": "1805",
        "checkTicketEndTime": "1910",
        "auditState": "1"
    }
]
```
### 编写脚本思路

基于抓包数据的分析，我设计了一个简单的脚本思路。通过使用华为云函数(免费白嫖)部署一个脚本，配置定时器发送请求，遍历返回的数据，判断班次（showTime）是否为19:05，并检查余票数量（remainCount）是否大于0。如果满足条件，通过调用推送加(免费白嫖)接口发送微信通知到我的微信。
![image.png](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312142334996.png)

### 创建指令
接下来，我们可以按照这个思路，编写一个Chatgpt能理解的指令，虽然指令看似很长，实际可以作为以后其他脚本的模板，只需要提供对应的信息，即可轻松生成我们所需要的脚本

[[Chatgpt提问模板]]

### 演示
![image.png](https://cdn.jsdelivr.net/gh/youyiying/blogs@master/images/202312142352564.png)

### 结语

