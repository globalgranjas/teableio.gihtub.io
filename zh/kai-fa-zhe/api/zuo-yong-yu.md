# 作用域

> 作用域表示个人访问令牌对资源可以执行的操作

个人访问令牌只能访问授予它们的范围所涵盖的 API 端点。可用范围的完整参考信息如下。

除了请求正确的作用域外，令牌还必须拥有执行操作所需的资源和权限。

**例如：** 如果个人访问令牌被授予的作用域是`record|read`，并添加了一个数据库，那么就可以在访问在该数据库中的表里面的记录，但是不允许使用对该数据库中的表进行写入记录操作，并且也不能访问除了该数据库中之外的表记录。

## 作用域范围

所有用户都可以使用以下范围。

### 空间

| Scope                | 描述             |
| -------------------- | -------------- |
| space\|create        | 创建空间           |
| space\|update        | 更新空间           |
| space\|delete        | 删除空间           |
| space\|read          | 读取空间           |
| space\|invite\_email | 通过电子邮件邀请用户加入空间 |
| space\|invite\_link  | 生成邀请链接以加入空间    |
| space\|grant\_role   | 授予角色给用户        |

### 数据库

| Scope               | 描述            |
| ------------------- | ------------- |
| base\|create        | 创建数据库         |
| base\|update        | 更新数据库         |
| base\|delete        | 删除数据库         |
| base\|read          | 读取数据库         |
| base\|invite\_email | 通过电子邮件邀请加入数据库 |
| base\|invite\_link  | 生成邀请链接以加入数据库  |

### 数据表

| Scope         | 描述     |
| ------------- | ------ |
| table\|create | 创建表格   |
| table\|update | 更新表格   |
| table\|delete | 删除表格   |
| table\|read   | 读取表格   |
| table\|import | 导入表格数据 |

### 视图

| Scope        | 描述   |
| ------------ | ---- |
| view\|create | 创建视图 |
| view\|update | 更新视图 |
| view\|delete | 删除视图 |
| view\|read   | 读取视图 |

### 字段

| Scope         | 描述   |
| ------------- | ---- |
| field\|create | 创建字段 |
| field\|update | 更新字段 |
| field\|delete | 删除字段 |
| field\|read   | 读取字段 |

### 记录

| Scope           | 描述      |
| --------------- | ------- |
| record\|create  | 创建记录    |
| record\|update  | 更新记录    |
| record\|delete  | 删除记录    |
| record\|read    | 读取记录    |
| record\|comment | 对记录进行评论 |



{% hint style="info" %}
注意，暂时无法通过 API Token 列出自己所在的全部空间站下的数据库，必须指定 spaceId
{% endhint %}

