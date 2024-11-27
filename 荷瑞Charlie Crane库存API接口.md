# 荷瑞Charlie Crane库存API接口

接口定义方：唯智

## 接口概述

  客人调用WMSAPI接口，WMS返回对应信息给到客人

## 功能描述

  对外系统接口调用接口采用基于HTTPS调用方式,报文采用JSON格式
  调用时返回对应客户的全量数据
  
## 接口地址  
  
  * 测试地址：https://xxx/Charlie_Crane_inventory 
  * 请求方法：GET
  * 请求头部：application/json
  * 头部Token:
  * 接口名称: Charlie_Crane_inventory
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json

   ```
      	 
返回内容：

```json
{
    "total": 2,
    "rows": [{
		"item": "3760287005903",//Item
		"name": "棉座椅垫",//报关品名 dec_itemname
		"qty": 10,//可用库存数量
		"unit": "箱",//单位：箱/板/PCS
		"spec": "74*40*28"//规格    
	     },
	     {
		"item": "3760287005902",//Item
		"name": "棉座椅垫",//报关品名 dec_itemname
		"qty": 10,//可用库存数量
		"unit": "箱",//单位：箱/板/PCS
		"spec": "74*40*29"//规格   
	     }],
    "code": 200,
    "msg": ""//查询成功或失败的信息
    
}
```
备注:
 * 查询客户为：荷瑞的可用库存
 * 可用库存数量按item，单位unit，规格spec作汇总
