# 现金收费

接口定义方：唯智

## 接口概述

  CMS通过订单编号和客户查询OWB系统的计费接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式

## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/cashChargeInfo
  * 请求方法：POST
  * 请求头部：application/json
  
## 参数说明
  
  Data：对外系统通过HTTP的post方式给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "warehouseCode": "仓库编号",
  "workCode": "工单号",
  "customerCode": "客户编号"
  "reserve1": "",
  "reserve2":"",
  "reserve3":"",
  "reserve4":"",
  "reserve5":""
	
}
```
  
返回内容：

```json
{
  "busicode":"busicode",
  "workCode": "工单号",
  "status":"1-正常费用/2-正常无费用/3-异常无费用",
  "customerCode": "客户编号" ,  
  "billingDetail": [{
			"id": "费用ID",
			"type":"费用项",
			"qty": "金额",
                        "quantity": "数量",
	                "transactionNo": "交易号",
			"chargeStatus": "收费状态",
			"tollCollector": “收费人",
			"chargeTime": "收费时间，格式:yyyy-MM-dd hh:mm:ss"
		},
		{
			"id": "费用ID",
			"type":"费用项",
			"qty": "金额",
                        "quantity": "数量",
	                "transactionNo": "交易号",
			"chargeStatus": "收费状态",
			"tollCollector": “收费人",
			"chargeTime": "收费时间，格式:yyyy-MM-dd hh:mm:ss"
		}]
}
```

备注：
1.status的状态值说明：
 * 当status=4，OWB无现金无月结费用，属于异常状态，CMS需控制不允许下一步操作；
 * 当status=3，OWB纯月结费用且CMS已做纯月结缴费确认，CMS需控制不允许再执行纯月结费用缴费；
 * 当status=2，OWB纯月结费用，即无现金费用且有纯月结费用，CMS需做纯月结费用缴费确认，即第一次纯月结费用缴费确认；
 * 当status=1，OWB纯现金费用，CMS需做纯现金缴费确认。
2.传值说明：
 * 每次查询WMS需将该单的已缴费和生效且未缴费的现金费用项全部传输给CMS，CMS用于缴费和打印小票
