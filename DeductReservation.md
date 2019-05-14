# 扣减预约方数接口

接口定义方：唯智

## 接口概述

  FD校验工单信息后将需预约时间和CBM信息推送给OWB进行方数扣减

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/deductReservation  
  * 请求方法：POST
  * 请求头部：application/json
  * 头部Token:21596b33a4875896
  
## 参数说明
  
  Data：对外系统通过HTTP的post方式给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "appointmentId": "预约ID",
  "appointmentCbm": "CBM（工单所有ASN的总方数）",
  "reserve1": "",
  "reserve2":"",
  "reserve3":"",
  "reserve4":"",
  "reserve5":""
	
}

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": "busicode"
}
```
