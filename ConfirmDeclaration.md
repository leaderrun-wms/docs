# 出库报关单确认申报

接口定义方：慧通关

## 功能描述

* 检查运抵
* 执行申报

## 接口详情

### 货物出库请求

路径：

```
    https://FD_HOST/outbound/port-arrival-certificate
```

* 具体FD_HOST的配置在首页的环境栏目中描述
* 测试环境使用http协议，生产环境使用https加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

内容：

```json
{
    "processId": "启动出仓流程返回的ID",
    "portArrivalCertificateUrl":"http://www.dxx.der.com/dfdf.png" //还柜纸 （可选）
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息"
}
```

说明：

* Authorization头信息：
    * 立航负责在慧通关平台中生成此秘钥
    * 此秘钥是代表立航的身份
    * WMS是以立航的身份调用此接口
    * 在慧通关的所有接口，都需要这个头信息作身份验证
* processId（输入）：
    * 启动出仓流程，返回的流程 ID
  
