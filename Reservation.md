# 预约时间查询接口

接口定义方：唯智

## 接口概述

  FD通过仓库、客户和CBM查询OWB系统可预约时间段
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式

## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/reservation
  * 请求方法：POST
  * 请求头部：application/json
  
## 参数说明
  
  Data：对外系统通过HTTP的post方式给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "warehouseCode": "仓库编号",
  "customerCode": "客户编码",
  "appointmentCbm": "CBM（工单所有ASN的总方数）"
}
```
  
返回内容：

```json
{
  
  "success": "true",
  "message": "若success为false时候的错误信息",
  "result":{
  	"busicode":"busicode",
	"timeSlots": [{
			"appointmentId": "预约ID",
			"eta":"预约日期",
			"etaInterval": "预约时间段"

		},
		{
			"appointmentId": "预约ID",
			"eta":"预约日期",
			"etaInterval": "预约时间段"
		}]
  }  
}
```
备注：
1、请求参数warehouseCode、customerCode、appointmentCbm都必填，否则OWB返回false;
