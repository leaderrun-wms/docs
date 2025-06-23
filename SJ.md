# 提前发送商检数据接口

接口定义方：慧通关

## 功能描述

* 提供货物转成商检数据到报关系统
* 只转发到报关系统，并不会启动出库流程
* 用于特殊商检准备

## 接口详情

### 发送特殊商检数据请求

路径：

```
    https://FD_HOST/sj
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
    "wmsOrderId": "仓库系统出库订单唯一标识",
    "wmsOrderDate": unixEpochInMillisecond,//出仓时间
    "warehouseCode": "PLS", //站点代码
    "orderType": "订单类型", // 看 orderType.md 
    "properties": [
        {
            "key": "DESTINATION_COUNTRY",
            "value": "CHN"  // 目的国 ISO三位编码
        },
        {
            "key": "DECLARATION_PORT", // 出境关别 编码
            "value": "5316"
        },
        {
            "key": "LEAVE_PORT", // 离境口岸 编码
            "value": "470601"
        },
        {
            "key": "SHIPMENT_METHOD", // 运输方式 编码
            "value": "2"
        },
        {
            "key": "LOCAL_PORT", // 指运港 编码
            "value": "CHN000"
        },
        {
            "key": "VOYAGE_NO",
            "value": "XXX"  // 船名航次
        },
	{
	     "key": "customerName", // 大客
	     "value": "德迅中国"
	},
	{
	     "key": "childrenCustomerName", // 子客
	     "value": "KN-SEX"
	},	
        {
            "key": "CONTAINERS",//柜信息
            "value":
            [{
                "seq": "1",
                "type": "HQ|GP",
                "spec": "20|40|45|53",
                "number": "柜号1"
            },
            {
                "seq": "2",
                "type": "HQ|GP",
                "spec": "20|40|45|53",
                "number": "柜号2"
            }]
         }
    ],
    "items": [  // 支持多个货物行一次出库
        {
            "id": "清单行唯一ID",
            "qty": "出库数量"
        },
        {
            "id": "清单行唯一ID",
            "qty": "出库数量"
        },
        {
            "id": "清单行唯一ID",
            "qty": "出库数量"
        }
    ],
    "packages": {
        "unit": "CTN",  // 出库外包装单位（操作单位） CTN/PLT/或其他约定的单位
	"qty": "总数量", // 如果清单行无法知道数量，填这个总箱数，如果清单行数量对应关系是明确的，这个地方填空（null 或 0）
        "details": [
            {
                "id": "清单行唯一ID",  // 每一个清单行的操作数量
                "qty": "操作数量"
            },
            {
                "id": "清单行唯一ID",
                "qty": "操作数量"
            },
            {
                "id": "清单行唯一ID",
                "qty": "操作数量"
            }
        ]
    }
}
```

返回内容：

```json
{
	"success": true,
	"message": "若success为false时候的错误信息",
	"messageDetails": {
		"global": ["全局错误信息1", "全局错误信息2"],
		"items": [{
			"id": "清单行唯一ID",
			"message": "该清单行错误信息"
		}]
	},
    "result": {
		"processId": "OMS的流程ID",
		"decls": [{
				"urmNo": "PR0001-1",
				"lineTotal": 10,
				"attchmentUrl": "http://pdf.xxx.com/PR0001-1-2.pdf",
				"decId": "2ec076f1-3029-4aab-a8a5-d4c0aacf135c", // 报关单id
				"details": [{
					"lineNo": 1, // 序号
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
                    			"cartonSpec"：10, // 箱数
					"grossWeight" : 10.3332,
                   			 "sj": "是", //是否整出
					 "asnNo": "ASN250600003", // ASN单号
                    			 "inboundDecItemNo":1,
		    			 "inboundCustomsLedgerId":"QDTIIK201908081603",
		   			 "inboundCustomsLedgerNo":25537145,
				  "decIdLineIdMappings": [{
					"mfLineId": "414e5d8f-813b-4bae-a4b0-ed7673fc8657", // 清单ID
					"decId": "2ec076f1-3029-4aab-a8a5-d4c0aacf135c", // 报关单Id
					"decLineNo": 1 // 报关单序号
				}]
			
		}]
	}
}
```

说明：

* Authorization头信息：
    * 立航负责在慧通关平台中生成此秘钥
    * 此秘钥是代表立航的身份
    * WMS是以立航的身份调用此接口
    * 在慧通关的所有接口，都需要这个头信息作身份验证
* items中的id（输入）：
    * 此ID在入仓时作为货物行的系统交互的唯一标识
    * 和在改变包装后新产生的货物行的ID
* items中的qty（输入）：
    * 出库数量，按当前货物行的单位为准
* wmsOrderId 为商检数据的唯一识别
    * 若已经传输了一个wmsOrderId，相同wmsOrderId的请求会被拒绝，除非报关系统做删除商检数据处理。
    * 出仓接口会按wmsOrderId关联商检数据

