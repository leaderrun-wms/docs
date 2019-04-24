# 交仓预约接口

接口定义方：慧通关

- 具体 ASN_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

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
	"etaInterval": "20:00 - 21:00" //预约时间区间
	"cars": [
				{
					"licensePlateNo": "车牌",
					"truckType": "车型",
					"driverName": "司机姓名",
					"driverMobile": "司机电话"
				}
			],
	"asnIds": ['ASNXXXXX','ASNXXXXX','ASNXXXXX'],
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
	"etaInterval": "18:00 - 19:00" //预约时间区间
	"cars": [
				{
					"licensePlateNo": "车牌",
					"truckType": "车型",
					"driverName": "司机姓名",
					"driverMobile": "司机电话"
				}
			],
	"asnIds": ['ASNXXXXX','ASNXXXXX'],
}
```

返回内容：

```json
{

    "success": true,
    "message": "若success为false时候的错误信息",
	"result": null
}