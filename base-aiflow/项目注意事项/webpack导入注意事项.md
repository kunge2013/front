# Webpack 导入注意事项

## 概述

在Vue项目中，有两种主要的导入方式：`@` 别名导入和 `./` 相对路径导入。正确使用这两种导入方式可以提高代码的可维护性和可读性。

## 配置说明

### @ 别名配置

项目中的 `@` 别名被配置为指向 `src` 目录：

**jsconfig.json 配置：**
```json
{
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
        "@/*": ["src/*"]
    }
  }
}
```

**vue.config.js 配置：**
```javascript
configureWebpack: {
  resolve: {
    alias: {
      '@': resolve('src')
    }
  }
}
```

## 导入方式对比

### 1. @ 别名导入

**使用场景：**
- 导入 `src` 目录下的任何文件
- 导入公共组件、工具函数、API等
- 导入样式文件

**语法：**
```javascript
// 导入组件
import Layout from '@/layout'
import SvgIcon from '@/components/SvgIcon'

// 导入工具函数
import { getToken } from '@/utils/auth'
import request from '@/utils/request'

// 导入API
import { login } from '@/api/user'

// 导入样式
import '@/styles/index.scss'
import '@/styles/mixin.scss'
```

**文件名规则：**
- 当导入目录时，会自动查找该目录下的 `index` 文件
- 支持多种扩展名：`.js`, `.vue`, `.ts` 等
- 例如：`@/components/SvgIcon` 实际解析为 `src/components/SvgIcon/index.vue`

### 2. ./ 相对路径导入

**使用场景：**
- 导入当前目录的文件
- 导入子目录的文件
- 导入同级目录的文件

**语法：**
```javascript
// 导入当前目录的文件
import App from './App'
import store from './store'
import router from './router'

// 导入子目录的文件
import { Navbar, Sidebar, AppMain } from './components'
import ResizeMixin from './mixin/ResizeHandler'

// 导入同级目录的文件
import getters from './getters'
import app from './modules/app'
```

## 最佳实践

### 推荐使用 @ 的情况：

1. **导入 src 目录下的公共文件**
   ```javascript
   import Layout from '@/layout'
   import { getToken } from '@/utils/auth'
   ```

2. **导入组件库**
   ```javascript
   import SvgIcon from '@/components/SvgIcon'
   import Breadcrumb from '@/components/Breadcrumb'
   ```

3. **导入工具函数和API**
   ```javascript
   import request from '@/utils/request'
   import { login, logout } from '@/api/user'
   ```

4. **导入样式文件**
   ```javascript
   import '@/styles/index.scss'
   import '@/styles/variables.scss'
   ```

### 推荐使用 ./ 的情况：

1. **导入当前目录的文件**
   ```javascript
   import App from './App'
   import store from './store'
   ```

2. **导入子目录的文件**
   ```javascript
   import { Navbar, Sidebar } from './components'
   import ResizeMixin from './mixin/ResizeHandler'
   ```

3. **导入同级目录的文件**
   ```javascript
   import getters from './getters'
   import app from './modules/app'
   ```

## 注意事项

### 1. 文件名解析规则

- **@ 导入**：会自动查找目录下的 `index` 文件
- **./ 导入**：需要明确指定文件名或使用相对路径

### 2. 路径解析顺序

当使用 `@` 导入目录时，解析顺序为：
1. `index.js`
2. `index.vue`
3. `index.ts`
4. 其他支持的扩展名

### 3. 常见错误

**错误示例：**
```javascript
// ❌ 错误：文件不存在
import SvgIcon from '@/components/SvgIcon/SvgIcon.js'

// ❌ 错误：路径不正确
import Layout from '@/layout/Layout.vue'
```

**正确示例：**
```javascript
// ✅ 正确：自动查找 index.vue
import SvgIcon from '@/components/SvgIcon'

// ✅ 正确：明确指定文件名
import Layout from '@/layout/index.vue'
```

### 4. 性能考虑

- **@ 导入**：路径更短，便于维护，但需要webpack解析别名
- **./ 导入**：路径明确，解析更快，但路径可能较长

## 项目中的实际应用

### 当前项目结构示例：

```
src/
├── components/
│   ├── SvgIcon/
│   │   └── index.vue
│   ├── Breadcrumb/
│   │   └── index.vue
│   └── Hamburger/
│       └── index.vue
├── utils/
│   ├── auth.js
│   ├── request.js
│   └── validate.js
├── api/
│   ├── user.js
│   └── table.js
└── styles/
    ├── index.scss
    ├── variables.scss
    └── mixin.scss
```

### 导入示例：

```javascript
// 使用 @ 导入
import SvgIcon from '@/components/SvgIcon'           // 自动查找 index.vue
import { getToken } from '@/utils/auth'              // 直接导入 auth.js
import { login } from '@/api/user'                   // 直接导入 user.js
import '@/styles/index.scss'                         // 导入样式文件

// 使用 ./ 导入
import App from './App'                              // 当前目录
import store from './store'                          // 当前目录
import { Navbar } from './components'                // 子目录
```

## 总结

- **@ 导入**：适用于导入 `src` 目录下的公共文件，路径简洁，便于维护
- **./ 导入**：适用于导入当前目录及其子目录的文件，路径明确
- 根据文件位置和用途选择合适的导入方式
- 注意文件名解析规则，避免路径错误 