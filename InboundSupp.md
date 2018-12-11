# ASN 信息补录回传

接口定义方：慧通关

## 功能描述

* 理论上此信息应该由ASN系统接收
* 接收ASN后期附加信息
  * 车型
  * 车牌
  * CBM
  * 司机姓名
  * 司机电话
  * 预计到仓时间

## 接口详情

### 货物出库请求

路径：

```
    https://ASN_HOST/api/asn/<ASNID>/properties
```

* 具体ASN_HOST的配置在首页的环境栏目中描述
* 测试环境使用http协议，生产环境使用https加密协议
* ASNID：ASN单号在URL路径名称中

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：PUT

内容：

```json
{
    "properties": [
        {
            "key": "TRUCK_TYPE",
            "value": "10吨车"
        },
        {
            "key": "LICENSE_PLATE_NO",
            "value": "粤B12345"
        },
        {
            "key": "DRIVER_NAME",
            "value": "王小虎"
        }
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
}
```

说明：

* Authorization头信息：
    * 立航负责在慧通关平台中生成此秘钥
    * 此秘钥是代表立航的身份
    * WMS是以立航的身份调用此接口
    * 在慧通关的所有接口，都需要这个头信息作身份验证
* properties（输入）：
    * 每一个Property为一个键值对
    * 调用者可以任意保存他所需要的信息，以Key为识别
    * 重复调用时，已经存在的Key会被新的值覆盖，不存在的会被创建
    * 要删除旧有的Property，Value值设null（或不设置）

建议属性Key名称：

| Key              | 说明         | 备注                              |
| ---------------- | ------------ | --------------------------------- |
| LICENSE_PLATE_NO | 车牌         | Key必须一致，才会自动填在报关单中 |
| TRUCK_TYPE       | 车型         |                                   |
| GOODS_VOLUME     | CBM          |                                   |
| DRIVER_NAME      | 司机姓名     |                                   |
| DRIVER_MOBILE    | 司机电话     |                                   |
| ETA              | 预计到仓时间 |                                   |