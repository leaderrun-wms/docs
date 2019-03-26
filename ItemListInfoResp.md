# 货物清单反馈接口

接口定义方:唯智

## 接口概述

  CMS通过清单行唯一ID（OWB返回的）查询OWB系统的货物清单反馈接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用JSON格式

## 接口地址  
  
  * 测试地址:https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/ItemListInfoResp
  * 请求方法:POST
  * 请求头部:application/json
  * 请求Token:21596b33a4875896
  
## 参数说明
  
  Data:对外系统post给OWB系统的JSON格式报文
  
  ```json
{
  "busicode":"busicode",
  "owbItemId": "OWB的清关行唯一ID",
  "itemDetail": {
	"id": "CMS清单行唯一ID",
	"so": "S/O",
	"po": "P/O#",
	"item": "ITEM#",
	"unit": "体积计算标准（CTN/PLT）",
	"panelQty": "板数",
	"boxQty": "箱数",
	"qty": "pcs数量",
	"captain": "长(cm)",
	"wide": "宽(cm)",
	"high": "高(cm)",
	"volume": "体积(CBM)",
	"weight": "毛重（KG）",
	"nweight": "净重（KG）",
	"sizeChildPO":"Size/Child PO",
	"scpBnoGno":"SCP#/BookingNO/GTN NO",
	"territoryCode":"Territory code(Location)",
	"supplierPack":"Description of goods/Supplier Pack",
	"supplierItemColor":"Supplier Item#/Color/Pack ID/Lot#",
	"mixedBOx":"混装编号",
	"mixedPallet":"混板编号",
	"style":"STYLE(VPN#)",
	"issplit":"是否拆装",
	"spare":"备品",
	"extend1": "",
	"extend2": "",
	"extend3": "",
	"extend4": "",
	extend5": ""
   }
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

