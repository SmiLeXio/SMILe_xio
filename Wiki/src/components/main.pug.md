# src/components/main.pug

## 文件用途
主卡片区域组件，显示用户头像、姓名、个性签名和导航链接，以及网格背景动画效果。

## 核心功能
1. **用户信息展示**：显示头像、姓名、个性签名
2. **导航链接**：提供 Blog、About、Email、Github 四个导航链接
3. **网格背景**：显示动态网格背景动画
4. **响应式设计**：适配不同屏幕尺寸

## 关键实现逻辑

### 容器结构
```pug
.content.content-main
  #card
    .card-inner.fade
      header
        // 头像和用户信息
      ul
        // 导航链接
  canvas.grid-background#gridCanvas
```
- **.content-main**: 主卡片区域容器
- **#card**: 卡片容器
- **.card-inner**: 卡片内部容器，带有淡入动画
- **canvas.grid-background**: 网格背景 Canvas

### 头像和用户信息
```pug
header
  img(src=`${main.avatar.link}` width=`${main.avatar.width}` height=`${main.avatar.height}` alt="avatar")
  h1(data-translate="name") #{main.name}
  h2#signature(data-translate="signature") #{main.signature}
```
- **img**: 用户头像
  - src: 从 config.json 的 main.avatar.link 获取
  - width/height: 从 config.json 的 main.avatar 获取
  - alt: 备用文本
- **h1**: 用户名，从 config.json 的 main.name 获取
- **h2**: 个性签名，从 config.json 的 main.signature 获取
- **data-translate**: 用于国际化翻译的属性

### 导航链接
```pug
- const { first , second , third, fourth } = main.ul
ul
  li
    a(href=`${first.href}` aria-label=`${first.text}`)
      i(class=`icon icon-${first.icon}`)
      span(data-translate=`${first.text}`) #{first.text}
  li
    a(href=`${second.href}` aria-label=`${second.text}`)
      i(class=`icon icon-${second.icon}`)
      span(data-translate=`${second.text}`) #{second.text}
  li
    a(href=`${third.href}` aria-label=`${third.text}` target="_blank")
      i(class=`icon icon-${third.icon}`)
      span(data-translate=`${third.text}`) #{third.text}
  li
    a(href=`${fourth.href}` aria-label=`${fourth.text}` target="_blank")
      i(class=`icon icon-${fourth.icon}`)
      span(data-translate=`${fourth.text}`) #{fourth.text}
```
- **解构赋值**: 从 main.ul 中提取四个链接配置
- **ul**: 无序列表容器
- **li**: 列表项，每个对应一个导航链接
- **a**: 链接元素
  - href: 链接地址
  - aria-label: 无障碍标签
  - target="_blank": Email 和 Github 链接在新标签页打开
- **i**: 图标元素，使用 icon 和 icon-{icon} 类名
- **span**: 链接文本
- **data-translate**: 用于国际化翻译的属性

### 网格背景
```pug
canvas.grid-background#gridCanvas
```
- **Canvas ID**: gridCanvas，用于 main.js 操作
- **类名**: grid-background，用于样式定位

## 重要注意事项
1. **头像路径**: 头像路径使用相对路径，需确保图片文件存在于 src/assets 目录
2. **图标类名**: 图标类名必须与 icon.less 中定义的图标一致
3. **外部链接**: Email 和 Github 链接使用 target="_blank" 在新标签页打开
4. **无障碍性**: 所有链接都包含 aria-label 属性，提高可访问性
5. **国际化**: data-translate 属性预留了国际化支持，可用于多语言切换
6. **Canvas 动画**: 网格背景需要 main.js 支持，确保脚本正确加载
7. **响应式**: 样式文件中包含移动设备的适配样式

## 相关文件
- config.json - 提供 main.name、main.signature、main.avatar、main.ul 等数据
- src/js/main.js - 网格背景动画脚本
- src/css/main/main.less - 主卡片样式文件
- src/css/common/icon.less - 图标样式文件
- src/index.pug - 主页面模板（引入此组件）
