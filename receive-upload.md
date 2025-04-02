# 收货完成上传接口

接口定义方：唯智

## 接口概述

  WMS收货工单状态为完成时，上传收货数据给ASN

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：
  
## 参数说明
  
  Data：对外系统post给ASN系统的JSON格式报文 
  
  内容：
   ```json
{
	"orderno": "收货工单号",
  "asnDetail": [{
     "asnno": "ASN号",
     "ctn": "箱数",
     "panel": "板数",
     "pcsqty": "PCS数量",
     "weight": "实际重量"  
    },
    {
     "asnno": "ASN号",
     "ctn": "箱数",
     "panel": "板数",
     "pcsqty": "PCS数量",
     "weight": "实际重量"  
    }]
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息"
}
```
