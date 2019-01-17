# 现金收费反馈

接口定义方:唯智

## 接口概述

  CMS通过订单编号和客户查询OWB系统的计费接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式

## 接口地址  
  
  * 测试地址:https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/cashChargeInfoStatus
  * 请求方法:POST
  * 请求头部:application/json
  * 请求Token:21596b33a4875896
  
## 参数说明
  
  Data:对外系统post给OWB系统的JSON格式报文
  
  ```json
{
  "busicode":"busicode",
  "workCode": "工单号",
  "customerCode":"客户编号"
  "billingDetail": [{
			"id": "清单行唯一ID",
			"type":"费用项",
			"qty": "金额",
			"reserve1": "",
			"reserve2": "",
			"reserve3": ""
		},
		{
			"id": "清单行唯一ID",
			"type":"费用项",
			"qty": "金额",
			"reserve1": "",
			"reserve2": "",
			"reserve3": ""
		}]
}
```
  
返回内容:
```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": "busicode"
}
```

