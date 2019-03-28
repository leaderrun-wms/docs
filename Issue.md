# 异常中心

接口定义方：慧通关

- 具体 ISSUE_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

## 创建异常

- 创建需要跨部门协调的问题跟踪项（Issue）
- 建立关联单证或有问题货物信息

路径：

```
    https://ISSUE_HOST/api/issue
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：

```json
{
  "origin": "发起异常的系统名字",
  "title": "异常标题",
  "description": "异常描述",
  "tag": ["异常类型标签1", "异常类型标签2"],
  "relations": [
    {
      "type": "manifest",
      "content": ["ItemID1", "ItemID2", "ItemID3"]
    },
    {
      "type": "declaration",
      "content": ["报关单号1", "报关单号2"]
    }
  ]
}
```

返回内容：

```json
{
  "success": true,
  "message": "若success为false时候的错误信息",
  "result": "创建了的ISSUE的唯一ID"
}
```

## 登记需要监听的回调地址

- 按 ISSUE ID 登记

路径：

```
    https://ISSUE_HOST/api/issue/<ISSUEID>/notification
```

- 具体 ISSUE_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：POST

请求内容：

```json
{
  "url": "http://myhost.com/i/need/this/callback"
}
```

返回内容：

```json
{
  "success": true,
  "message": "若success为false时候的错误信息",
  "result": {
    "id": "登记此回调的唯一ID，用于取消回调用"
  }
}
```

而注册了的回调地址，应不同的状态转变收到不同的通知：

- 变更关联单证或货物（relations）
- 变更状态（OPEN -> CLOSED）
- issue 中增加会话、或改变了某个会话

回调内容（POST请求）：

```json
{
  "id": "ISSUEID",
  "type": "变更类型", // relations, status, conversation
  "details": {
    // 根据不同类型返回不同结构
  }
}
```

- 当 type=relations：details 为空，可于查询接口查看更新后的内容
- 当 type=status： details 为 `{ "from": "from_status", "to": "to_status" }`
- 当 type=conversation: details 为空（目前还没定义会话的内容接口）

说明：
* 当回调请求失败（网络异常，服务器异常，返回值非200），则会进行每1分钟重试
* 同一个回调请求，在重试10分钟后，如果仍然失败，则此回调地址将会无法接受往后的回调，使用方需要重新注册登记回调地址

## 取消监听回调地址

- 按 Notification ID 取消

路径：

```
    https://ISSUE_HOST/api/issue/<ISSUEID>/notification/<NOTIFICATIONID>
```

- 具体 ISSUE_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：DELETE

返回内容：

```json
{
  "success": true,
  "message": "若success为false时候的错误信息"
}
```

## 查询异常和关联数据

- 按 ISSUE ID 查询异常内容

路径：

```
    https://ISSUE_HOST/api/issue/<ISSUEID>
```

- 具体 ISSUE_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：GET

返回结果：

```json
{
  "origin": "发起异常的系统名字",
  "title": "异常标题",
  "description": "异常描述",
  "tag": ["异常类型标签1", "异常类型标签2"],
  "relations": [
    {
      "type": "manifest",
      "content": ["ItemID1", "ItemID2", "ItemID3"]
    },
    {
      "type": "declaration",
      "content": ["报关单号1", "报关单号2"]
    }
  ]
}
```

## 查询异常关联数据

- 按 ISSUE ID 查询异常关联数据内容

路径：

```
    https://ISSUE_HOST/api/issue/<ISSUEID>/relations/<TYPE>
```

- 具体 ISSUE_HOST 的配置在首页的环境栏目中描述
- 测试环境使用 http 协议，生产环境使用 https 加密协议

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：GET

返回结果：

```json
{
  "type": "manifest",
  "content": ["ItemID1", "ItemID2", "ItemID3"]
}
```

## 变更异常相关的关联关系

- 用于增加或减少相关联关系的文件或货物

路径：

```
    https://ISSUE_HOST/api/issue/<ISSUEID>/relations/<TYPE>
```

请求头信息：

```
Authorization: Access_Key XXXXXXXX
```

请求方法：PUT

请求内容：

```json
{
  "type": "manifest",
  "content": ["ItemID1", "ItemID2", "ItemID3", "ItemID4"]
}
```
