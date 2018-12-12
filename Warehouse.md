# 仓库接口

接口定义方：唯智

## 接口概述

  CMS模糊查询OWB系统仓库，OWB系统将仓库信息反馈CMS

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：http://VTRADEX_HOST/leaderrun_edi/servlet/leaderrunServiceToCMS/WarehouseNameInfo
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
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "warehouseDetail": [{
        "warehouseName": "仓库名称",
        "warehouseCode": "仓库编码"
    },
    {
        "warehouseName": "仓库名称",
        "warehouseCode": "仓库编码"
    }]
}
```
