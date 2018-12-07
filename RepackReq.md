# 改包装关务信息接口

接口定义方：慧通关

## 功能描述

* 货物包装改动请求
* 输入：原始包装个数集合，目标包装个数集合
    * 如在原本货物清单行做改动，目标行则返回相同ID
    * 如原本货物行全部变成新一行（或多行）货物，则行ID应该是新产生的
* 输出：
    * 成功 - 更改包装申请已提交，需要单证部门进一步核实和匹配
    * 失败 - 返回失败原因说明

## 接口详情

### 更改包装请求

路径：

```
    https://FD_HOST/repack
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
    "omsProcessConfigId": "流程ID",
    "fromItems": [
        {
            "id": "清单行唯一ID",
            "qty": "旧包装数量"
        } // 可以多行货物
    ],
    "toItems": [
        {
            "id": "清单行唯一ID",
            "qty": "新包装数量",
            "unit": "新包装单位",
            "nw": netWeight,
            "nwUnit": "净重单位",
            "gw": grossWeight,
            "gwUnit": "毛重单位"
        } // 可以多行货物
    ],
    "callbackUrl": "http://somehost.com/somepath"
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
* fromItems、toItems 中的id（输入）：
    * 此ID在入仓时作为货物行的系统交互的唯一标识
    * 在改变包装后新产生的货物行，需要建一个新的ID
    * 若新旧行ID相等并只有一条数据，表示不产生新行，只改动单位和数量，旧行的数量需要是全部库存数量
* items中的qty（输入）：
    * 出库数量，按当前货物行的单位为准
* omsProcessConfigId（输入）：
    * 触发具体变更流程
    * 用户在OMS管理具体变更包装流程，processConfigId在OMS生成，并建议复制此值到WMS的出仓配置中
* nw/gw/nwUnit/gwUnit:
    * 旧行的总毛重和总净重，需要等于新行的总毛重和总净重
    * 若新旧行ID相等并只有一条数据，重量字段可以缺省不录，复用系统库存值
* callbackUrl:
    * 在完成整个变更流程后，系统会给此接口回调
* processId（输出）：
    * 此接口若成功，则返回流程编号，用来标识这一票订单在OMS内的唯一标识


流程完成后，系统会对CallbackUrl进行回调，详情请看：[改包装关务信息反馈接口](RepackResp.md)