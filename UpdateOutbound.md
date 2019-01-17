# 出库关务接口

接口定义方：慧通关

## 功能描述

* 是否可修改（申报后不能修改)
* 提供货物和关务数据是否可出仓检查

## 接口详情

### 修改货物出库请求

路径：

```
    https://FD_HOST/outbound/{processId}
```

* 具体FD_HOST的配置在首页的环境栏目中描述
* 测试环境使用http协议，生产环境使用https加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：PUT

内容：

```json
{
    "wmsOrderId": "仓库系统出库订单唯一标识",
    "wmsOrderDate": unixEpochInMillisecond,
    "properties": [
        {
            "key": "DESTINATION_COUNTRY",
            "value": "CNY"  // 目的国 ISO三位编码
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
            "key": "CONTAINER_NO",
            "value": "XXX"  // 柜号
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
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息"
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
* processId（输入）：
    * 创建时候返回的 出库流程ID
  
