# 订单放行接口

接口定义方：唯智

## 接口概述

    CMS确认ASN单可放行后CMS 传递给 OWB

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：http://localhost:8085/leaderrun_edi/servlet/leaderrunServiceToCMS/inbaseOderRelease
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：21596b33a4875896
  
 
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
    
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"warehouseName": "仓库名称",
  "asnCode": "asnCode"
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
