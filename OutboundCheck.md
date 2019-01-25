# 出库检查接口

接口定义方：慧通关

## 功能描述

* 提供货物和关务数据是否可出仓检查
* 仅仅提供检查，不会启动任何流程

## 接口详情

### 出库检查请求

路径：

```
    https://FD_HOST/outbound/check
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
    "success": false,
    "message": "若success为false时候的错误信息（标题）",
    "messageDetails": {
        "global": ["全局错误信息1", "全局错误信息2"],
        "items": [ 
            { "id": "清单行唯一ID", "message": "该清单行错误信息" }
        ]
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
    
  
