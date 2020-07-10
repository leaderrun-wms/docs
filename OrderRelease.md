# 订单放行接口(终)

接口定义方：唯智

## 接口概述

    CMS确认ASN单可放行后CMS 传递给 OWB

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/orderRelease
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：21596b33a4875896
  
 
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
    
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"releaseType": "订单类型",
        "workCode": "工单号/流水号",
	"releaseStatus":"已放行 || 未放行（已下发）||已终审||通关无纸化查验||核放单查验"
}
```
      	 
返回内容：

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result":  "busicode"
}
```
备注：
一、releaseType订单类型：IN-入库订单；OUT-出库订单

二、releaseStatus

  1-入库订单的状态说明
    1）放行状态：已放行/未放行（已下发）；
    2）账册状态：已终审；
    3）查验状态：通关无纸化查验
    4）核放单状态：核放单查验

 2-出库订单状态说明
    1)放行状态：已放行
