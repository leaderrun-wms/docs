# 系统一览

| 名称           | 编码 | 系统开发方   |
| -------------- | ---- | ------------ |
| 前台服务系统   | FD   | 慧通关       |
| ASN系统        | ASN  | 慧通关       |
| 关务系统       | CMS  | 慧通关       |
| 海关系统数据库 | HGXT | 唯智，慧通关 |
| 电子发票系统   | DZFP | ？           |
| ？             | OWB  | ？           |

# 整体系统架构

![架构图](diagrams/Architecture.png)
[编辑](https://www.draw.io/?title=Architecture.png&url=https%3A%2F%2Fgithub.com%2Fleaderrun-wms%2Fdocs%2Fraw%2Fmaster%2Fdiagrams%2FArchitecture.png%3Ft%3D0)


# 对接接口一览

| 序号 | 接口名称                                      | 发送方 | 接收方 | 服务 | 集成 | 描述                                                                                                                                      |
| ---- | --------------------------------------------- | ------ | ------ | ---- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | [入库订单接口](Inbound.md)                    | FD     | OWB    | ok   | OK   | 异步返回处理结果；1.创建会发；2.放行发 OWB 会自动审核往仓库下发；3.关务信息保存可供货代查看                                               |
| 2    | [创建出库关务接口](Outbound.md)               | OWB    | FD     | OK   |      | 主动推送查询给CMS，CMS实时反馈结果；订单审核发送时，如果反馈结果不成功，WMS可以往下执行；发运之前再次请求，如果反馈结果为不成功，不能发运 |
| 3    | [现金收费](Receivable.md)                     | OWB    | FD     | ok   |      | 创建订单的时候进行计费，提供接口给 CMS 查询，未收的费用项目及金额                                                                         |
| 4    | [现金收费反馈](Payment.md)                    | FD     | OWB    | ok   |      | 实际收费情况反馈，根据费用项目收费时的交易号判断是更新还是新增                                                                            |
| 5    | [库位货品信息](InternalOp.md)                 | OWB    | HGXT   |      |      | 收货，上架，移位，下架                                                                                                                    |
| 6    | [改包装关务信息接口](RepackReq.md)            | OWB    | FD     | RFI  |      | 货品包装形态改变，需要重新匹配关务信息                                                                                                    |
| 7    | [改包装关务信息反馈接口](RepackResp.md)       | FD     | OWB    | RFI  |      |                                                                                                                                           |
| 8    | [ASN 信息补录回传](InboundSupp.md)            | OWB    | ASN    | OK   |      | 小程序 asn 信息补录(车型，车牌，CBM，司机姓名，司机电话，预计到仓时间)，记录信息传给 CMS；车辆到仓再传一次                                |
| 9    | [报关单反馈](CustomsFeedbackPDF.md)           | FD     | OWB    | ok   |      | 根据单号查看报关单（CMS 提供产生的报关单链接）                                                                                            |
| 10   | [单证状态接口](CustomsFeedbackStatus.md)      | FD     | OWB    | ok   |      | 报关等完成后由 CMS 传递给 OWB                                                                                                             |
| 11   | [电子发票接口](ElectronicInvoice.md)          |        |        |      |      |                                                                                                                                           |
| 12   | [仓库信息接口](Warehouse.md)                  | FD     | OWB    | ok   |      |                                                                                                                                           |
| 13   | [客户信息接口](Customer.md)                   | FD     | OWB    | ok   |      |                                                                                                                                           |
| 14   | [订单放行接口](OrderRelease.md)          | FD     | OWB    | ok   |      |                                                                                                                                           |
| 15   | [出库订单确认申报接口](ConfirmDeclaration.md) | OWB    | FD     |      |      | 运抵确认出库报关单可申报                                                                                                                  |
| 16   | [修改出库关务接口](UpdateOutbound.md)         | OWB    | FD     |      |      | 主动推送查询给CMS，CMS实时反馈结果；订单审核发送时，如果反馈结果不成功，WMS可以往下执行；发运之前再次请求，如果反馈结果为不成功，不能发运 |
| 17   | [出库确认（货物内容已经确认不会变动：锁封）](OutboundConfirmation.md)         | OWB    | FD     |      |      | 调用此接口表示货物内容不会再改变  |
| 18   | [出仓检查验证](OutboundCheck.md)              | OWB    | FD     | OK   |      |                                                  
| 19   | [车型查询接口](Vehicletype.md)                   | FD    | OWB    | OK   |      |                                                   
| 20   | [异常中心接口](Issue.md)                   | OWB/FD    | ISSUE    |     |      | 异常订单生效，主动推送给 CMS ([有关异常数据分析](IssueAnalysis.md))                                             
| 21   | [货物清单查询接口](ItenListInfo.md)           | OWB    | FD    |     |      | 提供接口给 CMS 查询                                       
| 22   | [货物清单反馈接口](ItemListInfoResp.md)           | FD    | OWB    |     |      | 提供接口给 CMS 查询                                                                                    
| 22   | [OWB接收异常通知接口](IssueResp.md)           | FD    | OWB    |     |      | FD在异常发生后，创建Issue后通知OWB相关异常ID                                                                                     
| 24   | [FD接收异常通知](FDIssueNotification.md)   | OWB    | FD    |     |      | OWB在异常发生后，创建Issue后通知FD相关异常ID |
| 25   | [交仓预约接口](AppointDelivery.md) | OWB | ASN |  | | 监管仓库，创建交仓预约接口|
| 26   | [预约时间查询接口](Reservation.md) | FD | OWB |  | | 保税仓库，预约时间查询接口|
| 27   | [预约时间扣减接口](DeductReservation.md) | FD | OWB |  | | 保税仓库/监管仓库，工单校验通过通知OWB扣减预约时间的CBM|
| 28   | [公路舱单接口](Glcd.md) | OWB |  FD |  | | 下载公路舱单文件|
| 29   | [按入库单查询关务库存数据](InboundDecQuery.md) | OWB |  FD |  | | 提供查询关务库存数据的能力 |
| 30   | [货物延期申请](PeriodExtension.md) | OWB |  FD |  | | 货物延期申请 |
| 31   | [货物延期反馈接口](delayedOrderFeedback.md) | FD |  OWB |  | | 货物延期处理结果反馈 |
| 32   | [MQ入仓卸货 MQ消息接口](inboundfinished.md) | WMS |  FD | OK | | 发送客户EDI处理 |
| 33   | [MQ出仓装卸 MQ消息接口](outboundsealed.md) | WMS |  FD | OK | | 发送客户EDI处理 |
| 34   | [MQedi处理反馈接口](knediRetrun.md) | WMS |  FD | OK | | edi处理反馈接口 |
| 35   | [MQ消息格式注册表消息格式注册表](README.md) | WMS |  FD | OK | | 订单类型定义 |
| 36   | [订单类型定义](orderType.md) | WMS |  FD | OK | | 订单类型定义 |




# 环境

## 开发环境

* OWB: TODO
* FD: lhfdbe-test.yunbaoguan.cn:81
* ASN: lhomsbe-test.yunbaoguan.cn:81
* ISSUE: lhissuebe-test.yunbaoguan.cn
* 
## 生产环境
