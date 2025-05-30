# 农产品销售管理系统

## 项目介绍
本项目是一个现代化的农产品销售管理系统，采用前后端分离架构设计，提供农产品管理、销售、订单处理等功能。系统具有良好的用户界面和完善的后台管理功能。

系统主要功能包括：

1. **用户管理**
   - 用户注册与登录：支持农产品卖家和普通消费者两种角色注册和登录
   - 用户认证与授权：基于JWT的安全认证机制，不同角色拥有不同的权限
   - 个人资料管理：用户可以查看和修改个人信息

2. **产品管理**
   - 产品发布：卖家可以发布新的农产品，包括产品名称、价格、库存、描述和图片等信息
   - 产品编辑：卖家可以修改已发布产品的信息
   - 产品下架：卖家可以下架不再销售的产品
   - 产品分类：支持多种农产品分类，方便用户浏览和查询

3. **购物功能**
   - 产品浏览：消费者可以浏览所有在售农产品
   - 购物车管理：消费者可以将产品添加到购物车、调整数量或移除产品
   - 订单创建：消费者可以将购物车中的产品生成订单

4. **订单管理**
   - 消费者订单查看：消费者可以查看自己的所有订单及详情
   - 卖家订单处理：卖家可以查看收到的订单并更新订单状态（如确认接单、发货等）
   - 订单状态跟踪：消费者可以跟踪订单的处理进度

5. **文件管理**
   - 图片上传：支持农产品图片的上传和存储

系统对不同用户角色提供了不同的操作界面和功能：
- 游客：可以浏览产品但无法购买
- 消费者：可以浏览产品、加入购物车、下单购买、查看订单历史
- 卖家：可以管理自己的产品、处理收到的订单

## 技术栈

### 前端技术栈
- Vue 3.5.13
- TypeScript
- Vite 6.0.5
- Element Plus 2.9.3
- Pinia 2.3.1
- Vue Router 4.5.0
- Axios

### 后端技术栈
- Java 21
- Spring Boot 3.2.3
- Spring Security
- Spring Data JPA
- MySQL
- Flyway
- JWT
- Swagger/OpenAPI
- Lombok

## 项目结构

```
agriculturalSales/
├── frontend/                       # 前端项目目录
│   ├── src/                        # 源代码目录
│   │   ├── assets/                 # 静态资源文件
│   │   ├── api/                    # API请求封装
│   │   │   ├── auth.ts             # 认证相关API
│   │   │   ├── cart.ts             # 购物车相关API
│   │   │   ├── order.ts            # 订单相关API
│   │   │   ├── product.ts          # 产品相关API
│   │   │   └── user.ts             # 用户相关API
│   │   ├── components/             # 通用组件
│   │   │   └── ImageUpload.vue     # 图片上传组件
│   │   ├── router/                 # 路由配置
│   │   │   └── index.ts            # 路由定义
│   │   ├── stores/                 # 状态管理
│   │   │   └── user.ts             # 用户状态管理
│   │   ├── types/                  # TypeScript类型定义
│   │   │   └── order.ts            # 订单相关类型定义
│   │   ├── utils/                  # 工具函数
│   │   │   ├── request.ts          # HTTP请求封装
│   │   │   └── image.ts            # 图片处理工具
│   │   ├── views/                  # 页面组件
│   │   │   ├── Home.vue            # 首页
│   │   │   ├── Login.vue           # 登录页
│   │   │   ├── Register.vue        # 注册页
│   │   │   ├── ProductList.vue     # 产品列表页
│   │   │   ├── Cart.vue            # 购物车页
│   │   │   ├── OrderList.vue       # 订单列表页
│   │   │   ├── OrderDetail.vue     # 订单详情页
│   │   │   ├── ProductManagement.vue # 产品管理页(卖家)
│   │   │   ├── SellerOrders.vue    # 卖家订单管理页
│   │   │   └── Profile.vue         # 个人资料页
│   │   ├── App.vue                 # 主应用组件
│   │   ├── main.ts                 # 入口文件
│   │   └── style.css               # 全局样式
│   ├── public/                     # 静态资源
│   ├── dist/                       # 构建输出目录
│   ├── index.html                  # HTML入口文件
│   ├── tsconfig.json               # TypeScript配置
│   ├── vite.config.ts              # Vite配置
│   └── package.json                # 项目依赖配置
│
└── backend/                        # 后端项目目录
    ├── src/                        # 源代码目录
    │   ├── main/
    │   │   ├── java/com/example/farmproducts/
    │   │   │   ├── config/         # 配置类
    │   │   │   │   ├── JwtAuthenticationFilter.java # JWT认证过滤器
    │   │   │   │   ├── JwtTokenUtil.java         # JWT工具类
    │   │   │   │   ├── SecurityConfig.java       # 安全配置
    │   │   │   │   ├── SwaggerConfig.java        # Swagger配置
    │   │   │   │   └── WebConfig.java            # Web配置
    │   │   │   ├── controller/     # 控制器
    │   │   │   │   ├── AuthController.java        # 认证控制器
    │   │   │   │   ├── CartController.java        # 购物车控制器
    │   │   │   │   ├── FileController.java        # 文件控制器
    │   │   │   │   ├── OrderController.java       # 订单控制器
    │   │   │   │   ├── ProductController.java     # 产品控制器
    │   │   │   │   └── UserProfileController.java # 用户资料控制器
    │   │   │   ├── dto/           # 数据传输对象
    │   │   │   │   ├── AuthRequest.java           # 认证请求DTO
    │   │   │   │   ├── AuthResponse.java          # 认证响应DTO
    │   │   │   │   ├── CartItemRequest.java       # 购物车项请求DTO
    │   │   │   │   ├── CartItemResponse.java      # 购物车项响应DTO
    │   │   │   │   ├── OrderItemRequest.java      # 订单项请求DTO
    │   │   │   │   ├── OrderItemResponse.java     # 订单项响应DTO
    │   │   │   │   ├── OrderRequest.java          # 订单请求DTO
    │   │   │   │   ├── OrderResponse.java         # 订单响应DTO
    │   │   │   │   ├── ProductRequest.java        # 产品请求DTO
    │   │   │   │   ├── ProductResponse.java       # 产品响应DTO
    │   │   │   │   ├── RegisterRequest.java       # 注册请求DTO
    │   │   │   │   ├── UserProfileRequest.java    # 用户资料请求DTO
    │   │   │   │   └── UserProfileResponse.java   # 用户资料响应DTO
    │   │   │   ├── entity/        # 实体类
    │   │   │   │   ├── CartItem.java              # 购物车项实体
    │   │   │   │   ├── Order.java                 # 订单实体
    │   │   │   │   ├── OrderItem.java             # 订单项实体
    │   │   │   │   ├── OrderStatus.java           # 订单状态枚举
    │   │   │   │   ├── Product.java               # 产品实体
    │   │   │   │   ├── ProductType.java           # 产品类型实体
    │   │   │   │   ├── User.java                  # 用户实体
    │   │   │   │   └── UserRole.java              # 用户角色枚举
    │   │   │   ├── enums/         # 枚举类
    │   │   │   ├── exception/     # 异常处理
    │   │   │   ├── repository/    # 数据访问层
    │   │   │   │   ├── CartItemRepository.java    # 购物车项仓库
    │   │   │   │   ├── OrderItemRepository.java   # 订单项仓库
    │   │   │   │   ├── OrderRepository.java       # 订单仓库
    │   │   │   │   ├── ProductRepository.java     # 产品仓库
    │   │   │   │   └── UserRepository.java        # 用户仓库
    │   │   │   ├── security/      # 安全配置
    │   │   │   │   └── CustomUserDetails.java     # 自定义用户详情
    │   │   │   ├── service/       # 业务逻辑层
    │   │   │   │   ├── CartService.java           # 购物车服务接口
    │   │   │   │   ├── FileService.java           # 文件服务接口
    │   │   │   │   ├── OrderService.java          # 订单服务接口
    │   │   │   │   ├── ProductService.java        # 产品服务接口
    │   │   │   │   ├── UserDetailsService.java    # 用户详情服务接口
    │   │   │   │   ├── UserService.java           # 用户服务接口
    │   │   │   │   └── impl/                      # 服务实现
    │   │   │   │       ├── CartServiceImpl.java     # 购物车服务实现
    │   │   │   │       ├── FileServiceImpl.java     # 文件服务实现
    │   │   │   │       ├── OrderServiceImpl.java    # 订单服务实现
    │   │   │   │       ├── ProductServiceImpl.java  # 产品服务实现
    │   │   │   │       ├── UserDetailsServiceImpl.java # 用户详情服务实现
    │   │   │   │       └── UserServiceImpl.java     # 用户服务实现
    │   │   │   └── FarmProductsApplication.java   # 应用启动类
    │   │   └── resources/         # 资源文件
    │   │       ├── application.properties         # 基础配置属性
    │   │       ├── application.yml                # YAML格式配置
    │   │       └── db/migration/                  # 数据库迁移脚本
    │   │           ├── V1__init.sql               # 初始化脚本
    │   │           ├── V2__create_product_table.sql # 产品表创建脚本
    │   │           ├── V3__create_cart_table.sql  # 购物车表创建脚本
    │   │           ├── V4__create_order_tables.sql # 订单表创建脚本
    │   │           └── V5__add_user_profile_fields.sql # 用户资料字段添加脚本
    │   └── test/                  # 测试代码
    ├── target/                     # 构建输出目录
    └── pom.xml                     # Maven 项目配置
```

## 功能详细说明

### 用户模块
1. **用户注册**
   - 支持用户选择角色（消费者或卖家）进行注册
   - 注册时需提供基本信息，如用户名、密码、联系方式等
   - 系统自动进行用户名唯一性验证

2. **用户登录**
   - 提供基于JWT的安全登录机制
   - 登录成功后返回令牌，后续接口调用需携带令牌
   - 对不同角色提供不同的登录后界面和权限

3. **个人资料管理**
   - 用户可以查看和编辑个人资料
   - 包括名称、联系方式、地址等个人信息
   - 支持密码修改和安全设置

### 产品模块
1. **产品管理（卖家）**
   - 产品的CRUD（创建、读取、更新、删除）操作
   - 支持产品图片上传和管理
   - 支持对产品进行分类、定价和库存管理
   - 提供产品上架、下架功能

2. **产品浏览（所有用户）**
   - 产品列表展示，支持分页查询
   - 产品详情查看
   - 支持按类别、价格等条件筛选产品
   - 支持产品搜索功能

### 购物模块
1. **购物车管理**
   - 将产品添加到购物车
   - 调整购物车中产品的数量
   - 从购物车中移除产品
   - 购物车商品汇总和结算功能

2. **订单处理**
   - 下单功能：将购物车中的商品转化为订单
   - 订单状态跟踪：待确认、待发货、已发货、已完成等
   - 订单历史查询：查看历史订单记录和详情

3. **卖家订单管理**
   - 查看收到的订单列表
   - 更新订单状态（确认订单、发货等）
   - 订单统计和管理功能

## 环境要求

### 前端环境要求
- Node.js 16+
- npm 或 yarn 包管理器

### 后端环境要求
- JDK 21
- Maven 3.6+
- MySQL 8.0+

## 启动方式

### 前端启动
1. 进入前端项目目录：
```bash
cd frontend
```

2. 安装依赖：
```bash
npm install
```

3. 开发环境启动：
```bash
npm run dev
```

4. 生产环境构建：
```bash
npm run build
```

### 后端启动
1. 进入后端项目目录：
```bash
cd backend
```

2. 编译项目：
```bash
mvn clean install
```

3. 运行项目：
```bash
mvn spring-boot:run
```

## 配置说明

### 前端配置
- 开发环境配置文件：`.env.development`
- 生产环境配置文件：`.env.production`

### 后端配置
- 主配置文件：`application.properties`和`application.yml`
   - 服务器端口配置
   - 数据库连接配置
   - JWT配置
   - 文件上传配置
- 数据库迁移：使用Flyway管理数据库版本和结构
   - 迁移脚本位于`src/main/resources/db/migration`目录



## 数据库信息

### 用户表 (users)

```sql
CREATE TABLE users (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(100) NOT NULL,
    role enum('SELLER', 'CUSTOMER') DEFAULT 'CUSTOMER' NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### 商品表 (products)
```sql
CREATE TABLE products (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    stock INT NOT NULL,
    seller_id BIGINT NOT NULL,
    type ENUM('VEGETABLE', 'FRUIT', 'GRAIN', 'MEAT', 'SEAFOOD', 'OTHER') DEFAULT 'VEGETABLE' NOT NULL,
    image VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (seller_id) REFERENCES users(id)
);
```

### 购物车表 (cart_items)
```sql
CREATE TABLE cart_items (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    user_id BIGINT NOT NULL,
    product_id BIGINT NOT NULL,
    quantity INT NOT NULL,
    image VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

### 订单表 (orders)
```sql
CREATE TABLE orders (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    order_number VARCHAR(50) NOT NULL,
    user_id BIGINT NOT NULL,
    seller_id BIGINT NOT NULL,
    receiver_name VARCHAR(50) NOT NULL,
    receiver_phone VARCHAR(20) NOT NULL,
    receiver_address VARCHAR(255) NOT NULL,
    total_amount DECIMAL(10,2) NOT NULL,
    status enum('PENDING_PAYMENT', 'PENDING_SHIPMENT', 'SHIPPED', 'PENDING_RECEIPT','COMPLETED', 'CANCELLED') DEFAULT 'PENDING_PAYMENT' NOT NULL,
    tracking_number VARCHAR(50),
    shipping_company VARCHAR(50),
    create_time DATETIME NOT NULL,
    pay_time DATETIME,
    ship_time DATETIME,
    complete_time DATETIME,
    created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (seller_id) REFERENCES users(id)
);
```

### 订单项表 (order_items)
```sql
CREATE TABLE order_items (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    order_id BIGINT NOT NULL,
    product_id BIGINT NOT NULL,
    quantity INT NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    total_price DECIMAL(10,2) NOT NULL,
    created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

### 用户表扩展字段 (users)
```sql
ALTER TABLE users
ADD COLUMN real_name VARCHAR(50),
ADD COLUMN phone VARCHAR(20),
ADD COLUMN email VARCHAR(100),
ADD COLUMN address VARCHAR(200);
```

### 索引信息
```sql
CREATE INDEX idx_user_id ON orders(user_id);
CREATE INDEX idx_seller_id ON orders(seller_id);
CREATE INDEX idx_order_number ON orders(order_number);
CREATE INDEX idx_status ON orders(status);
CREATE INDEX idx_order_id ON order_items(order_id);
CREATE INDEX idx_product_id ON order_items(product_id);
```


## 接口文档
- 启动后端服务后，访问 Swagger 文档：`http://localhost:8080/swagger-ui.html`
- API接口分类：
  - 认证接口：用户注册、登录
  - 产品接口：产品CRUD、查询
  - 购物车接口：购物车管理
  - 订单接口：订单管理
  - 用户接口：用户资料管理

## 部署说明
1. 前端部署
   - 执行 `npm run build` 生成静态文件
   - 将 `dist` 目录下的文件部署到 Web 服务器（如Nginx或Apache）
   - 配置服务器将API请求代理到后端服务

2. 后端部署
   - 使用 `mvn package` 打包生成 JAR 文件
   - 使用 `java -jar farm-products-1.0-SNAPSHOT.jar` 命令运行生成的 JAR 文件
   - 配置环境变量或启动参数以适应生产环境需求
