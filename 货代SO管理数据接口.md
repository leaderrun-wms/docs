# edi booking import API

* 测试地址： http://omsbe.lh.yunbaoguan.cn:81/shipment
* 生产地址： https://lhomsbe.yunbaoguan.cn/shipment

## HTTP请求方法
* Method: POST
* HTTP Header: 
    * Authorization: ACCESS_KEY 5ljrfjEidYSl12lK2QLfLlGF4LisYsg4GiaJ
    * Content-Type: application/xml
* 参数说明 

|字段名| 类型 | 是否必填|说明|
|:---|:----|:---|:----|
|refName|string|否|文件名|
|customerId|string|是|客户id,eg.KN/Maersk/DB,严格区分大小写|
|body|byte[]|是|booking文件|

### 说明：
* Authorization头信息是用于验证调用者身份的钥匙，必填。若验证身份失败，将返回状态401 Unauthorized

## HTTP返回结果

* Content-Type: application/json
* Body样本（成功）:

```json
{
    "success": true,
    "message": null,
    "id": "021a0b6d-f477-4e31-b745-cc4c6aed41eb",
    "commReference": "HONS11706569",
    "logicalAddress": "HKHKG01",
    "physicalAddress": "KNLGT02",
    "email": "neck.chi@kuehne-nagel.com",
    "bookingNo": "4110072080504700"
}
```

* Body样本（失败）:

```json
{
    "success": false,
    "message": "asnId存在, 数据不能导入",
    "id": "021a0b6d-f477-4e31-b745-cc4c6aed41eb",
    "commReference": "HONS11706569",
    "logicalAddress": "HKHKG01",
    "physicalAddress": "KNLGT02",
    "email": "neck.chi@kuehne-nagel.com",
    "bookingNo": "4110072080504700"
}
```

### 说明

* success: true (成功) / false (失败)
* message: 非null表示在失败的情况下的相关错误信息
* id: 立航内部Booking ID

## 发送样例

### curl
```sh

# curl -d @src/test/resources/kn-samples/4363-9871-911.055.xml \
	-H 'Authorization: Access_Key 5ljrfjEidYSl12lK2QLfLlGF4LisYsg4GiaJ' \
	-H 'Content-Type: text/xml' \
	'http://omsbe.lh.yunbaoguan.cn:81/shipment?refName=4363-9871-911.055.xml&customerId=KN'

```
