<h1>Mall</h1>

 ## 商城项目目录
```
mall_system/
├─ .venv/                  # 虚拟环境
├─ manage.py               # Django 项目管理脚本，启动服务器、创建应用等
├─ requirements.txt        # 项目依赖文件（记录 pip 安装包）
├─ .gitignore              # Git 忽略文件配置
├─ static/                 # 存放静态文件：CSS、JS、图片等
├─ templates/              # 存放 HTML 模板文件
├─ .env                    # 环境变量配置文件（敏感信息，如 SECRET_KEY、数据库密码）
├─ mall/                   # Django 项目配置目录
│   ├─ __init__.py         # Python 模块标识文件
│   ├─ settings.py         # Django 项目全局配置文件
│   ├─ urls.py             # URL 总路由配置
│   ├─ asgi.py             # 异步服务器入口（ASGI）
│   └─ wsgi.py             # 同步服务器入口（WSGI）
└─ apps/                   # 自己的应用模块
    ├─ shop/               # 商品模块
    │   ├─ __init__.py
    │   ├─ admin.py        # 后台管理商品
    │   ├─ apps.py         # App 配置
    │   ├─ models.py       # 数据模型
    │   ├─ views.py        # 视图或 API
    │   └─ tests.py        # 单元测试
    ├─ users/              # 用户模块
    │   ├─ __init__.py
    │   ├─ admin.py
    │   ├─ apps.py
    │   ├─ models.py
    │   ├─ views.py
    │   └─ tests.py
    ├─ cart/               # 购物车模块
    │   ├─ __init__.py
    │   ├─ admin.py
    │   ├─ apps.py
    │   ├─ models.py
    │   ├─ views.py
    │   └─ tests.py
    └─ orders/             # 订单模块
        ├─ __init__.py
        ├─ admin.py
        ├─ apps.py
        ├─ models.py
        ├─ views.py
        └─ tests.py
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

    