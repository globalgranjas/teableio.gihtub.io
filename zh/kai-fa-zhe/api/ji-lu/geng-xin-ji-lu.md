---
description: 介绍如何在指定的表中更新一条记录
---

# 更新记录

### 路径

PATCH /table/{tableId}/record/{recordId}

### 请求

#### 路径参数

* tableId (string): 表的唯一标识符[（如何获取）](../huo-qu-id.md#tableid)。
* recordId (string): 要更新的记录的唯一标识符[ (如何获取）](../huo-qu-id.md#recordid)。

#### 请求体

* **record（必填）**
  * 描述：要更新的记录数据
  * 类型：对象
  *   示例：

      ```javascript
      {
        "fields": {
          "Name": "John Doe",
          "Age": 31,
          "Email": "john.doe@example.com"
        }
      }
      ```
  * 说明：`fields` 对象包含要更新的字段名和对应的新值。每一种字段值结构都不一样，详情请[查看记录字段值类型](ji-lu-zi-duan-zhi-lei-xing.md)

{% hint style="info" %}
要清空一个字段的值请显式的传递 `null,`如果字段名没有传递则不会进行任何更新
{% endhint %}

* **fieldKeyType（可选）**
  * 描述：指定字段键的类型
  * 类型：字符串
  * 可选值：
    * "name"：使用字段名作为键
    * "id"：使用字段 ID 作为键
  * 示例：`"name"` 或 `"id"`
  * 说明：如果不指定，默认使用字段名作为键。
  * 用法：
    *   当设置为 "name" 时：

        复制

        ```javascript
        {
          fields: {
            "Name": "John Doe",
            "Age": 30
          }
        }
        ```
    *   当设置为 "id" 时：

        复制

        ```javascript
        {
          fields: {
            "fldABCDEFGHIJKLMN": "John Doe",
            "fldOPQRSTUVWXYZ12": 30
          }
        }
        ```
* **typecast（可选）**
  * 描述：是否自动转换字段值类型，默认会严格校验，需要保证输入的值符合当前字段的数据类型，如果开启则会尝试自动进行转换。
  * 类型：布尔值
  * 可选值：true 或 false
  * 示例：`true`
  * 说明：如果设置为 true，系统会尝试将输入值转换为正确的字段值类型。
  * 用法示例：
    *   关联字段：可以直接使用主键文本进行关联

        复制

        ```javascript
        {
          "User table": "张三"
        }
        ```
    *   日期字段：可以使用非标准格式的日期字符串

        复制

        ```javascript
        {
          "Date": "2023-05-15"
        }
        ```
    *   用户字段：可以直接使用用户名

        复制

        ```javascript
        {
          "Assigned To": "John Doe"
        }
        ```

### 响应

#### 成功响应

* 状态码: 200 OK
* 响应体: 返回更新后的记录数据。

**示例响应体**

```javascript
{
    "id": "rec123456789ABCDE",
    "fields": {
        "Name": "John Doe",
        "Age": 31,
        "Email": "john.doe@example.com"
    }
}
```

#### 错误响应

* 状态码: 400 Bad Request: 请求体格式错误或缺少必需字段。
* 状态码: 404 Not Found: 指定的表 tableId 或记录 recordId 不存在。

#### 示例代码

{% tabs %}
{% tab title="CURL" %}
```typescript
curl -X PATCH 'https://app.teable.cn/table/__tableId__/record/__recordId__' \
  -H 'Authorization: Bearer __token__' \
  -H 'Content-Type: application/json' \
  -d '{
    "record": {
      "fields": {
        "Name": "John Doe",
        "Age": 31
      }
    }
  }'
```
{% endtab %}

{% tab title="JS SDK" %}
```typescript
import { configApi, updateRecord } from '@teable/openapi';

configApi({
  endpoint: 'https://app.teable.cn',
  token,
});

const response = await updateRecord('__tableId__', '__recordId__', {
  record: {
    fields: {
      Name: 'John Doe',
      Age: 31
    }
  }
});

console.log(response.data);
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
const response = await fetch('https://app.teable.cn/table/__tableId__/record/__recordId__', {
  method: 'PATCH',
  headers: {
    'Authorization': 'Bearer __token__',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    record: {
      fields: {
        Name: 'John Doe',
        Age: 31
      }
    }
  })
});

console.log(await response.json());
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

response = requests.patch(
    'https://app.teable.cn/table/__tableId__/record/__recordId__',
    headers={
        'Authorization': 'Bearer __token__',
        'Content-Type': 'application/json'
    },
    json={
        'record': {
            'fields': {
                'Name': 'John Doe',
                'Age': 31
            }
        }
    }
)

print(response.json())
```
{% endtab %}
{% endtabs %}
