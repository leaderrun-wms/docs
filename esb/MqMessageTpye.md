# 消息格式注册表

| 消息类型          | 系统ID | 版本 | 产生说明                     | 内文格式 和 样本                         |
|-------------------|--------|------|------------------------------|------------------------------------------|
| so.received       | ASN    | 1    | 客户上传了SO档案             | [格式和样本](asn.approved/readme.md)      |
| asn.approved      | ASN    | 1    | ASN已审核通过                | [格式和样本](asn.approved/readme.md)     |
| asn.arrived       | FD     | 1    | ASN已到达仓库(交单)          | [格式和样本](asn.arrived/readme.md)      |
| customs.declared  | FD     | 1    | 海关已申报                   | [格式和样本](customs.declared/readme.md) |
| customs.released  | FD     | 1    | 海关已放行                   | [格式和样本](customs.released/readme.md) |
| inbound.started   | WMS    | 1    | 开始卸货                     |                                          |
| inbound.finished  | WMS    | 1    | 入仓卸货                     | [格式和样本](inbound.finished.md)  |
| outbound.received | WMS    | 1    | 收到出库指令                 |                                          |
| outbound.started  | WMS    | 1    | 出库指令开始处理（开始装柜） |                                          |
| outbound.sealed   | WMS    | 1    | 出仓装柜                    | [格式和样本](outbound.sealed.md)  |
| customs.declared  | FD     | 1    | 海关已申报（和入库一致）     | [格式和样本](customs.declared/readme.md) |
| customs.released  | FD     | 1    | 海关已放行（和入库一致）     | [格式和样本](customs.released/readme.md) |
