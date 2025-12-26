# src/index.pug

## 文件用途
项目的主页面模板文件，使用 Pug 模板引擎定义网站的整体 HTML 结构，通过引入各个组件模块构建完整的页面。

## 核心功能
1. **页面结构定义**：定义 HTML5 文档的基本结构
2. **组件引入**：引入 head、intro、main、scripts 等组件模块
3. **模板渲染**：使用 config.json 中的数据渲染页面内容

## 关键实现逻辑

### 文档声明与根元素
```pug
doctype html
html(lang="en")
```
- **doctype html**: 声明文档类型为 HTML5
- **html(lang="en")**: 定义根元素，语言属性设置为英语

### 头部引入
```pug
include components/head
```
- 引入 components/head.pug 组件，包含页面的 meta 标签、样式表引用等头部信息

### 主体内容
```pug
body
  main
    include components/intro.pug
    include components/main.pug
    include components/scripts
```
- **body**: 定义页面主体区域
- **main**: 使用语义化标签包裹主要内容
- **include components/intro.pug**: 引入首页介绍区域组件
- **include components/main.pug**: 引入主卡片区域组件
- **include components/scripts**: 引入脚本组件，包含页面所需的 JavaScript 文件和配置

## 重要注意事项
1. **组件顺序**：组件的引入顺序决定了页面内容的显示顺序，intro 在前，main 在后
2. **语言设置**：html 标签的 lang 属性设置为 "en"，如需支持中文可修改为 "zh-CN"
3. **语义化标签**：使用 main 标签包裹主要内容，符合 HTML5 语义化规范
4. **模板数据**：此文件本身不直接使用模板变量，数据通过引入的组件文件传递
5. **文件编码**：确保文件使用 UTF-8 编码保存，以支持中文等特殊字符
6. **缩进规范**：Pug 使用缩进表示嵌套关系，保持一致的缩进（2 空格或 4 空格）

## 相关文件
- config.json - 模板渲染的数据源
- src/components/head.pug - 头部组件
- src/components/intro.pug - 介绍区域组件
- src/components/main.pug - 主卡片组件
- src/components/scripts.pug - 脚本组件
- gulpfile.js - 构建脚本，负责将 Pug 编译为 HTML
