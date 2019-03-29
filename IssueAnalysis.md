
# 货物异常分析和数据整理

| 预报                   | 实际                  | 描述                  | 异常manifest的content数据            | 查询WMS结果                         |
| ---------------------- | --------------------- | --------------------- | ------------------------------------ | ----------------------------------- |
| Item1 x 10             | Item1 x 9             | 少货                  | ["Item1"]                            | Item1=9                             |
| Item1 x 10             | Item1 x 11            | 多货                  | ["Item1"]                            | Item1=11                            |
| Item1 x 10             | Item1 x 0, Item2 x 10 | 1. 少货 2. 没预报收货 | ["Item1", "Item2"]                   | Item1=0, Item2=10                   |
| Item1 x 10             | Item1 x 5, Item2 x 5  | 1. 少货 2. 没预报收货 | ["Item1", "Item2"]                   | Item1=5, Item2=5                    |
| Item1 x 10, Item2 x 10 | Item3 x 20            | 1. 少货 2. 没预报收货 | ["Item1", "Item2", "Item3"]          | Item1=0, Item2=0, Item3=20          |
| Item1 x 10, Item2 x 10 | Item3 x 15, Item4 x 5 | 1. 少货 2. 没预报收货 | ["Item1", "Item2", "Item3", "Item4"] | Item1=0, Item2=0, Item3=15, Item4=5 |
