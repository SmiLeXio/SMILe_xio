# config.json

## 文件用途
项目的核心配置文件，定义了网站的元数据、页面内容、导航链接等可配置信息，供 Pug 模板渲染时使用。

## 核心功能
1. **网站元数据配置**：定义网站标题、描述、图标等基本信息
2. **页面内容配置**：配置首页介绍、主卡片等内容
3. **导航链接配置**：定义 Blog、About、Email、Github 等链接
4. **功能开关**：控制背景动画、作者支持等功能的开启与关闭

## 关键实现逻辑

### head 配置
定义网站头部信息
```json
{
  "head": {
    "title": "SMILe_Xio",
    "description": "Author:SMILe_Xio,Category:Personal Blog",
    "favicon": "favicon.ico"
  }
}
```
- **title**: 网页标题，显示在浏览器标签页
- **description**: 网页描述，用于 SEO 和搜索引擎索引
- **favicon**: 网站图标文件路径

### intro 配置
定义首页介绍区域内容
```json
{
  "intro": {
    "title": "SMILe_Xio",
    "subtitle": "做个可爱的人，不烦世事，满心欢喜❤",
    "enter": "enter",
    "supportAuthor": true,
    "background": true
  }
}
```
- **title**: 主标题，显示在首页中央的大标题
- **subtitle**: 副标题，显示在主标题下方的个性签名
- **enter**: 进入按钮文字，点击后滚动到主卡片区域
- **supportAuthor**: 是否显示 GitHub 角标链接，true 显示右上角 GitHub 图标
- **background**: 是否启用背景动画，true 时加载 background.js 实现流体动画

### main 配置
定义主卡片区域内容
```json
{
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
- **name**: 用户名，显示在头像下方
- **signature**: 个性签名，显示在用户名下方
- **avatar**: 头像配置
  - **link**: 头像图片路径
  - **height**: 头像高度（像素）
  - **width**: 头像宽度（像素）
- **ul**: 导航链接列表，包含四个链接项
  - **first**: Blog 链接，使用 bokeyuan 图标
  - **second**: About 链接，使用 xiaolian 图标
  - **third**: Email 链接，使用 email 图标
  - **fourth**: Github 链接，使用 github 图标

## 重要注意事项
1. **图片路径**：头像路径使用相对路径 assets/avatar.jpg，需确保图片文件存在于 src/assets 目录
2. **图标类名**：导航链接的 icon 属性对应 CSS 中的图标类名，需与 icon.less 中定义的图标一致
3. **功能开关**：supportAuthor 和 background 为布尔值，控制功能的开启与关闭
4. **邮箱地址**：Email 链接使用 mailto: 协议，点击可直接打开邮件客户端
5. **外部链接**：Github 链接使用 https 协议，会在新标签页打开
6. **字符编码**：副标题中的 ❤ 等特殊字符需确保文件使用 UTF-8 编码保存
7. **配置修改**：修改配置后需重新运行构建命令（gulp build 或 npm run dev）才能生效

## 相关文件
- gulpfile.js - 使用此配置文件渲染 Pug 模板
- src/index.pug - 使用此配置的主页面模板
- src/components/intro.pug - 使用此配置的介绍区域模板
- src/components/main.pug - 使用此配置的主卡片模板
- src/assets/avatar.jpg - 头像图片文件
- src/js/background.js - 背景动画脚本（当 background 为 true 时加载）
