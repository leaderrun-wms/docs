# 按入库单查询关务库存数据

接口定义方：慧通关

## 功能描述

* 按入库单查询当前库存数据

## 接口详情

路径：

```
    https://FD_HOST/inbound-dec
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
    "inboundBatchNos": [
        "入库单号1", // 批量查询多个入库单号
        "入库单号2",
        "入库单号3"
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": [
        {
            "inboundBatchNo": "入库单号1",
            "items": [ // 入库单所有请单行
                {
                    "id": "line-id-001",
                    "qty": "10.0", //PCS数
                    "decItems": [ // 表示商品 line-id-001 关联了 2 行关务行
                        {
                            "lineNo": 1, // 原报关单序号
                            "hsCode": "9102190000", // 商品编码
                            "ciCode": "9102190000999", // 商检编码
                            "name": "三条明细，单箱（35CBM）", // 商品名称
                            "spec": "3|0|锌合金表壳|电子驱动|指针|ALDO牌|无型号", // 商品要素
                            "salesUnit": "008", // 成交单位（传中文）
                            "salesUnitQty": 10, // 成交数量
                            "unit1": "008", // 法1单位（传中文）
                            "unit1Qty": 10, // 法1数量
                            "unit2": null, // 法2单位（传中文）
                            "unit2Qty": null, // 法2数量
                            "unitPrice": 20, // 单价
                            "totalPrice": 200, // 总价
                            "netWeight": 1.3333, // 净重
                            "currency": "USD", // 币种
                            "control": null, // 监管条件（传中文）
                            "levy": "1", //征免性质（传中文）
                            "destinationCountry": "CHE", // 最终目的国（传中文）
                            "originCountry": "CHN", // 原厂国（传中文）
                            "origin": "深圳特区", // 境内货源地（传中文）
                            "sourceCode": "440306", // 产地代码
                            "goodsNumber": "PLA20040001-1-1", // 料件号
                            "cartonSpec": 10, // 箱数
                            "grossWeight": 10.3332, // 毛重	
                            "properties": [
                                {
                                    "key": "grossWeight", // 毛重
                                    "value": 1.8333
                                },
                                {
                                    "key": "inboundDecId",
                                    "value": "2d741e52431f4ae0ac6a6c13635614b6" // 原报关单ID
                                },
                                {
                                    "key": "inboundDecItemNo",
                                    "value": 1 // 原报关单序号
                                },
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD201908081603" // 核注清单号
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 25537145 // 核注清单序号
                                }
                            ]
                        },
                        {
                            "lineNo": 2, // 原报关单序号
                            "hsCode": "9102190000", // 商品编码
                            "ciCode": "9102190000999", // 商检编码
                            "name": "三条明细，单箱（35CBM）", // 商品名称
                            "spec": "3|0|锌合金表壳|电子驱动|指针|ALDO牌|无型号", // 商品要素
                            "salesUnit": "008", // 成交单位
                            "salesUnitQty": 10, // 成交数量
                            "unit1": "008", // 法1单位
                            "unit1Qty": 10, // 法1数量
                            "unit2": null, // 法2单位
                            "unit2Qty": null, // 法2数量
                            "unitPrice": 20, // 单价
                            "totalPrice": 200, // 总价
                            "netWeight": 1.3333, // 净重
                            "currency": "USD", // 币种
                            "control": null, // 监管条件
                            "levy": "1",
                            "destinationCountry": "CHE", // 最终目的国
                            "originCountry": "CHN", // 原厂国
                            "origin": null, // 境内货源地
                            "sourceCode": "440306", // 产地代码
                            "goodsNumber": null, // 料件号
                            "cartonSpec": 10, // 箱数
                            "grossWeight": 10.3332, // 	
                            "properties": [
                                {
                                    "key": "grossWeight", // 毛重
                                    "value": 1.8333
                                },
                                {
                                    "key": "inboundDecId",
                                    "value": "2d741e52431f4ae0ac6a6c13635614b6"
                                },
                                {
                                    "key": "inboundDecItemNo",
                                    "value": 1
                                },
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD201908081603"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 25537146
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "inboundBatchNo": "入库单号2",
            "items": [ // 入库单所有请单行
            ]
        }
        {
            "inboundBatchNo": "入库单号3",
            "items": [ // 入库单所有请单行
            ]
        }
    ]
}
```

说明：

* Authorization头信息：
    * 立航负责在慧通关平台中生成此秘钥
    * 此秘钥是代表立航的身份
    * WMS是以立航的身份调用此接口
    * 在慧通关的所有接口，都需要这个头信息作身份验证
* 入库单查询（输入）：
* 返回清单ID，数量
* 和每一个清单ID、数量的相对关务行数据
* 只要清单行含对应的关务行，就返回对应的关务行，而**并不做任何归并、组合、拆分关系的比例分摊计算**。例如：清单行【A】和【B】对应一行关务行【X】，则【A】会有【X】的全部数量，【B】也同时有【X】的全部数量。
* 料件号：PLA20040001-1-1（单号-报关单行号-清单行号）
