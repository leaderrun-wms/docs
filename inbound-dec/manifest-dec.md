# 按清单行查询关务库存数据
(20230407更改，由查询库存数据变更为查询入库数据)
接口定义方：慧通关

## 功能描述

* 按入库单查询对应入库单入库数据，只有对应入库单金关序号全部返填后才能返回入库数据（ 即："key": "inboundCustomsLedgerNo"的值必需全部大于0）

## 接口详情

路径：

```
    https://FD_HOST/inbound-dec/origin/manifest-dec
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
        "bc8a512d4c7f417f84b43be04deada3b", // 批量查询多个清单行
        "e3c22ce5ab274174a6c9296b2ac02f86",
        "552ddc84-9eba-4872-92b7-14ee02368641"
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": null,
    "result": [
        {
            "inboundBatchNo": "IPLA230404441",//入库单号
            "items": [// 入库单所有请单行
                {
                    "id": "bc8a512d4c7f417f84b43be04deada3b",//清单ID
                    "qty": 20,//PCS数
                    "decItems": [
                        {
                            "lineNo": 1,// 原报关单序号
                            "hsCode": "8413709990",// 商品编码
                            "ciCode": "",// 商检编码
                            "name": "永磁同步泵",// 商品名称
                            "spec": "1|0|电动驱动|离心式|3600r/min|洗碗机用|FUDI牌|TP-66-25-2-14型",// 商品要素
                            "salesUnit": "001",// 成交单位（传代码）
                            "salesUnitQty": 20.0,// 成交数量
                            "unit1": "001",// 法1单位（传代码）
                            "unit1Qty": 20.0,// 法1数量
                            "unit2": "035",// 法2单位（传代码）
                            "unit2Qty": 9.2,// 法2数量
                            "unitPrice": 6.86,// 单价
                            "totalPrice": 137.2,// 总价
                            "netWeight": 9.2,// 净重
                            "currency": "USD",// 币种
                            "control": null,// 监管条件（传中文）
                            "levy": "1",//征免性质（传中文）
                            "destinationCountry": "ITA",// 最终目的国（传代码）
                            "originCountry": "142",// 原厂国（传代码）
                            "origin": null,// 境内货源地（传代码）深圳特区
                            "sourceCode": null,// 产地代码
                            "goodsNumber": "IPLA230404441-1-1",// 料件号
                            "cartonSpec": "1",// 箱数
                            "grossWeight": 9.9, // 毛重	
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265641"// 核注清单号
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067405// 核注清单序号
                                }
                            ]
                        }
                    ]
                },
                {
                    "id": "e3c22ce5ab274174a6c9296b2ac02f86",
                    "qty": 235,
                    "decItems": [
                        {
                            "lineNo": 2,
                            "hsCode": "8422901000",
                            "ciCode": "",
                            "name": "洗碗机安装组件",
                            "spec": "0|0|洗碗机用|无品牌|无型号|||刀叉篮组件、门开关组件、内门组件等",
                            "salesUnit": "035",
                            "salesUnitQty": 468.1,
                            "unit1": "035",
                            "unit1Qty": 468.1,
                            "unit2": null,
                            "unit2Qty": null,
                            "unitPrice": 7.0567,
                            "totalPrice": 3303.25,
                            "netWeight": 468.1,
                            "currency": "USD",
                            "control": null,
                            "levy": "1",
                            "destinationCountry": "ITA",
                            "originCountry": "142",
                            "origin": null,
                            "sourceCode": null,
                            "goodsNumber": "IPLA230404441-1-2",
                            "cartonSpec": "26",
                            "grossWeight": 526.4,
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265641"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067406
                                }
                            ]
                        }
                    ]
                },
                {
                    "id": "552ddc84-9eba-4872-92b7-14ee02368641",
                    "qty": 116,
                    "decItems": [
                        {
                            "lineNo": 2,
                            "hsCode": "8422901000",
                            "ciCode": "",
                            "name": "洗碗机安装组件",
                            "spec": "0|0|洗碗机用|无品牌|无型号|||刀叉篮组件、门开关组件、内门组件等",
                            "salesUnit": "035",
                            "salesUnitQty": 468.1,
                            "unit1": "035",
                            "unit1Qty": 468.1,
                            "unit2": null,
                            "unit2Qty": null,
                            "unitPrice": 7.0567,
                            "totalPrice": 3303.25,
                            "netWeight": 468.1,
                            "currency": "USD",
                            "control": null,
                            "levy": "1",
                            "destinationCountry": "ITA",
                            "originCountry": "142",
                            "origin": null,
                            "sourceCode": null,
                            "goodsNumber": "IPLA230404441-1-2",
                            "cartonSpec": "11",
                            "grossWeight": 526.4,
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265641"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067406
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "inboundBatchNo": "IPLA230404438",
            "items": [
                {
                    "id": "865979ff-c8cc-483e-a29c-d24298cef5d2",
                    "qty": 1728,
                    "decItems": [
                        {
                            "lineNo": 1,
                            "hsCode": "6302539090",
                            "ciCode": "",
                            "name": "食品罩",
                            "spec": "3|0|餐桌用|针织|75%涤纶+25%铁制|FOX RUN牌|18\"",
                            "salesUnit": "011",
                            "salesUnitQty": 1728.0,
                            "unit1": "011",
                            "unit1Qty": 1728.0,
                            "unit2": "035",
                            "unit2Qty": 138.0,
                            "unitPrice": 1.5069,
                            "totalPrice": 2604.0,
                            "netWeight": 138.0,
                            "currency": "USD",
                            "control": null,
                            "levy": "1",
                            "destinationCountry": "USA",
                            "originCountry": "142",
                            "origin": null,
                            "sourceCode": null,
                            "goodsNumber": "IPLA230404438-1-1",
                            "cartonSpec": "12",
                            "grossWeight": 144,
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265436"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067310
                                }
                            ]
                        }
                    ]
                },
                {
                    "id": "0c753564-0c3f-48a3-a766-398fa3fb7105",
                    "qty": 2016,
                    "decItems": [
                        {
                            "lineNo": 2,
                            "hsCode": "6302539090",
                            "ciCode": "",
                            "name": "食品罩",
                            "spec": "3|0|餐桌用|针织|75%涤纶+25%铁制|FOX RUN牌|13\"",
                            "salesUnit": "011",
                            "salesUnitQty": 2016.0,
                            "unit1": "011",
                            "unit1Qty": 2016.0,
                            "unit2": "035",
                            "unit2Qty": 161.0,
                            "unitPrice": 1.4544,
                            "totalPrice": 2932.0,
                            "netWeight": 161.0,
                            "currency": "USD",
                            "control": null,
                            "levy": "1",
                            "destinationCountry": "USA",
                            "originCountry": "142",
                            "origin": null,
                            "sourceCode": null,
                            "goodsNumber": "IPLA230404438-1-2",
                            "cartonSpec": "14",
                            "grossWeight": 196,
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265436"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067311
                                }
                            ]
                        }
                    ]
                },
                {
                    "id": "895b0543-15cb-4870-a332-230fa061546d",
                    "qty": 1152,
                    "decItems": [
                        {
                            "lineNo": 3,
                            "hsCode": "6302539090",
                            "ciCode": "",
                            "name": "食品罩",
                            "spec": "3|0|餐桌用|针织|75%涤纶+25%铁制|FOX RUN牌|30\"",
                            "salesUnit": "011",
                            "salesUnitQty": 1152.0,
                            "unit1": "011",
                            "unit1Qty": 1152.0,
                            "unit2": "035",
                            "unit2Qty": 168.0,
                            "unitPrice": 1.9717,
                            "totalPrice": 2271.36,
                            "netWeight": 168.0,
                            "currency": "USD",
                            "control": null,
                            "levy": "1",
                            "destinationCountry": "USA",
                            "originCountry": "142",
                            "origin": null,
                            "sourceCode": null,
                            "goodsNumber": "IPLA230404438-1-3",
                            "cartonSpec": "8",
                            "grossWeight": 200,
                            "properties": [
                                {
                                    "key": "inboundCustomsLedgerId",
                                    "value": "QD535223I000265436"
                                },
                                {
                                    "key": "inboundCustomsLedgerNo",
                                    "value": 1067312
                                }
                            ]
                        }
                    ]
                }
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
* 料件号：IPLA230404441-1-1（单号-报关单行号-清单行号）
* 只有对应入库单金关序号全部返填后才能返回入库数据（ 即："key": "inboundCustomsLedgerNo"的值必需全部大于0）
