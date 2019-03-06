# 入库订单接口

接口定义方：唯智

## 接口概述

  CMS将放行成功的ASN信息传到OWB系统，OWB系统根据ASN信息生成入库入库订单

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/InbaseOderInfo  
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
	"workCode": "工单号",
	"customerCode": "订单客户编号",
	"paymentCode": "付款方编号",
	"consignorConsigneeCode": "Crm工厂",
	"consignorConsigneeName": "Crm工厂名称",
	"consignorConsigneeEmail": "Crm工厂",
	"volume": "体积",
	"weight": "毛重",
	"arriveDate": "预计到仓时间",
	"status":"状态",
	"driver_name":"司机姓名",
	"reserve1": "",
	"reserve2": "",
	"carDetail":[{
			"license_plate_no":"车牌号",
			"truck_type":"车型"
		},
		{	
			"license_plate_no":"车牌号",
			"truck_type":"车型"	
		}
	],	
	"oderDetail": [{
			"id": "清单行唯一ID",
			"so": "SO",
			"po": "PO",
			"item": "ITEM",
			"unit": "体积计算标识",
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
			"extend1": "混板编号",
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
			"unit": "体积计算标识",
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
			"extend1": "混板编号",
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
		  "lines":"行数",
		  "name":"品名"
	      },
	      {
	          "id":"报关单ID",
		  "lines":"行数",
		   "name":"品名"
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
 * CMS创建工单时推送信息到OWB系统，状态为new
 * CMS修改工单时推送信息到OWB系统，状态为update
 * CMS删除工单时推送信息到OWB系统，状态为delete
 * CMS接单后（接单窗口完成接单）再次推送信息给OWB系统，状态为active，CMS接单后不允许对工单进行修改和删除操作
 * 时间格式 yyyy-MM-dd HH:mm:ss
 * 车型，CMB数量，司机姓名，车牌号新建传入可以非必填
 

