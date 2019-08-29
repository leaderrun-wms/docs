# 客户信息接口

接口定义方：唯智

## 接口概述

  CMS模糊查询OWB系统客户，OWB系统将客信息反馈CMS

## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTPS调用方式,报文采用 JSON格式
  
## 接口地址  
  
  * 测试地址：https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/findBaseCustomer
  * 请求方法：POST
  * 请求头部：application/json
  * 请求Token：21596b33a4875896
  
## 参数说明
  
  Data：对外系统post给OWB系统的JSON格式报文 
  
  内容：
   ```json
{
	"busicode": "年月日时分秒+6位随机数",
	"customerType": "客户类型（大客户||小客户）",
  "customerCode": "客户编码（如果类型是小客户需传入大客户编码）",
  "customerName": "客户名称"
  
}
```
      	 
返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "customerDetail": [{
        "customerName": "客户名称",
        "customerCode": "客户编码",
	"is_edi": "true"
    },
    {
        "customerName": "客户名称",
        "customerCode": "客户编码",
	"is_edi": "false"
    }]
}
```
