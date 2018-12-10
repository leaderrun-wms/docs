# 现金收费反馈

接口定义方:唯智

## 接口概述

  CMS通过订单编号和客户查询OWB系统的计费接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用 JSON格式

## 接口地址  
  
  * 测试地址:http://localhost:8085/leaderrun_edi/servlet/leaderrunServiceToCMS/cashChargeInfoStatus
  * 请求方法:POST
  * 请求头部:application/json
  
## 参数说明
  
  Data:对外系统post给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "warehouseCode": "仓库编号",
	"ASNcode": "ASN编号",
  "customerCode": "客户编号",
	"reserve1":"",
	"reserve2":"",
	"reserve3":"",
	"reserve4":"",
	"reserve5":"",
	"reserve6":"",
	"reserve7":"",
	"reserve8":"",
	"reserve9":"",
	"reserve10":""
	
}
```
  
返回内容:

```json
{
  "warehouseCode": "仓库编号",
  "ASNcode": "ASN编号",
  "customerCode": "客户编号" ,  
	"calculatedCharge":"金额",
	"status":"状态",
	"extend1": "",
	"extend2": "",
	"extend3": "",
	"extend4": "",
	"extend5": "",
	"extend6": "",
	"extend7": "",
	"extend8": "",
	"extend9": "",
	"extend10": ""
}
```
