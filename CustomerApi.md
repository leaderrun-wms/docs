# 荷瑞API接口

接口定义方：唯智

## 接口概述

  客人调用WMSAPI接口，WMS返回对应信息给到客人

## 功能描述

  对外系统接口调用接口采用基于HTTPS调用方式,报文采用JSON格式
  
## 接口地址  
  
  * 测试地址： 
  * 请求方法：POST
  * 请求头部：application/json
  * 头部Token:
  * 接口名称: HoRuiApi
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json

   ```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result":{
        "decls": [{
			    	"Itemcode": "3760287005903",//Item
				"ItemName": "棉座椅垫",//报关品名 dec_itemname
				"Unit": "箱",//单位：箱/板/PCS
				"Qty": 10,//可用库存数量
				"Spec": "74*40*28"//规格    
        }]
    }
}
```
备注:
 * 查询客户为：荷瑞的可用库存
 * 可用库存数量按ItemCode，单位Unit，规格Spec作汇总
