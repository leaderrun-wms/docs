# 工单收货信息反馈

接口定义方：慧通关

## 功能描述



## 接口详情

### 货物出库请求

路径：

```
    https://LHFD_HOST/api/asn/<ASNID>/properties
```

* 具体ASN_HOST的配置在首页的环境栏目中描述
* 测试环境使用http协议，生产环境使用https加密协议
* ASNID：ASN单号在URL路径名称中

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：PUT

内容：

```json
{
    "properties": [
        {
            "key": "WAYBILL_NO",
            "value": "运单号 W000001"
        },
        {
            "key": "TRUCK_TYPE",
            "value": "10吨车"
        },
        {
            "key": "LICENSE_PLATE_NO",
            "value": "粤B12345"
        },
        {
            "key": "DRIVER_NAME",
            "value": "王小虎"
        }
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
}
```
