# 出库关务接口

接口定义方：慧通关

## 功能描述

* 提供货物和关务数据是否可出仓检查
* 进行具体出库，启动关务单证流程

## 出库流程  
* 测试环境海运出库流程(processConfigId 96c7e228-bbd4-4cf2-9ba3-30430ee6957d)

## 接口详情

### 创建货物出库请求

路径：

```
    https://FD_HOST/outbound
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
    "wmsOrderDate": unixEpochInMillisecond,
    "warehouseCode": "PLS",
    "omsProcessConfigId": "流程ID",
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
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
    "result": {
        "processId": "OMS的流程ID"
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
* omsProcessConfigId（输入）：
    * 由于海运、陆运和空运在单证层面在流程上会稍有不同，这里使用的值也会不同
    * 具体值的设置，根据出仓需要来配置
    * 用户在OMS管理具体流程，processConfigId在OMS生成，并建议复制此值到WMS的出仓配置中
* processId（输出）：
    * 此接口若成功，则返回流程编号，用来标识这一票订单在OMS内的唯一标识
    
  
