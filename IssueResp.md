# OWB接收异常通知

接口定义方:唯智

## 接口概述

  FD在异常发生后，创建Issue后通知OWB相关的异常ID
  
## 功能描述

  对外系统接口调用OWB系统接口采用基于HTTP调用方式,报文采用JSON格式

## 接口地址  
  
  * 测试地址:https://14.29.237.141:9090/leaderrun_edi/servlet/leaderrunServiceToCMS/issueResp
  * 请求方法:POST
  * 请求头部:application/json
  * 请求Token:21596b33a4875896
  
## 参数说明
  
  Data:对外系统post给OWB系统的JSON格式报文
  
  ```json
{
  "busicode":"busicode",
  "issueid": "ISSUE ID"
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

