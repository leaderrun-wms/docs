# 入库订单接口

接口定义方：唯智

## 接口概述

  CMS将放行成功的ASN信息传到OWB系统，OWB系统根据ASN信息生成入库入库订单

## 功能描述

  对外系统接口调用OWB系统接口采用基于WebService调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：http://localhost:8085/leaderrun_edi/servlet/leaderrunServiceToCMS/InbaseOderInfo
  * 请求方法：POST
  * 请求头部：application/json
  
## 参数说明
  
  Data：对外系统post给云仓系统的JSON格式报文 
  
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"warehouseCode": "仓库编号",
	"ASNCode": "ASN单号",
	"customerCode": "客户编号",
	"consignorConsigneeCode": "Crm工厂",
	"volume": "体积",
	"weight": "毛重",
	"arriveDate": "预计到仓时间",
	"reserve1": "",
	"reserve2": "",
	"reserve3": "",
	"reserve4": "",
	"reserve5": "",
	"reserve6": "",
	"reserve7": "",
	"reserve8": "",
	"reserve9": "",
	"reserve10": "",
	"oderDetail": [{
			"id": "清单行唯一ID",
			"SO": "SO",
			"PO": "PO",
			"ITEM": "ITEM",
			"unti": "包装单位",
			"panelQty": "板数",
			"boxQty": "箱数",
			"qty": "pcs数量",
			"captain": "长",
			"wide": "宽",
			"high": "高",
			"volume": "体积",
			"weight": "重量",
			"extend1": "",
			"extend2": "",
			"extend3": "",
			"extend4": "",
			"extend5": "",
			"extend6": "",
			"extend7": "",
			"extend8": "",
			"extend9": "",
			"extend10": ""
		},
		{
			"id": "清单行唯一ID",
			"SO": "SO",
			"PO": "PO",
			"ITEM": "ITEM",
			"unti": "包装单位",
			"panelQty": "板数",
			"boxQty": "箱数",
			"qty": "pcs数量",
			"captain": "长",
			"wide": "宽",
			"high": "高",
			"volume": "体积",
			"weight": "重量",
			"extend1": "",
			"extend2": "",
			"extend3": "",
			"extend4": "",
			"extend5": "",
			"extend6": "",
			"extend7": "",
			"extend8": "",
			"extend9": "",
			"extend10": ""
		}
	],
	"customsDetail": [{
			"id": "清单行唯一ID",
			"url": "报关单链接"
		},
		{
			"id": "清单行唯一ID",
			"url": "报关单链接"
		},
		{
			"id": "清单行唯一ID",
			"url": "报关单链接"
		}
	]
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": {
        "processId": "busicode"
    }
}
```
