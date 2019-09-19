# FD接收异常通知

接口定义方：慧通关

- 具体 FD_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

## 入库通知异常ID

路径：

```
    https://FD_HOST/inbound/issue
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：applicatin/json

```json
ISSUEID
```

ISSUEID为异常中心创建异常后的异常ID

返回内容：无（状态200）

## 出库通知异常ID

路径：

```
    https://FD_HOST/outbound/issue
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：applicatin/json

```json
ISSUEID
```

ISSUEID为异常中心创建异常后的异常ID

返回内容：无（状态200）