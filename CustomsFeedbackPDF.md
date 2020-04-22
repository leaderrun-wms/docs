# 报关单反馈

接口定义方：唯智

## 接口概述

    报关单创建后CMS 传递给 OWB

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/customsDeclarationInfo
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
	"status": "状态(入库||出库)"
	"customsDetail": [{
			"id": "报关单ID",
			"ledgerId": "核注清单号",
			"url": "报关单链接",
			"remark": "备注"
		},
		{
			"id": "报关单ID",
			"ledgerId": "核注清单号",
			"url": "报关单链接",
			"remark": "备注"
		},
		{
			"id": "报关单ID",
			"ledgerId": "核注清单号",
			"url": "报关单链接",
			"remark": "备注"
		}
	]
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": "busicode"
}
```
