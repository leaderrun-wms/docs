# 单证状态接口

接口定义方：唯智

## 接口概述

    报关完成后CMS 传递给 OWB

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/customsDeclarationStatus
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：21596b33a4875896
  
 
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"warehouseCode": "仓库编号",
	"workCode": "工单号",
	"customerCode": "客户编号"
	"customsDetail": [{
			"id": "报关单号",
			"status":"状态"
		},
		{
			"id": "报关单号",
			"status":"状态"
		},
		{
			"id": "报关单号",
			"status":"状态"
		}
	]
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
1.云报关系统报关单状态更新，每次只需推送报关单最新的状态给WMS系统
