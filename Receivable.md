# 现金收费

接口定义方：唯智

## 接口概述

  CMS通过订单编号和客户查询OWB系统的计费接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用 JSON格式

## 接口地址  
  
  * 测试地址：http://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/cashChargeInfo
  * 请求方法：POST
  * 请求头部：application/json
  
## 参数说明
  
  Data：对外系统通过HTTP的post方式给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "warehouseCode": "仓库编号",
  "asnCode": "ASN编号",
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
  "asnCode": "ASN编号",
  "customerCode": "客户编号" ,  
  "billingDetail": [{
			"id": "清单行唯一ID",
			"type":"费用项",
			"qty": "金额",
	                "extend1": "",
			"extend2": "",
			"extend3": ""
		},
		{
			"id": "清单行唯一ID",
			"type":"费用项",
			"qty": "金额",
	                "extend1": "",
			"extend2": "",
			"extend3": ""
		}]
}
```
  
