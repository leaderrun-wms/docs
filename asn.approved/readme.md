# asn.approved (ASN审核通过)

## 消息体格式

| 字段           | 描述             | 样本          |
|----------------|------------------|---------------|
| asn            | ASN号码          | ASN2006001234 |
| customerCode   | 客户代码         | KN            |
| manifest       | 货物清单         |               |
| declarations   | 报关单(可以多份) |               |
| mappings       | 清单和报关单关系 |               |
| submittedOrgId | 提交公司ID       | 562           |
| submittedBy    | 提交公司名称     | 某某工厂      |
| submittedAt    | 提审时间         | 1592972477000 |
| approver       | 审核人           | 陈大文        |
| approvedAt     | 审核时间         | 1592982477000 |

## 样本

```json
{
    "asn": "ASN2006001234",
    "customerCode": "KN",
    "manifest": [
        {}, {}, {}
    ],
    "declarations": [
        {}, {}, {}
    ],
    "mappings": [
        {}, {}, {}
    ],
    "submittedOrgId": "562",
    "submittedBy": "某某工厂",
    "submittedAt": 1592972477000,
    "approver": "陈大文",
    "approvedAt": 1592982477000
}
```
