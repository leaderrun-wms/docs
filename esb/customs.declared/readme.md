# customs.declared (已申报海关)

## 消息体格式

| 字段          | 描述                     | 样本          |
|---------------|--------------------------|---------------|
| declarationId | 报关单系统唯一号码       | UUID          |
| warehouseCode | 仓库代码                 | PLA           |
| refNo         | 关联号码 (ASN或出库单号) | ASN2006001234 |
| refType       | 关联单证类型             | ASN           |
| declaredAt    | 申报时间                 | 1592982477000 |
| declaration   | 申报内容                 |               |

## 样本

```json
{
    "declarationId": "1f3e28efe64a40e59a64fa96ec6f33af",
    "warehouseCode": "PLA",
    "refNo": "ASN2006001234",
    "refType": "ASN",
    "declaredAt": 1592982477000,
    "declaration": {
        "header": {},
        "detail": [
            {}, {}, {}
        ]
    }
}
```
