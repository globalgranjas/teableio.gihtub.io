---
description: 这里列举了Teable 所有可用的环境变量以及相关解释
---

# 环境变量



| 环境变量                                         | 描述                                                      | 默认值              | 是否必需 | 示例                                               |
| -------------------------------------------- | ------------------------------------------------------- | ---------------- | ---- | ------------------------------------------------ |
| PUBLIC\_ORIGIN                               | 用于生成完整 URL 的公共源，必须设置为您的应用程序访问地址                         | -                | 是    | https://app.teable.io                            |
| SECRET\_KEY                                  | 用于 JWT、会话和共享的密钥，请使用强密码                                  | defaultSecretKey | 是    | yourStrongSecretKey                              |
| BACKEND\_STORAGE\_PROVIDER                   | 存储提供商，可选值：local、minio、s3                                | local            | -    | s3                                               |
| BACKEND\_STORAGE\_S3\_REGION                 | S3 云存储区域，当 BACKEND\_STORAGE\_PROVIDER 为 s3 时需要配置        | -                | -    | us-east-2                                        |
| BACKEND\_STORAGE\_S3\_ENDPOINT               | S3 云存储端点，当 BACKEND\_STORAGE\_PROVIDER 为 s3 时需要配置        | -                | -    | https://s3.us-east-2.amazonaws.com               |
| BACKEND\_STORAGE\_S3\_ACCESS\_KEY            | S3 云存储访问密钥，当 BACKEND\_STORAGE\_PROVIDER 为 s3 时需要配置      | -                | -    | your\_access\_key                                |
| BACKEND\_STORAGE\_S3\_SECRET\_KEY            | S3 云存储秘密密钥，当 BACKEND\_STORAGE\_PROVIDER 为 s3 时需要配置      | -                | -    | your\_secret\_key                                |
| BACKEND\_CACHE\_PROVIDER                     | 缓存提供商，可选值：sqlite、memory、redis                           | sqlite           | -    | redis                                            |
| BACKEND\_CACHE\_REDIS\_URI                   | Redis 缓存连接 URI，当 BACKEND\_CACHE\_PROVIDER 为 redis 时需要配置 | -                | -    | redis://default:teable@127.0.0.1:6379/0          |
| NEXT\_PUBLIC\_MICROSOFT\_CLARITY\_ID         | Microsoft Clarity 指标 ID，用于启用 Microsoft Clarity 分析       | -                | -    | your-metrics-id                                  |
| NEXT\_PUBLIC\_UMAMI\_WEBSITE\_ID             | 启用 Umami 分析并设置 WEBSITE\_ID                              |                  |      | your-umami-website-id                            |
| NEXT\_PUBLIC\_UMAMI\_URL                     | 启用 Umami 分析并设置分析 script 加载地址                            |                  |      | https://umami.example.com/script.js              |
| TEMPLATE\_SPACE\_ID                          | 模板基础所在的空间 ID，用于模板中心操作的基本信息                              | -                | -    | your-template-space-id                           |
| TEMPLATE\_SITE\_LINK                         | 模板站点链接，需要设置此值才能启用从模板创建的功能                               | -                | -    | https://template.teable.io                       |
| PORT                                         | 应用程序运行的端口                                               | 3000             | -    | 3000                                             |
| LOG\_LEVEL                                   | 日志级别，可选值：fatal、error、warn、info、debug、trace              | info             | -    | debug                                            |
| ENABLE\_GLOBAL\_ERROR\_LOGGING               | 是否启用 4xx 错误日志记录                                         | false            | -    | true                                             |
| PRISMA\_DATABASE\_URL                        | 数据库连接 URL，必须配置                                          | -                | 是    | postgresql://teable:teable@127.0.0.1:5432/teable |
| PUBLIC\_DATABASE\_PROXY                      | 外部数据库访问代理，配置此项才能启用空间数据库外部访问功能                           | -                | -    | 127.0.0.1:5432                                   |
| API\_DOC\_DISENABLED                         | 是否禁用 API 文档                                             | false            | -    | true                                             |
| BACKEND\_GITHUB\_CLIENT\_ID                  | GitHub OAuth 客户端 ID                                     | -                | -    | github\_client\_id                               |
| BACKEND\_GITHUB\_CLIENT\_SECRET              | GitHub OAuth 客户端密钥                                      | -                | -    | github\_client\_secret                           |
| BACKEND\_GOOGLE\_CLIENT\_ID                  | Google OAuth 客户端 ID                                     | -                | -    | google\_client\_id                               |
| BACKEND\_GOOGLE\_CLIENT\_SECRET              | Google OAuth 客户端密钥                                      | -                | -    | google\_client\_secret                           |
| BACKEND\_GOOGLE\_CALLBACK\_URL               | Google OAuth 回调 URL                                     | -                | -    | https://app.teable.io/api/auth/google/callback   |
| BACKEND\_OIDC\_CLIENT\_ID                    | OIDC 客户端 ID                                             | -                | -    | google\_client\_id                               |
| BACKEND\_OIDC\_CLIENT\_SECRET                | OIDC 客户端密钥                                              | -                | -    | google\_client\_secret                           |
| BACKEND\_OIDC\_CALLBACK\_URL                 | OIDC 回调 URL                                             | -                | -    | https://app.teable.io/api/auth/oidc/callback     |
| BACKEND\_OIDC\_USER\_INFO\_URL               | OIDC 用户信息 URL                                           | -                | -    | https://openidconnect.googleapis.com/v1/userinfo |
| BACKEND\_OIDC\_TOKEN\_URL                    | OIDC 令牌 URL                                             | -                | -    | https://oauth2.googleapis.com/token              |
| BACKEND\_OIDC\_AUTHORIZATION\_URL            | OIDC 授权 URL                                             | -                | -    | https://accounts.google.com/o/oauth2/auth        |
| BACKEND\_OIDC\_ISSUER                        | OIDC 发行者 URL                                            | -                | -    | https://accounts.google.com                      |
| BACKEND\_OIDC\_OTHER                         | OIDC 其他配置，JSON 格式                                       | -                | -    | {"scope": \["email", "profile"]}                 |
| SOCIAL\_AUTH\_PROVIDERS                      | 社交认证提供商列表，多个提供商用逗号分隔                                    | -                | -    | github,google,oidc                               |
| BACKEND\_MAIL\_HOST                          | 邮件服务器主机                                                 | -                | -    | smtp.gmail.com                                   |
| BACKEND\_MAIL\_PORT                          | 邮件服务器端口                                                 | -                | -    | 465                                              |
| BACKEND\_MAIL\_SECURE                        | 是否使用安全连接                                                | -                | -    | true                                             |
| BACKEND\_MAIL\_SENDER                        | 发件人邮箱地址                                                 | -                | -    | noreply@company.com                              |
| BACKEND\_MAIL\_SENDER\_NAME                  | 发件人名称                                                   | -                | -    | noreply                                          |
| BACKEND\_MAIL\_AUTH\_USER                    | 邮件服务器认证用户名                                              | -                | -    | username                                         |
| BACKEND\_MAIL\_AUTH\_PASS                    | 邮件服务器认证密码                                               | -                | -    | usertoken                                        |
| BACKEND\_SESSION\_EXPIRES\_IN                | 会话过期时间                                                  | 7d               | -    | 7d                                               |
| BACKEND\_SESSION\_SECRET                     | 会话密钥，如果不设置则使用 SECRET\_KEY                               | SECRET\_KEY      | -    | your\_session\_secret                            |
| BACKEND\_JWT\_EXPIRES\_IN                    | JWT 过期时间                                                | 20d              | -    | 20d                                              |
| BACKEND\_JWT\_SECRET                         | JWT 密钥，如果不设置则使用 SECRET\_KEY                             | SECRET\_KEY      | -    | your\_jwt\_secret                                |
| BACKEND\_RESET\_PASSWORD\_EMAIL\_EXPIRES\_IN | 重置密码邮件过期时间                                              | 30m              | -    | 30m                                              |

