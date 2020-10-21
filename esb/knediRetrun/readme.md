# edi处理反馈接口

接口定义方：唯智

## 接口概述

    云报关将入仓卸货和出仓装柜成功推送KN EDI后，需将EDI处理结果反馈给OWB系统

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/knediRetrun
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：21596b33a4875896
  
 
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",	
	"workCode": "入库单号/出库单号",
  "soCode": "SO",
	"status":"状态"		
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result":  "busicode"
}
```
备注：
1.云报关系统接收到KN EDI的处理结果后需反馈给OWB系统
