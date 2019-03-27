# 关务锁接口

接口定义方:唯智

## 接口概述

  CMS锁单时主动调用OWB系统的异常锁单接口
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用JSON格式

## 接口地址  
  
  * 测试地址:https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/IssueResp
  * 请求方法:POST
  * 请求头部:application/json
  * 请求Token:21596b33a4875896
  
## 参数说明
  
  Data:对外系统post给OWB系统的JSON格式报文
  
  ```json
{
  "busicode":"busicode",
  "issueid": "CMS创建的ISSUE的唯一ID",
  "ItenId": ["ItemID1", "ItemID2", "ItemID3", "ItemID4"]
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

