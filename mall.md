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

### CRUD 接口
Django MVT (Model-View-Template) 模式来实现商品的增删改查（CRUD）
    