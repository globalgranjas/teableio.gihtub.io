---
description: 介绍如何在指定的表中删除多条记录
---

# 删除记录

#### 路径

DELETE /table/{tableId}/record

#### 请求

**路径参数**

* tableId (string): 表的唯一标识符。

**查询参数**

* **recordIds（必填）**
  * 描述：要删除的记录 ID 数组
  * 类型：数组
  * 示例：`["rec123456", "rec789012"]`
  * 说明：每个元素都是一个字符串，代表要删除的记录的 ID。

#### 响应

**成功响应**

* 状态码: 200 OK
* 响应体: 无内容

#### 错误响应

* 状态码: 400 Bad Request: 请求参数格式错误或缺少必需参数。
* 状态码: 404 Not Found: 指定的表 tableId 不存在或某些记录 ID 不存在。

#### 示例代码

{% tabs %}
{% tab title="CURL" %}
```bash
curl -X DELETE 'https://app.teable.cn/table/__tableId__/record?recordIds[]=rec123456&recordIds[]=rec789012' \
  -H 'Authorization: Bearer __token__'
```
{% endtab %}

{% tab title="JS SDK" %}
```typescript
import { configApi, deleteRecords } from '@teable/openapi';

configApi({
  endpoint: 'https://app.teable.cn',
  token: '__token__',
});

await deleteRecords('__tableId__', ['rec123456', 'rec789012']);

```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
const response = await fetch('https://app.teable.cn/table/__tableId__/record?recordIds[]=rec123456&recordIds[]=rec789012', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer __token__'
  }
});

console.log(response.status); // 200 if successful
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

response = requests.delete(
    'https://app.teable.cn/table/__tableId__/record',
    headers={
        'Authorization': 'Bearer __token__'
    },
    params={
        'recordIds': ['rec123456', 'rec789012']
    }
)

print(response.status_code) # 200 if successful
```
{% endtab %}
{% endtabs %}

