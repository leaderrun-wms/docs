# 公路舱单接口

接口定义方：慧通关

- 具体 FD_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

## 获取公路仓单

路径：

```
    https://FD_HOST/outbound/glcd/<filename>
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：applicatin/json

```json
{
	
    "wmsOrderId": "仓库系统出库订单唯一标识",
    "warehouseCode": "PLS",
    "properties": [
        {
            "key": "CONTAINERS", // 柜信息
            "value": 
            [{
                "seq": "1",
                "type": "HQ|GP",
                "spec": "20|40|45|53",
                "number": "柜号1"
            }]
         },
        {

            "key": "IMPORT_EXPORT_PORT", // 进出境口岸代码
            "value": "5301"
        }
    ],
    "items": [  // 清单信息
        {
            "id": "清单id",
            "qty": "10"
        }
    ]

}
```

返回内容： 

	byte[]