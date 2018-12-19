# 入库订单接口

接口定义方：唯智

## 接口概述

  CMS将放行成功的ASN信息传到OWB系统，OWB系统根据ASN信息生成入库入库订单

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用JSON格式
  
## 接口地址  
  
  * 测试地址：http://VTRADEX_HOST/leaderrun_edi/servlet/leaderrunServiceToCMS/InbaseOderInfo  
  * 请求方法：POST
  * 请求头部：application/json
  * 头部Token:21596b33a4875896
  
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"warehouseCode": "仓库编号",
	"aSNCode": "ASN单号",
	"customerCode": "订单客户编号",
	"paymentCode": "付款方编号",
	"consignorConsigneeCode": "Crm工厂",
	"consignorConsigneeName": "Crm工厂名称",
	"consignorConsigneeEmail": "Crm工厂",
	"volume": "体积",
	"weight": "毛重",
	"arriveDate": "预计到仓时间",
	"status":"状态",
	"reserve1": "",
	"reserve2": "",
	"oderDetail": [{
			"id": "清单行唯一ID",
			"so": "SO",
			"po": "PO",
			"item": "ITEM",
			"unti": "包装单位",
			"panelQty": "板数",
			"boxQty": "箱数",
			"qty": "pcs数量",
			"captain": "长",
			"wide": "宽",
			"high": "高",
			"volume": "体积",
			"weight": "重量",
			"sizeChildPO":"scp/bno/gno",
			"scpBnoGno":"",
			"territoryCode":"",
			"supplierPack":"",
			"supplierItemColor":"",
			"extend1": "",
			"extend2": "",
			"extend3": "",
			"extend4": "",
			"extend5": ""
		},
		{
			"id": "清单行唯一ID",
			"so": "SO",
			"po": "PO",
			"item": "ITEM",
			"unti": "包装单位",
			"panelQty": "板数",
			"boxQty": "箱数",
			"qty": "pcs数量",
			"captain": "长",
			"wide": "宽",
			"high": "高",
			"volume": "体积",
			"weight": "重量",
			"sizeChildPO":"scp/bno/gno",
			"scpBnoGno":"",
			"territoryCode":"",
			"supplierPack":"",
			"supplierItemColor":"",
			"extend1": "",
			"extend2": "",
			"extend3": "",
			"extend4": "",
			"extend5": ""
		}
	],
	"customsDeclaration": [{//报关单
	      "code":"报关单号",
	      "type":"清关||转关"
	      "customsDeclarationDetail": [{
	          "id":"报关单ID",
		  "lines":"行数"
	      },
	      {
	          "id":"报关单ID",
		  "lines":"行数"
	      }
	     }]
	}]
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result":"busicode"
    
}
```
备注:
 * CMS创建ASN时推送信息到OWB系统，状态为new
 * CMS放行ASN时推送信息到OWB系统，状态为update
 * CMS放行ASN时推送信息到OWB系统，状态为delete
 

