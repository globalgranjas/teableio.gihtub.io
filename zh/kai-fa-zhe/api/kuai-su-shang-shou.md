---
description: 本文将介绍如何快速上手 Teable API 以及使用 API SDK
---

# 快速上手

## 获取访问令牌

个人访问令牌是一种用于身份验证和授权的令牌。用于在为自己、客户或公司开发集成和扩展时对Teable的API进行身份验证。

### 第一步：创建一个访问令牌

1. 进入[令牌管理页面](https://app.teable.cn/setting/personal-access-token)，点击”创建令牌“按钮来创建一个新的个人访问令牌。
2. 为您的令牌选择一个有效期，注意改有效期无法修改。
3. 为您的令牌添加可访问的数据库或者空间。令牌将只能在分配给它的数据库和空间中读取和写入数据。

{% hint style="info" %}
一旦您的令牌创建成功，我们只会向您显示一次，我们建议您将其复制粘贴到你认为安全的地方进行存储。
{% endhint %}

### 第二步：调用 API 接口[​](https://developers.vika.cn/api/quick-start#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E8%B0%83%E7%94%A8-api-%E6%8E%A5%E5%8F%A3%E5%AE%9E%E7%8E%B0%E6%95%B0%E6%8D%AE%E7%9A%84%E5%A2%9E%E5%88%A0%E6%94%B9%E6%9F%A5) <a href="#di-er-bu-diao-yong-api-jie-kou-shi-xian-shu-ju-de-zeng-shan-gai-cha" id="di-er-bu-diao-yong-api-jie-kou-shi-xian-shu-ju-de-zeng-shan-gai-cha"></a>

你可以选择以下任一方式向 API 服务器发送请求, 首先选择一个你想要操作的表格，并获得表格 ID [(如何获取？)](huo-qu-id.md#tableid)

{% hint style="info" %}
注意：在执行下列代码前，你需要将 `__tableId__` 和 `__token__` 替换为真实的表格 ID 和 API Token。
{% endhint %}

### 获取记录

以调用 "获取记录" API 接口为例，下面是一些常见语言的 HTTPS 请求示例：

{% tabs %}
{% tab title="CURL" %}
```bash
curl "https://app.teable.cn/api/table/__tableId__/record" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer __token___"
```
{% endtab %}

{% tab title="JS SDK" %}
```typescript
import { configApi, getRecords } from '@teable/openapi';

const token = '__token__';
const tableId = '__tableId__';

configApi({
  endpoint: 'https://app.teable.cn',
  token,
});

getRecords(tableId)
  .then(res => console.log(res.data))
  .catch(error => console.error('Failed to fetch records:', error));

// or use await in async function
// const res = await getRecords(__tableId__);
```
{% endtab %}

{% tab title="TypeScript" %}
### Fetch

```typescript
async function getRecords(token: string, tableId: string): Promise<{
    records: {
        id: string;
        fields: Record<string, unknown>;
        name?: string;
        autoNumber?: number;
        createdTime?: string;
        lastModifiedTime?: string;
        createdBy?: string;
        lastModifiedBy?: string;
    }[];
}> {
  const url = `https://app.teable.cn/api/table/${tableId}/record`;
  const response = await fetch(url, {
    method: 'GET',
    headers: {
      'Authorization': `Bearer ${token}`,
      'Content-Type': 'application/json'
    }
  });

  return await response.json();
}

const token = '__token__';
const tableId = '__tableId__';

getRecords(token, tableId)
  .then(data => console.log(data))
  .catch(error => console.error('Failed to fetch records:', error));

```

### Axios

```typescript
import axios from 'axios';

async function getRecords(token: string, tableId: string) {
  const response = await axios.get(`https://app.teable.cn/api/table/${tableId}/record`, {
    headers: {
      'Authorization': `Bearer ${token}`,
      'Content-Type': 'application/json'
    }
  });
  return response.data;
}

const token = '__token__';
const tableId = '__tableId__';

getRecords(token, tableId)
  .then(data => console.log(data))
  .catch(error => console.error('Failed to fetch records:', error));
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

def get_records(token: str, table_id: str):
    url = f'https://app.teable.cn/api/table/{table_id}/record'
    headers = {
        'Authorization': f'Bearer {token}',
        'Content-Type': 'application/json'
    }
    
    response = requests.get(url, headers=headers)
    response.raise_for_status()
    return response.json()

token = '__token__'
table_id = '__tableId__'

try:
    records = get_records(token, table_id)
    print(records)
except Exception as e:
    print(f'Failed to fetch records: {e}')
```
{% endtab %}
{% endtabs %}

获取记录时支持指定 视图，筛选条件，排序条件，fieldKeyType (以 Id 还是 Name 作为字段 key 进行返回）, cellFormat（返回 JSON 还是纯文本格式的单元格数据）。我们为开发者提供了一个快捷的[查询参数构建器](https://app.teable.cn/developer/tool/query-builder)，可以帮助轻松构建自定义的请求。\


## 更多 API

记录增删改查 API 作为最常用的 API 我们准备了完善的说明文档

{% content-ref url="ji-lu/chuang-jian-ji-lu.md" %}
[chuang-jian-ji-lu.md](ji-lu/chuang-jian-ji-lu.md)
{% endcontent-ref %}

{% content-ref url="ji-lu/geng-xin-ji-lu.md" %}
[geng-xin-ji-lu.md](ji-lu/geng-xin-ji-lu.md)
{% endcontent-ref %}

{% content-ref url="ji-lu/shan-chu-ji-lu.md" %}
[shan-chu-ji-lu.md](ji-lu/shan-chu-ji-lu.md)
{% endcontent-ref %}

其他的 API 可以在 [Swagger文档](https://app.teable.cn/docs) （可以在线调试）或者 [Redoc文档](https://app.teable.cn/redocs) （说明信息更丰富）中查看，这里包括了 Teable 所有可用的 API。

