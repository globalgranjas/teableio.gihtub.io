# 错误码

> Teable Web API 遵循 HTTP 状态代码语义。

- 2xx 

  代表成功

- 4xx

  用户错误

- 5xx

  服务端错误

错误信息将返回一个 JSON 编码的正文，其中包含错误和信息字段。下面是一个错误信息主体：

```json
{
  "message": "not allowed to operate space|read on spcxxxxxx",
  "status": 403,
  "code": "restricted_resource"
}
```



## 成功状态码

| HTTP 状态码 | 描述              |
| :---------- | :---------------- |
| 200         | 请求已经成功完成. |



## 错误码

下面是一些错误码列举

### 400 Bad Request

请求正文无法解析为`JSON`，包括传入`Body`参数不符合规范要求。

### 401 Unauthorized

未授权访问接口。

### 403 Forbidden

使用无权访问受保护资源的 API 凭据访问该资源。

### 404 Not Found

未找到路由或者资源。当访问不存在的资源路径，或者访问的请求方法不匹配。将返回此错误。

### 500 Internal Server Error

服务器遇到意外的情况

### 503 Service Unavailable

服务暂时不可用，可能处理超时，或者数据库连接失效。

