订单类型定义：

一、入库订单类型：

保税仓：

1. 出口入区（编码：EXPORT_IN）
2. 进境入区（编号：ENTRY_IN）
3. 区内转入（编号：TIA_IN）
4. 区外转入（编号：TOA_IN）

监管仓：

5. 入库订单（编号：BASEORDER_IN）

其他：

6. 退场入库（编号：BACKLOCATION_IN）
7. 普通入库（编号：ORDINARYORDER_IN）

其中1-5的订单类型的入库订单需在FD、OWB系系统进行交互。

二、出库订单类型：

保税仓：

1. 进口出区（编号：ENTRY_OUT）
2. 出境出区（编号：EXPORT_OUT）
3. 区内转出（编号：TIA_OUT）
4. 区外转出（编号：TOA_OUT）

监管仓：

5. 出库订单（编号：BASEORDER_OUT）
6. 仓转仓出库（编号：WTOW_OUT）

其他：

7. 退仓出库（编号：WITHDRAW_OUT）
8. 普通出库（编号：ORDINARYORDER_OUT）

其中1-6的订单类型的出库订单需在FD、OWB系系统进行交互。
