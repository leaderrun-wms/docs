# 提前发送商检数据接口

接口定义方：慧通关

## 功能描述

* 提供货物转成商检数据到报关系统
* 只转发到报关系统，并不会启动出库流程
* 用于保税仓体现商检准备

## 接口详情

### 提前发送商检数据请求

路径：

```
    https://FD_HOST/ci
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
            "value": "value": 
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

