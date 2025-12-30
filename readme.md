<h1>Mall</h1>

 ## 商城项目目录
```
my_mall_project/
├── manage.py
├── core/                  # 项目配置核心
│   ├── settings.py        # 数据库、Redis、JWT等配置
│   ├── urls.py            # 总路由
│   └── wsgi/asgi.py       # 异步支持（高并发关键）
├── apps/                  # 业务逻辑应用
│   ├── products/          # 商品模块（增删改查）
│   │   ├── models.py      # MySQL 表定义
│   │   ├── views.py       # 业务逻辑
│   │   ├── serializers.py # 高并发接口通常配合 DRF 使用
│   │   └── urls.py
│   └── users/             # 用户与权限模块
│       ├── models.py      # 自定义用户模型（身份认证）
│       └── permissions.py # 权限控制逻辑
├── middleware/            # 中间件（用于身份校验、流量限制）
│   └── auth_middleware.py
├── utils/                 # 工具类
│   ├── redis_client.py    # 高并发下的缓存处理
│   └── response.py        # 统一响应格式
├── scripts/               # 压力测试或数据初始化脚本
├── requirements.txt       # 依赖包（django, django-redis, djangorestframework-simplejwt等）
└── .env                   # 敏感信息（数据库密码、秘钥）
```
### git提交规范
| 类型       | 用法            |
| -------- | ------------- |
| feat     | 新功能           |
| fix      | 修复 bug        |
| docs     | 文档修改          |
| style    | 格式/样式/空格，不改逻辑 |
| refactor | 重构，不新增功能      |
| test     | 添加/修改测试       |
| chore    | 其他杂事，如依赖、配置   |


### 商城项目系统架构表格（Markdown）
| 层级 / 模块      | 技术 / 工具                               | 功能说明                                        |
| ------------ | ------------------------------------- | ------------------------------------------- |
| **客户端 / 前端** | Web (React / Vue) 或 移动端 App           | 调用后端 API 渲染页面或操作数据                          |
| **API 接口层**  | Django REST Framework (DRF)           | 提供 RESTful API，处理请求和响应，做权限校验、序列化            |
| **Web 服务层**  | Gunicorn + Nginx                      | Gunicorn 多进程处理 Django 请求，Nginx 做反向代理、静态文件服务 |
| **业务逻辑层**    | Django Views / Services / Serializers | 处理商城业务逻辑：商品、购物车、订单、用户管理等                    |
| **数据库**      | PostgreSQL / MySQL                    | 存储核心数据：用户表、商品表、订单表等；支持索引优化查询                |
| **缓存**       | Redis / Memcached                     | 缓存热点数据：商品列表、首页推荐、用户 session，减轻数据库压力         |
| **异步任务**     | Celery + Redis / RabbitMQ             | 异步处理耗时任务：发送邮件、生成订单、库存扣减、消息通知                |
| **安全**       | Django 内置 + JWT / Token               | CSRF 防护、身份认证、权限控制、防 SQL 注入、XSS 防护           |
| **监控 & 日志**  | Prometheus + Grafana / Sentry         | 监控系统性能、记录异常、报警                              |
| **部署 & 运维**  | Docker + Nginx + Gunicorn             | 容器化部署，负载均衡，数据库备份，日志管理                       |

    