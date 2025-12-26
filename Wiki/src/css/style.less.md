# src/css/style.less

## 文件用途
主样式文件，通过 @import 指令引入所有 LESS 模块，作为样式系统的入口文件。

## 核心功能
1. **样式模块化**：将样式按功能模块组织
2. **统一入口**：提供单一的样式入口点
3. **依赖管理**：管理样式文件之间的依赖关系

## 关键实现逻辑

### 导入语句
```less
@import 'common/variable';
@import 'common/common';
@import 'common/icon';

@import 'layout/layout';

@import 'intro/intro';
@import 'main/main';
```

### 模块说明

#### 通用模块（common）
- **variable**: 定义 LESS 变量和 CSS 自定义属性
- **common**: 定义通用样式和重置样式
- **icon**: 定义图标样式

#### 布局模块（layout）
- **layout**: 定义页面布局和容器样式

#### 功能模块
- **intro**: 定义首页介绍区域样式
- **main**: 定义主卡片区域样式

## 重要注意事项
1. **导入顺序**：导入顺序很重要，变量定义必须在变量使用之前
2. **文件路径**：使用相对路径，确保文件位置正确
3. **模块化设计**：每个模块负责特定的功能，保持代码组织清晰
4. **编译顺序**：Gulp 会按导入顺序编译 LESS 文件
5. **变量作用域**：在 variable.less 中定义的变量可以在所有导入的文件中使用

## 相关文件
- src/css/common/variable.less - 变量定义文件
- src/css/common/common.less - 通用样式文件
- src/css/common/icon.less - 图标样式文件
- src/css/layout/layout.less - 布局样式文件
- src/css/intro/intro.less - 介绍区域样式文件
- src/css/main/main.less - 主卡片样式文件
- gulpfile.js - 构建脚本，负责将 LESS 编译为 CSS
