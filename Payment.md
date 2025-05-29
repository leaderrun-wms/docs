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
  "customerCode": "客户编号",
  "status": "1/2/3/4/5/6",
  "chargingmethod": "扫码支付/刷卡支付/现金支付/银行转账",## 收费方式
  "transferor": "转账人",
  "billingDetail": [{
			"id": "费用ID",
			"type":"费用项",
			"qty": "金额",
			"reserve1": "收费人",
			"reserve2": "收费时间，格式：yyyy-MM-dd hh:mm:ss",
			"reserve3": "交易号",
			"reserve4": "转账交易号",
			"reserve5": "退款原因",
			"reserve6": "备用字段",
			"reserve7": "备用字段"
		},
		{
			"id": "费用ID",
			"type":"费用项",
			"qty": "金额",
			"reserve1": "收费人",
			"reserve2": "收费时间，格式:yyyy-MM-dd hh:mm:ss",
			"reserve3": "交易号",
			"reserve4": "转账交易号",
			"reserve5": "退款原因",
			"reserve6": "备用字段",
			"reserve7": "备用字段"
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

备注：CMS现金缴费，只推送本次缴费的现金费用项目，原已缴费现金项目不再推送给WMS。
  *接口增加状态（status）值：5，用于处理发票类型（主要是电子发票），每次申请电子发票成功后云报关将本次申请成功的所有明细推送给WMS系统，已推送的不再重复推送。
  *接口增加状态（status）值：6，用于处理退款业务。
