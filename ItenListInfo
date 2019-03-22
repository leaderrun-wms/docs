# 异常货物清单查询接口

接口定义方：唯智

## 接口概述

  CMS通过清单行唯一ID查询OWB系统的异常货物清单接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用JSON格式

## 接口地址  
  
  * 测试地址：http://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/ItemListInfo
  * 请求方法：POST
  * 请求头部：application/json
  * 头部Token:21596b33a4875896
  
## 参数说明
  
  Data：对外系统通过HTTP的post方式给OWB系统的JSON格式报文
  
  ```json
{
  "busicode": "年月日时分秒+6位随机数",   
  "cmsItemId": "CMS清关行唯一ID"
}
```
  
返回内容：

```json
{
    "busicode": "busicode",
    "cmsItemId": "CMS清关行唯一ID",
    "Items": [
        {
            "id": "清单行唯一ID",
            "so": "so",
            "po": "po",
            "item": "item",
            "unit": "包装单位",
            "qty": "实际收货数量",
            "extend1": "",
            "extend2": "",
            "extend3": "",
            "extend4": "",
            "extend5": ""
        } ,
        {
            "id": "清单行唯一ID",
            "so": "so",
            "po": "po",
            "item": "item",
            "unit": "包装单位",
            "qty": "实际收货数量",
            "extend1": "",
            "extend2": "",
            "extend3": "",
            "extend4": "",
            "extend5": ""
        }
    ]
}
```
