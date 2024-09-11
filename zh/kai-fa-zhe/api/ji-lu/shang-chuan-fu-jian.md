---
description: 将本地文件或通过 URL 将文件上传至指定记录中附件字段的末尾
---

# 上传附件

### 路径

POST /table/{tableId}/record/{recordId}/{fieldId}/uploadAttachment

### 请求

#### 路径参数

* tableId (string): 表的唯一标识符[（如何获取）](../huo-qu-id.md#tableid)。
* recordId (string): 要更新的记录的唯一标识符[ (如何获取）](../huo-qu-id.md#recordid)。
* fieldId (string): 要上传到的附件字段 ID [(如何获取)](../huo-qu-id.md#fieldid)



{% hint style="info" %}
附件字段可以上传多个附件，该 API 每次允许上传一个附件到单元格最末尾

如需删除或调整附件顺序请使用[更新记录 API](geng-xin-ji-lu.md)
{% endhint %}

{% hint style="info" %}
fieldId 必须为附件类型字段

通过 API 上传的附件在云端版本中最大为 100m, 在私有化版本中无限制
{% endhint %}

#### 请求体

类型：formData

参数：

* **file（ 可选）**
  * 描述：要更新的记录数据
  * 类型：Buffer 或 ReadStream
* **fileUrl（可选）**
  * 描述：要进行上传的 URL
  * 类型：字符串
  * 示例：`https://app.teable.io/favicon.ico`
  * 说明：file 和 fileUrl 同时只能指定一个，若都制定则优先 file

### 响应

#### 成功响应

* 状态码: 200 OK
* 响应体: 返回更新后的记录数据。

**示例响应体**

```javascript
{
    "id": "rec123456789ABCDE",
    "fields": {
      "fld123456789ABCDE": [
        {
          "id": "act75TiSyhcS7hfrizW",
          "name": "example.jpg",
          "path": "table/example",
          "size": 392903,
          "token": "tokenxxxxx",
          "width": 976,
          "height": 1000,
          "mimetype": "image/jpeg",
          "presignedUrl": "https://sss.teable.io/pvt-assets/table/previewURL"
        }
      ],
    }
}
```

#### 错误响应

* 状态码: 400 Bad Request: 请求体格式错误或缺少必需字段。
* 状态码: 404 Not Found: 指定的表 tableId 或记录 recordId 不存在。

### 示例代码

#### 通过文件上传

{% tabs %}
{% tab title="CURL" %}
通过文件上传

```sh
curl -X POST 'https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment' \
  -H 'Authorization: Bearer __token__' \
  -H 'Content-Type: multipart/form-data' \
  -F 'file=@/path/to/your/file.jpg'
```

通过 URL 上传

```sh
curl -X POST 'https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment' \
  -H 'Authorization: Bearer __token__' \
  -H 'Content-Type: multipart/form-data' \
  -F 'fileUrl=https://example.com/image.jpg'
```
{% endtab %}

{% tab title="JS SDK" %}
```typescript
import { configApi, uploadAttachment } from '@teable/openapi';

configApi({
  endpoint: 'https://app.teable.cn',
  token: '__token__',
});

// Node.js 环境：上传本地文件
const fileBuffer = fs.readFileSync('/path/to/your/file.jpg');
const response = await uploadAttachment('__tableId__', '__recordId__', '__fieldId__', fileBuffer);

console.log(response.data);

// 上传 URL（适用于 Node.js 和浏览器环境）
const response = await uploadAttachment('__tableId__', '__recordId__', '__fieldId__', 'https://example.com/image.jpg');

console.log(response.data);

// 浏览器环境：上传文件
// 假设有一个 file input 元素: <input type="file" id="fileInput">
document.getElementById('fileInput').addEventListener('change', async (event) => {
  const file = event.target.files[0];
  if (file) {
    const response = await uploadAttachment('__tableId__', '__recordId__', '__fieldId__', file);
    console.log(response.data);
  }
});
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
import FormData from 'form-data';
import fs from 'fs';

// Node.js 环境：上传本地文件
const formData = new FormData();
formData.append('file', fs.createReadStream('/path/to/your/file.jpg'));

const response = await fetch('https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer __token__',
    ...formData.getHeaders()
  },
  body: formData
});

console.log(await response.json());

// 上传 URL（适用于 Node.js 和浏览器环境）
const formDataUrl = new FormData();
formDataUrl.append('fileUrl', 'https://example.com/image.jpg');

const responseUrl = await fetch('https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer __token__',
    ...formDataUrl.getHeaders()
  },
  body: formDataUrl
});

console.log(await responseUrl.json());

// 浏览器环境：上传文件
// 假设有一个 file input 元素: <input type="file" id="fileInput">
document.getElementById('fileInput').addEventListener('change', async (event: Event) => {
  const fileInput = event.target as HTMLInputElement;
  const file = fileInput.files?.[0];
  if (file) {
    const formData = new FormData();
    formData.append('file', file);

    const response = await fetch('https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment', {
      method: 'POST',
      headers: {
        'Authorization': 'Bearer __token__'
      },
      body: formData
    });

    console.log(await response.json());
  }
});
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

# 上传本地文件
with open('/path/to/your/file.jpg', 'rb') as file:
    response = requests.post(
        'https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment',
        headers={
            'Authorization': 'Bearer __token__'
        },
        files={'file': file}
    )

print(response.json())

# 上传 URL
response_url = requests.post(
    'https://app.teable.cn/table/__tableId__/record/__recordId__/__fieldId__/uploadAttachment',
    headers={
        'Authorization': 'Bearer __token__'
    },
    data={'fileUrl': 'https://example.com/image.jpg'}
)

print(response_url.json())
```
{% endtab %}
{% endtabs %}

