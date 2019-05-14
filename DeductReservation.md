# 扣减预约方数接口

接口定义方：唯智

## 接口概述

  FD校验工单订单信息后将需预约时间和CBM信息推送给OWB进行方数扣减

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/deductReservation  
  * 请求方法：POST
  * 请求头部：application/json
  * 头部Token:21596b33a4875896
  
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
请求方法：POST

请求内容：applicatin/json

```json
{
	"asnIds": ["ASNXXXXX","ASNXXXXX","ASNXXXXX"]
}
```

返回内容：

```json
{
    "success": true, 
    "message": "若success为false时候的错误信息",
    "result": [{ // success为true返回
			"asnId": "ASNXXXXX",
			"cbm": "1234",
			"warehouse": "PLC",
			"customer": {
				"customerCode": "大客code",
				"customerName": "大客",
				"childrenCustomerCode": "子客Code",
				"childrenCustomerName": "子客"
			}
		}]
}
```


## 创建交仓预约

路径：

```
    https://ASN_HOST/api/appointment
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：applicatin/json

```json
{

	"appointmentId": "预约id",
	"eta": 1555999135000, //预约时间
	"etaInterval": "20:00 - 21:00", //预约时间区间
	"cars": [
				{
					"licensePlateNo": "车牌",
					"truckType": "车型",
					"driverName": "司机姓名",
					"driverMobile": "司机电话"
				}
			],
	"asnIds": ["ASNXXXXX","ASNXXXXX","ASNXXXXX"]
}
```

返回内容：

```json
{

    "success": true,
    "message": "若success为false时候的错误信息",
	"result": "返回工单号"
}
```

## 更新交仓预约


路径：

```
    https://ASN_HOST/api/appointment/<appointmentId>
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：PUT

请求内容：applicatin/json

```json
{

	"appointmentId": "预约id",
	"eta": 1555999135000, //预约时间
	"etaInterval": "18:00 - 19:00", //预约时间区间
	"cars": [
				{
					"licensePlateNo": "车牌",
					"truckType": "车型",
					"driverName": "司机姓名",
					"driverMobile": "司机电话"
				}
			],
	"asnIds": ["ASNXXXXX","ASNXXXXX"],
}
```

返回内容：

```json
{

    "success": true,
    "message": "若success为false时候的错误信息",
	"result": null
}
