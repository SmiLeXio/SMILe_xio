# HomePage 项目总览

## 项目简介
HomePage 是一个个人主页项目，采用现代化的前端技术栈构建，包含动态背景动画、响应式设计和优雅的用户界面。项目使用 Pug 模板引擎、LESS 预处理器和 Gulp 构建工具，提供流畅的用户体验和视觉效果。

## 技术栈

### 前端技术
- **HTML5**: 使用语义化标签构建页面结构
- **Pug**: 模板引擎，用于生成 HTML
- **LESS**: CSS 预处理器，提供变量、嵌套等功能
- **JavaScript (ES6+)**: 使用现代 JavaScript 语法
- **Canvas API**: 实现动态背景和网格动画
- **WebGL**: 实现流体粒子效果（可选）

### 构建工具
- **Gulp**: 自动化构建工具
- **Babel**: JavaScript 编译器，将 ES6+ 转换为 ES5
- **Uglify**: JavaScript 压缩工具
- **Clean-css**: CSS 压缩工具
- **Htmlmin**: HTML 压缩工具
- **Autoprefixer**: 自动添加浏览器前缀

### 第三方库
- **anime.js**: 动画库，用于页面动画效果
- **font.min.css**: 外部字体库

## 项目结构

```
HomePage/
├── src/                    # 源代码目录
│   ├── components/         # Pug 组件目录
│   │   ├── head.pug       # 头部组件
│   │   ├── intro.pug      # 介绍区域组件
│   │   ├── main.pug       # 主卡片组件
│   │   └── scripts.pug    # 脚本引入组件
│   ├── css/               # 样式文件目录
│   │   ├── common/        # 通用样式
│   │   │   ├── variable.less   # 变量定义
│   │   │   ├── common.less     # 通用样式
│   │   │   └── icon.less       # 图标样式
│   │   ├── layout/        # 布局样式
│   │   │   └── layout.less     # 布局样式
│   │   ├── intro/         # 介绍区域样式
│   │   │   └── intro.less      # 介绍区域样式
│   │   ├── main/          # 主卡片样式
│   │   │   └── main.less       # 主卡片样式
│   │   └── style.less     # 主样式文件
│   ├── js/                # JavaScript 文件目录
│   │   ├── main.js        # 网格动画脚本
│   │   └── background.js  # 流体动画脚本
│   ├── assets/            # 静态资源目录
│   │   └── avatar.jpg     # 头像图片
│   └── index.pug          # 主页面模板
├── dist/                   # 构建输出目录
│   ├── css/               # 编译后的 CSS
│   ├── js/                # 编译后的 JavaScript
│   ├── assets/            # 复制的静态资源
│   └── index.html         # 编译后的 HTML
├── Wiki/                   # 文档目录
│   ├── package.json.md
│   ├── gulpfile.js.md
│   ├── config.json.md
│   └── src/               # 源代码文档
├── package.json            # 项目配置文件
├── gulpfile.js            # 构建脚本
├── config.json            # 项目配置
└── favicon.ico            # 网站图标
```

## 核心功能

### 1. 首页介绍区域
- **主标题**: 显示用户名称，带有动态阴影效果
- **副标题**: 显示个性签名，带有逐字显示动画
- **进入按钮**: 带有闪光效果，点击后滚动到主卡片区域
- **箭头指示**: 两个箭头带有下落动画，引导用户向下滚动
- **GitHub 角标**: 可选的 GitHub 链接角标
- **背景动画**: 可选的流体粒子背景动画

### 2. 主卡片区域
- **用户头像**: 圆形头像，带有白色边框和阴影效果
- **用户名**: 显示用户名称
- **个性签名**: 显示个性签名
- **导航链接**: Blog、About、Email、Github 四个导航链接
- **网格背景**: 动态网格背景动画

### 3. 动画效果
- **白色阴影动画**: 主标题的动态阴影效果
- **闪光动画**: 进入按钮的闪光效果
- **箭头移动动画**: 箭头的下落动画
- **字母发光动画**: 副标题字母的逐个显示动画
- **网格动画**: 主卡片的网格背景动画
- **流体动画**: 首页的流体粒子动画（可选）

### 4. 响应式设计
- **移动设备适配**: 小屏幕设备自动调整字体大小和布局
- **视口单位**: 使用 vh、vw 等视口单位实现响应式布局
- **Flexbox 布局**: 使用 Flexbox 实现灵活的布局
- **媒体查询**: 使用媒体查询适配不同屏幕尺寸

## 配置说明

### config.json 配置文件
```json
{
  "head": {
    "title": "SMILe_Xio",
    "description": "Author:SMILe_Xio,Category:Personal Blog",
    "favicon": "favicon.ico"
  },
  "intro": {
    "title": "SMILe_Xio",
    "subtitle": "做个可爱的人，不烦世事，满心欢喜❤",
    "enter": "enter",
    "supportAuthor": true,
    "background": true
  },
  "main": {
    "name": "SMILe_Xio",
    "signature": "Code & Input & Output",
    "avatar": {
      "link": "assets/avatar.jpg",
      "height": "100",
      "width": "100"
    },
    "ul": {
      "first": { "href": "blog/", "icon": "bokeyuan", "text": "Blog" },
      "second": { "href": "about/", "icon": "xiaolian", "text": "About" },
      "third": { "href": "mailto:hi@simonaking.com", "icon": "email", "text": "Email" },
      "fourth": { "href": "https://github.com/SimonAKing", "icon": "github", "text": "Github" }
    }
  }
}
```

### 主要配置项说明
- **head.title**: 网页标题
- **head.description**: 网页描述，用于 SEO
- **head.favicon**: 网站图标
- **intro.title**: 主标题
- **intro.subtitle**: 副标题
- **intro.enter**: 进入按钮文字
- **intro.supportAuthor**: 是否显示 GitHub 角标
- **intro.background**: 是否启用背景动画
- **main.name**: 用户名
- **main.signature**: 个性签名
- **main.avatar**: 头像配置
- **main.ul**: 导航链接配置

## 构建流程

### 开发模式
```bash
npm run dev
```
1. 执行 predev 脚本（gulp build）
2. 启动开发服务器（端口 3000）
3. 监听文件变化，自动重新构建
4. 支持热重载

### 生产构建
```bash
npm run build
```
1. 清理构建输出目录
2. 复制静态资源
3. 编译 Pug 模板
4. 编译 LESS 样式
5. 编译 JavaScript
6. 优化 HTML

## 开发指南

### 环境要求
- Node.js >= 10.x
- npm >= 6.x

### 安装依赖
```bash
npm install
```

### 启动开发服务器
```bash
npm run dev
```
访问 http://localhost:3000

### 构建生产版本
```bash
npm run build
```

### 修改配置
编辑 config.json 文件，修改后重新运行构建命令。

### 添加自定义样式
在 src/css/ 目录下创建或修改 LESS 文件。

### 添加自定义脚本
在 src/js/ 目录下创建或修改 JavaScript 文件。

## 性能优化

### 构建优化
- **代码压缩**: 使用 Uglify 压缩 JavaScript
- **样式压缩**: 使用 Clean-css 压缩 CSS
- **HTML 优化**: 使用 Htmlmin 优化 HTML
- **浏览器前缀**: 使用 Autoprefixer 自动添加浏览器前缀

### 运行时优化
- **will-change**: 使用 will-change 属性优化滚动性能
- **requestAnimationFrame**: 使用 requestAnimationFrame 实现流畅动画
- **CSS 变量**: 使用 CSS 变量减少重复计算
- **CDN 加速**: 使用 CDN 加载第三方库

## 浏览器兼容性

### 支持的浏览器
- Chrome >= 60
- Firefox >= 60
- Safari >= 12
- Edge >= 79
- iOS Safari >= 12
- Android Chrome >= 60

### 兼容性处理
- **Babel**: 将 ES6+ 转换为 ES5
- **Autoprefixer**: 自动添加浏览器前缀
- **html5shiv**: 让 IE8 及以下支持 HTML5 标签
- **respond.js**: 让 IE8 及以下支持 CSS3 媒体查询

## 注意事项

1. **端口配置**: 开发服务器使用端口 3000，确保端口未被占用
2. **CDN 依赖**: 项目依赖外部 CDN，确保网络连接正常
3. **图片资源**: 头像图片需放置在 src/assets 目录
4. **配置修改**: 修改配置后需重新运行构建命令
5. **性能考虑**: 流体动画配置参数会影响性能，低端设备可能需要降低分辨率
6. **浏览器兼容**: 旧版浏览器可能不支持所有特性
7. **字符编码**: 确保文件使用 UTF-8 编码保存

## 相关文档

- [package.json 文档](./package.json.md)
- [gulpfile.js 文档](./gulpfile.js.md)
- [config.json 文档](./config.json.md)
- [src/index.pug 文档](./src/index.pug.md)
- [src/js/main.js 文档](./src/js/main.js.md)
- [src/js/background.js 文档](./src/js/background.js.md)
- [src/components/head.pug 文档](./src/components/head.pug.md)
- [src/components/intro.pug 文档](./src/components/intro.pug.md)
- [src/components/main.pug 文档](./src/components/main.pug.md)
- [src/components/scripts.pug 文档](./src/components/scripts.pug.md)
- [src/css/style.less 文档](./src/css/style.less.md)
- [src/css/common/variable.less 文档](./src/css/common/variable.less.md)
- [src/css/common/common.less 文档](./src/css/common/common.less.md)
- [src/css/layout/layout.less 文档](./src/css/layout/layout.less.md)
- [src/css/intro/intro.less 文档](./src/css/intro/intro.less.md)
- [src/css/main/main.less 文档](./src/css/main/main.less.md)

## 许可证
LGPI-3.0

## 作者
SimonAKing <hi@simonaking.com>

## 项目主页
http://simonaking.com

## 代码仓库
https://github.com/SimonAKing/HomePage
