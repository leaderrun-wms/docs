# 出库确认（货物内容已经确认不会变动：锁封）

接口定义方：慧通关

## 功能描述

* 货已离开仓库

路径：

```
    https://FD_HOST/outbound/confirmation
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
    "processId": "启动出仓流程返回的ID",
    "properties": [  // 确认时的额外属性，可为空
        {"key": "KNJobNo", "value": "somevalue"}
    ]
}
```

返回内容：

```json
{
    "success": true,
    "message": "若success为false时候的错误信息",
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
* processId（输入）：
    * 启动出仓流程，返回的流程 ID
  
