# inbound.finished (入仓卸货)

## 消息体格式

| 字段           | 描述              | 样本             |
|----------------|------------------|---------------   |
| orderNumber    | 入库单号          |IPLA200300001    |
| customerCode   | 收货方代码        | KN-ACCO         |
| storageDate    | 收货日期          |2020-06-05       |
| inboundType    | 收货模式          | PDA / 导入      |
| soInfos        |                  |                 |
| soCode         |  SO              |4363-9188-001.123|
| poCode         |  PO              |4363-9188-001    |
| itemCode       |  ITEM            |4363-9188        |
| packs          |                  |                 |
| unit           | 包装单位          |CTN / PLT        |
| qty            | 包装数量          | 56              |
| pcsQty         | pcs数            | 112              |
| actualCbm      | 实际体积          | 1.2             |
| actualWgt      | 实际毛重          | 300              |


## 样本

```json
{
    "orderNumber":"IPLA200300001",
    "customerCode":"KN-ACCO",
    "storageDate":"2020-06-05",
    "inboundType":"PDA",
    "soInfos":[
        {
            "soCode":"4363-9188-001.123",
            "poCode":"4363-9188-001",
            "itemCode":"4363-9188",
            "packs":[
                {
                    "unit":"CTN",
                    "qty":"25.0",
                    "pcsQty":"25.0",
                    "actualCbm":"25.0",
                    "actualWgt":"25.0"
                },
                {
                    "unit":"PLT",
                    "qty":"5.0",
                    "pcsQty":"25.0",
                    "actualCbm":"25.0",
                    "actualWgt":"25.0"
                }
            ]
        },
        {
            "soCode":"4363-9188-001.124",
            "poCode":"4363-9188-001",
            "itemCode":"4363-9188",
            "packs":[
                {
                    "unit":"CTN",
                    "qty":"20.0",
                    "pcsQty":"25.0",
                    "actualCbm":"25.0",
                    "actualWgt":"25.0"
                }
            ]
        }
    ]
}
```
