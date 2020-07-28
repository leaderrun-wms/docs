# outbound.sealed (出仓卸货)

## 消息体格式

| 字段           | 描述              | 样本            |
|----------------|------------------ |---------------  |
| orderNumber    | 出库库单号        |XPLAH200700417   |
| containerNumber| 柜号              | KDA-UUU-99      |
| outboundDate   | 装柜完成日期       |2020-06-05       |
| soCode         | SO               |4363-9188-001.123|
| unit           | 包装单位          |PCS / CTN / PLT  |
| packageQty     | 包装数量          | 56              |



## 样本

```json
{
    "orderNumber": "IPLA200300001",
    "containerNumber": "KDA-UUU-99"，
    "outboundDate": "2020-06-05",
    "soCode": "4363-9188-001.123",
    "unit": "PCS",
    "packageQty": "500"
}
```
