---
description: 介绍如何在指定的表中创建多个记录
---

# 创建记录

### 路径

POST /table/{tableId}/record

### 请求

#### 路径参数

* tableId (string): 表的唯一标识符。

#### 请求体

非常感谢您的反馈。我会根据您的建议进行修改和补充。以下是更新后的列表：

* **records（必填）**
  * 描述：要创建的记录数组
  * 类型：数组
  *   示例：

      ```javascript
      [
        {
          fields: {
            "Name": "John Doe",
            "Age": 30,
            "Email": "john@example.com"
          }
        },
        {
          fields: {
            "Name": "Jane Smith",
            "Age": 28,
            "Email": "jane@example.com"
          }
        }
      ]
      ```
  * 说明：每个记录都是一个包含 `fields` 对象的项。`fields` 对象包含字段名和对应的值，每一种字段值结构都不一样，详情请[查看记录字段值类型](ji-lu-zi-duan-zhi-lei-xing.md)。
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

        ```javascript
        {
          fields: {
            "Name": "John Doe",
            "Age": 30
          }
        }
        ```
    *   当设置为 "id" 时：

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

        ```javascript
        {
          "User table": "张三"
        }
        ```
    *   日期字段：可以使用非标准格式的日期字符串

        ```javascript
        {
          "Date": "2023-05-15"
        }
        ```
    *   用户字段：可以直接使用用户名

        ```javascript
        {
          "Assigned To": "John Doe"
        }
        ```
* **order（可选）**
  * 描述：指定新记录的在指定视图所在的位置
  * 类型：对象
  * 包含以下属性：&#x20;
    * viewId
      * 描述：视图的 ID [（如何获取）](../huo-qu-id.md#viewid)
        * 类型：字符串
        * 示例：`"viwABCDEFGHIJKLMN"`
    * anchorId
      * 描述：锚点记录的 ID[（如何获取）](../huo-qu-id.md#recordid)
      * 类型：字符串
      * 示例：`"rec123456789ABCDE"`
    * position
      * 描述：相对于锚点记录的位置
      * 类型：字符串
      * 可选值：
        * "before"：在锚点记录之前
        * "after"：在锚点记录之后
      * 示例：`"after"`
  *   完整示例：

      ```javascript
      {
        viewId: "viwABCDEFGHIJKLMN",
        anchorId: "rec123456789ABCDE",
        position: "after"
      }
      ```
  * 说明：使用 order 可以精确控制新记录在特定视图中的位置。

这个更新后的列表包含了 `fieldKeyType` 和 `typecast` 的详细用法，并移除了 `order` 属性中的必填标记。同时，我们也提供了更多的示例来说明不同设置下的使用方式。

### 响应

#### 成功响应

* 状态码: 201 Created
* 响应体: 返回创建的记录数据。

**示例响应体**

```typescript
{
  "records": [
    {
      "id": "record789",
      "fields": {
        "single line text": "text value 1"
      }
    },
    {
      "id": "record567",
      "fields": {
        "single line text": "text value 2"
      }
    }
  ]
}
```

### 错误响应

* 状态码: 400 Bad Request: 请求体格式错误或缺少必需字段。
* 状态码: 404 Not Found: 指定的表 tableId 不存在。

### 示例代码

{% tabs %}
{% tab title="CURL" %}
```typescript
curl -X POST 'https://app.teable.cn/table/__tableId__/record' \
  -H 'Authorization: Bearer __token__' \
  -H 'Content-Type: application/json' \
  -d '{
    "records": [
      {
        "fields": {
          "Name": "John Doe",
          "Age": 30
        }
      }
    ]
  }'
```
{% endtab %}

{% tab title="JS SDK" %}
```typescript
import { configApi, createRecords } from '@teable/openapi';

configApi({
  endpoint: 'https://app.teable.cn',
  token,
});

const response = await createRecords('__tableId__', {
  records: [
    {
      fields: {
        Name: 'John Doe',
        Age: 30
      }
    }
  ]
});

console.log(response.data);
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
const response = await fetch('https://app.teable.cn/table/__tableId__/record', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer __token__',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    records: [
      {
        fields: {
          Name: 'John Doe',
          Age: 30
        }
      }
    ]
  })
});

console.log(await response.json());
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

response = requests.post(
    'https://app.teable.cn/table/__tableId__/record',
    headers={
        'Authorization': 'Bearer __token__',
        'Content-Type': 'application/json'
    },
    json={
        'records': [
            {
                'fields': {
                    'Name': 'John Doe',
                    'Age': 30
                }
            }
        ]
    }
)

print(response.json())
```
{% endtab %}
{% endtabs %}

