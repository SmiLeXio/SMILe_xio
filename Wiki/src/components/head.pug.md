# src/components/head.pug

## 文件用途
页面头部组件，定义 HTML 文档的 meta 标签、样式表引用、图标等头部信息，确保页面在搜索引擎和社交媒体上正确显示。

## 核心功能
1. **页面元数据**：定义标题、描述、字符集等基本元数据
2. **视口配置**：配置移动设备视口，确保响应式布局
3. **样式表引入**：引入外部字体和项目样式表
4. **性能优化**：配置 DNS 预取和资源预加载
5. **兼容性处理**：为旧版浏览器提供兼容性支持

## 关键实现逻辑

### 基本元数据
```pug
title #{head.title}

meta(charset="utf-8")
meta(name="viewport" content="width=device-width,initial-scale=1,maximum-scale=2")
meta(http-equiv="X-UA-Compatible" content="IE=edge,chrome=1")
meta(name="renderer" content="webkit")
```
- **title**: 页面标题，从 config.json 的 head.title 获取
- **charset**: 字符编码设置为 UTF-8
- **viewport**: 配置移动设备视口，初始缩放为 1，最大缩放为 2
- **X-UA-Compatible**: 指定 IE 使用最新渲染模式
- **renderer**: 指定使用 Webkit 内核渲染（针对双核浏览器）

### 主题颜色
```pug
meta(name="theme-color" content="#222325")
meta(name="apple-mobile-web-app-status-bar-style" content="#222325")
meta(name="msapplication-navbutton-color" content="#222325")
```
- **theme-color**: 浏览器地址栏主题颜色（Chrome/Edge）
- **apple-mobile-web-app-status-bar-style**: iOS 状态栏样式
- **msapplication-navbutton-color**: Windows Phone 导航栏颜色

### 样式表引入
```pug
link(rel="stylesheet" href="https://cdn.jsdelivr.net/gh/SimonAKing/font/font.min.css" )
link(rel="stylesheet" href='css/style.css' )
```
- **font.min.css**: 引入外部字体库（CDN）
- **style.css**: 引入项目主样式表（编译后的 CSS）

### 性能优化
```pug
meta(http-equiv="x-dns-prefetch-control" content="on")
link(rel="dns-prefetch" href="https://cdn.jsdelivr.net")
link(rel="prefetch" href="https://cdn.jsdelivr.net/")
```
- **x-dns-prefetch-control**: 启用 DNS 预取
- **dns-prefetch**: 预解析 CDN 域名
- **prefetch**: 预加载 CDN 资源

### SEO 和图标
```pug
meta(name="description" content=`${head.description}`)
link(rel="icon" href=`${head.favicon}` type="image/x-icon")
link(rel="shortcut icon" href=`${head.favicon}` type="image/x-icon")
```
- **description**: 页面描述，用于 SEO
- **icon**: 网站图标（现代浏览器）
- **shortcut icon**: 网站图标（旧版浏览器）

### IE 兼容性处理
```pug
<!--[if lt IE 9]>
  style.
    .alert { padding: 15px; margin-bottom: 20px; border: 1px solid transparent; border-radius: 4px } .alert-danger { background-color: #f2dede; border-color: #ebccd1; color: #a94442; border-bottom: 1px solid #ebccd1 } .alert-link { color: #843534; font-weight: bold } .topframe { margin: 0; padding-left: 15px; padding-right: 15px; text-align: center; border-radius: 0; position: fixed; left: 0; right: 0; top: 0; z-index: 1000 }

  .alert.alert-danger.topframe
    !='你的浏览器实在<strong>太太太太太太旧了</strong>，放学别走，升级完浏览器再说'
    a.alert-link(target="_blank" href="http://browsehappy.com") 立即升级

  script(src="https://cdn.bootcss.com/html5shiv/r29/html5.min.js")
  script(src="https://cdn.bootcss.com/respond.js/1.4.2/respond.min.js")
<![endif]-->
```
- **条件注释**: 仅在 IE9 及以下版本加载
- **警告提示**: 显示浏览器升级提示
- **html5shiv**: 让 IE8 及以下支持 HTML5 标签
- **respond.js**: 让 IE8 及以下支持 CSS3 媒体查询

## 重要注意事项
1. **CDN 依赖**：字体库依赖外部 CDN，确保网络连接正常
2. **主题颜色**：主题颜色应与页面背景色保持一致
3. **视口配置**：maximum-scale 设置为 2 允许用户放大页面
4. **IE 兼容性**：IE 兼容性代码仅在旧版浏览器加载，不影响现代浏览器
5. **SEO 优化**：description 标签对搜索引擎优化很重要，应包含关键词
6. **图标格式**：favicon 使用 x-icon 格式，确保浏览器兼容性
7. **字符编码**：必须使用 UTF-8 编码，否则中文等字符会显示异常

## 相关文件
- config.json - 提供 head.title、head.description、head.favicon 等数据
- src/css/style.less - 主样式源文件
- dist/css/style.css - 编译后的样式文件
- src/index.pug - 主页面模板（引入此组件）
