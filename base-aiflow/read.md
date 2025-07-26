# Base-Aiflow 项目文档

## 项目概述

Base-Aiflow 是一个基于 Vue.js 2.x 的管理后台模板项目，集成了 Element UI、Vuex、Vue Router 等主流技术栈。该项目提供了完整的权限控制、路由管理、状态管理、API 请求封装等功能，是一个开箱即用的企业级前端解决方案。

### 技术栈

- **Vue.js 2.6.10** - 渐进式 JavaScript 框架
- **Element UI 2.13.2** - 基于 Vue 的组件库
- **Vue Router 3.0.6** - Vue.js 官方路由管理器
- **Vuex 3.1.0** - Vue.js 的状态管理模式
- **Axios 0.18.1** - HTTP 客户端
- **Sass** - CSS 预处理器
- **Jest** - 单元测试框架

### 主要特性

- ✅ 完整的权限控制系统
- ✅ 响应式布局设计
- ✅ 国际化支持
- ✅ SVG 图标系统
- ✅ Mock 数据服务
- ✅ 代码规范检查 (ESLint)
- ✅ 单元测试支持
- ✅ 热重载开发环境

## 目录结构说明

```
base-aiflow/
├── public/                 # 静态资源目录
│   ├── index.html         # HTML 模板
│   └── favicon.ico        # 网站图标
├── src/                   # 源代码目录
│   ├── api/               # API 接口定义
│   │   ├── table.js       # 表格相关接口
│   │   └── user.js        # 用户相关接口
│   ├── assets/            # 静态资源
│   ├── components/        # 公共组件
│   │   ├── Breadcrumb/    # 面包屑导航组件
│   │   ├── Hamburger/     # 汉堡菜单组件
│   │   └── SvgIcon/       # SVG 图标组件
│   ├── icons/             # SVG 图标文件
│   ├── layout/            # 布局组件
│   │   ├── components/    # 布局相关组件
│   │   └── mixin/         # 布局混入
│   ├── router/            # 路由配置
│   │   └── index.js       # 路由主文件
│   ├── store/             # Vuex 状态管理
│   │   ├── modules/       # 状态模块
│   │   │   ├── app.js     # 应用状态
│   │   │   ├── settings.js # 设置状态
│   │   │   └── user.js    # 用户状态
│   │   ├── getters.js     # 全局 getters
│   │   └── index.js       # store 入口
│   ├── styles/            # 样式文件
│   ├── utils/             # 工具函数
│   │   ├── auth.js        # 认证相关工具
│   │   ├── request.js     # HTTP 请求封装
│   │   ├── validate.js    # 验证工具
│   │   └── index.js       # 通用工具函数
│   ├── views/             # 页面组件
│   │   ├── dashboard/     # 仪表板页面
│   │   ├── login/         # 登录页面
│   │   ├── form/          # 表单页面
│   │   ├── table/         # 表格页面
│   │   ├── tree/          # 树形组件页面
│   │   └── nested/        # 嵌套路由页面
│   ├── App.vue            # 根组件
│   ├── main.js            # 应用入口
│   ├── permission.js      # 权限控制
│   └── settings.js        # 项目配置
├── mock/                  # Mock 数据
│   ├── index.js           # Mock 入口
│   ├── mock-server.js     # Mock 服务器
│   ├── table.js           # 表格数据
│   ├── user.js            # 用户数据
│   └── utils.js           # Mock 工具
├── tests/                 # 测试文件
├── build/                 # 构建输出
├── node_modules/          # 依赖包
├── package.json           # 项目配置
├── vue.config.js          # Vue CLI 配置
├── babel.config.js        # Babel 配置
├── jest.config.js         # Jest 测试配置
├── .eslintrc.js          # ESLint 配置
└── README.md             # 项目说明
```

## 各目录详细说明

### 📁 `src/api/` - API 接口层
存放所有与后端 API 交互的接口定义文件。每个功能模块对应一个 JS 文件，便于管理和维护。

**示例用法：**
```javascript
// src/api/user.js
import request from '@/utils/request'

export function login(data) {
  return request({
    url: '/user/login',
    method: 'post',
    data
  })
}
```

### 📁 `src/components/` - 公共组件
存放可复用的 Vue 组件，这些组件在整个项目中都可以使用。

**现有组件：**
- `SvgIcon/` - SVG 图标组件，支持外部链接和本地 SVG
- `Breadcrumb/` - 面包屑导航组件
- `Hamburger/` - 汉堡菜单组件

### 📁 `src/layout/` - 布局组件
定义应用的整体布局结构，包括侧边栏、顶部导航、主内容区域等。

### 📁 `src/router/` - 路由配置
定义应用的路由规则，包括路由守卫、权限控制等。

### 📁 `src/store/` - 状态管理
使用 Vuex 进行状态管理，按模块划分不同的状态。

**模块说明：**
- `app.js` - 应用全局状态（侧边栏、设备类型等）
- `user.js` - 用户相关状态（用户信息、token 等）
- `settings.js` - 应用设置状态

### 📁 `src/utils/` - 工具函数
存放各种工具函数和辅助方法。

**主要文件：**
- `request.js` - Axios 请求封装，包含拦截器配置
- `auth.js` - 认证相关工具函数
- `validate.js` - 数据验证工具
- `index.js` - 通用工具函数

### 📁 `src/views/` - 页面组件
存放各个页面的 Vue 组件，按功能模块组织。

### 📁 `src/icons/` - 图标资源
存放 SVG 图标文件，配合 `SvgIcon` 组件使用。

### 📁 `mock/` - 模拟数据
在开发阶段提供模拟的 API 数据，便于前端开发和测试。

## 自定义组件指南

### 1. 创建新组件

在 `src/components/` 目录下创建新的组件文件夹：

```bash
mkdir src/components/MyComponent
```

### 2. 组件结构

每个组件建议包含以下文件：

```
MyComponent/
├── index.vue          # 主组件文件
├── README.md          # 组件说明文档
└── __tests__/         # 测试文件（可选）
```

### 3. 组件开发规范

#### 3.1 组件命名
- 使用 PascalCase 命名组件
- 组件名应该是多个单词，避免与 HTML 元素冲突

```vue
<!-- MyComponent/index.vue -->
<template>
  <div class="my-component">
    <!-- 组件内容 -->
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  props: {
    // 定义 props
  },
  data() {
    return {
      // 组件数据
    }
  },
  methods: {
    // 组件方法
  }
}
</script>

<style lang="scss" scoped>
.my-component {
  // 组件样式
}
</style>
```

#### 3.2 Props 定义
使用详细的 props 定义，包含类型、默认值、验证等：

```javascript
props: {
  title: {
    type: String,
    required: true,
    default: ''
  },
  count: {
    type: Number,
    default: 0,
    validator: function (value) {
      return value >= 0
    }
  }
}
```

#### 3.3 事件通信
使用 `$emit` 向父组件发送事件：

```javascript
methods: {
  handleClick() {
    this.$emit('click', { data: 'some data' })
  }
}
```

### 4. 组件注册

#### 4.1 全局注册
在 `src/main.js` 中全局注册组件：

```javascript
import MyComponent from '@/components/MyComponent'

Vue.component('MyComponent', MyComponent)
```

#### 4.2 局部注册
在需要使用组件的页面中局部注册：

```javascript
import MyComponent from '@/components/MyComponent'

export default {
  components: {
    MyComponent
  }
}
```

### 5. 组件使用示例

```vue
<template>
  <div>
    <my-component 
      :title="title"
      :count="count"
      @click="handleComponentClick"
    />
  </div>
</template>

<script>
import MyComponent from '@/components/MyComponent'

export default {
  components: {
    MyComponent
  },
  data() {
    return {
      title: 'My Title',
      count: 10
    }
  },
  methods: {
    handleComponentClick(data) {
      console.log('Component clicked:', data)
    }
  }
}
</script>
```

## 开发指南

### 环境要求
- Node.js >= 8.9
- npm >= 3.0.0

### 安装依赖
```bash
npm install
```

### 开发模式
```bash
npm run dev
```

### 构建生产版本
```bash
npm run build:prod
```

### 代码检查
```bash
npm run lint
```

### 运行测试
```bash
npm run test:unit
```

## 配置说明

### 环境变量
项目支持多环境配置，可以在根目录创建以下文件：
- `.env.development` - 开发环境配置
- `.env.production` - 生产环境配置
- `.env.staging` - 预发布环境配置

### API 配置
在 `src/utils/request.js` 中配置 API 基础 URL：
```javascript
const service = axios.create({
  baseURL: process.env.VUE_APP_BASE_API,
  timeout: 5000
})
```

### 路由配置
在 `src/router/index.js` 中配置路由规则和权限控制。

### 状态管理
在 `src/store/modules/` 中添加新的状态模块。

## 部署说明

### 构建
```bash
npm run build:prod
```

### 部署到服务器
将 `dist` 目录下的文件部署到 Web 服务器即可。

### Nginx 配置示例
```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /path/to/dist;
    index index.html;
    
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

## 常见问题

### 1. 图标不显示
确保 SVG 文件已放置在 `src/icons/svg/` 目录下，并且文件名正确。

### 2. 路由跳转问题
检查路由配置和权限设置是否正确。

### 3. API 请求失败
检查 `src/utils/request.js` 中的配置和后端 API 地址是否正确。

### 4. 样式问题
确保正确引入了 Element UI 的样式文件。

## 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 联系方式

如有问题或建议，请通过以下方式联系：
- 提交 Issue
- 发送邮件至项目维护者

---

**注意：** 这是一个基础模板项目，在实际使用中请根据具体需求进行定制和扩展。 