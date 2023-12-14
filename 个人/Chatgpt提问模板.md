# 全局规则
严格按照步骤编写，不要遗漏任何请求参数，使用中文输出结果
# 查询接口
## 请求命令
``` bash
curl -X POST 'https://www.niankawang.com/ec/router' \
   --data '_method=travel.ec.wareApptShow.list.get&_v=1.0&_appKey=000001&_format=json&_locale=zh&_timestamp=20231214210153&_sessionId=wx_VISITOR_oXYF65b34VQ7W3Veiq4bGaLQKqTI&wxAppId=wx981dad825bf3014c&wxAgentId=&ownerId=wx6f7350d9e062d8c6&wxType=mini&personType=VISITOR&sceneId=DF3810BA57DE42DEA1953107F01F937A&programmeId=64D3205C266846149C11DEE4A9D6CAC5&apptDate=&lessApptDate=20231220&excludeDay=20231214&wareId=439F42CDA4024D9B843DF43E14897EA8&_sign=0B596A176245754231477FE2BA8A3A3C1EF70591' \
  --compressed
```
## 响应内容：
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
# 发送微信通知接口
## 提交地址
http://www.pushplus.plus/send
## 提交JSON内容
```json
 {
	'token': 'b3ebe73619e5428a9c55fc4767b813f4',
	'title': '鹭江夜游余票通知',
	'content': '班次{showTime} 剩余票数: {remainCount}<br />',
	'template': 'html'
}
```
# 华为云函数模板
``` python
def my_initializer(context):
    # 编写代码
```
# 参考华为云函数模板编写python脚本
1. 发送查询请求
2. 将响应内容进行jie'xi收到的JSON格式的响应进行遍历
3. 从每个项目中提取信息showTime、remainCount，进行条件判断，检查showTime是否为'1940'，以及是否有余票（remainCount > 0），如果条件满足，发送到通知。
