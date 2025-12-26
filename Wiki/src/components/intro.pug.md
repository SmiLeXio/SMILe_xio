# src/components/intro.pug

## 文件用途
首页介绍区域组件，显示用户的主标题、副标题、进入按钮，以及可选的 GitHub 角标和背景动画效果。

## 核心功能
1. **标题展示**：显示用户主标题和个性签名
2. **导航入口**：提供进入主卡片的按钮和箭头指示
3. **GitHub 角标**：可选的 GitHub 链接角标
4. **背景动画**：可选的 Canvas 背景动画
5. **SVG 形状**：底部的波浪形状装饰

## 关键实现逻辑

### 容器结构
```pug
.content.content-intro
  .content-inner
    // 内容区域
  .shape-wrap
    // 形状装饰
```
- **.content-intro**: 介绍区域容器
- **.content-inner**: 内容内部容器
- **.shape-wrap**: 形状装饰容器

### GitHub 角标
```pug
if intro.supportAuthor
  a(href="https://github.com/SimonAKing/HomePage" class="github-corner" aria-label="View source on GitHub" target="_blank" rel="noopener noreferrer")
    svg(width="80" height="80" viewBox="0 0 250 250" style=`fill:${intro.background? 'transparent': '#222325'}; color:#fff; position: absolute; top: 0; border: 0; right: 0;` aria-hidden="true")
      path(d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z")
      path(d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm")
      path(d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body")
  style.
    .github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}
```
- **条件渲染**: 仅当 intro.supportAuthor 为 true 时显示
- **SVG 图标**: GitHub 章鱼猫图标
- **悬停动画**: 鼠标悬停时章鱼手臂摆动
- **响应式**: 移动设备上自动播放动画

### 背景动画 Canvas
```pug
if intro.background
  canvas#background
```
- **条件渲染**: 仅当 intro.background 为 true 时创建
- **Canvas ID**: background，用于 background.js 操作

### 主要内容
```pug
.wrap.fade
  h2.content-title #{intro.title}
  h3.content-subtitle(original-content=`${intro.subtitle}`) &nbsp;
  a.enter #{intro.enter}
  .arrow.arrow-1
  .arrow.arrow-2
```
- **.wrap.fade**: 内容容器，带有淡入动画
- **h2.content-title**: 主标题，显示 intro.title
- **h3.content-subtitle**: 副标题，显示 intro.subtitle
- **a.enter**: 进入按钮，点击后滚动到主卡片
- **.arrow**: 两个箭头，带有下落动画

### SVG 形状装饰
```pug
.shape-wrap
  svg.shape(width="100%" height="100vh" preserveAspectRatio="none" viewBox="0 0 1440 800" xmlns:pathdata="http://www.codrops.com/")
    path( d="M -44,-50 C -52.71,28.52 15.86,8.186 184,14.69 383.3,22.39 462.5,12.58 638,14 835.5,15.6 987,6.4 1194,13.86 1661,30.68 1652,-36.74 1582,-140.1 1512,-243.5 15.88,-589.5 -44,-50 Z" pathdata:id="M -44,-50 C -137.1,117.4 67.86,445.5 236,452 435.3,459.7 500.5,242.6 676,244 873.5,245.6 957,522.4 1154,594 1593,753.7 1793,226.3 1582,-126 1371,-478.3 219.8,-524.2 -44,-50 Z")
```
- **SVG 形状**: 波浪形状，分隔介绍区域和主卡片区域
- **pathdata 属性**: 用于滚动动画的路径数据
- **preserveAspectRatio**: 保持形状比例

## 重要注意事项
1. **GitHub 链接**: GitHub 链接硬编码为 SimonAKing/HomePage，如需修改请更新 href 属性
2. **背景动画**: 背景动画需要 background.js 支持，确保脚本正确加载
3. **副标题**: 副标题使用 original-content 属性存储原始文本，用于 JavaScript 处理
4. **箭头动画**: 两个箭头有不同的动画延迟，创建连续下落效果
5. **形状动画**: SVG 形状使用 pathdata 属性实现滚动变形效果
6. **响应式设计**: GitHub 角标在移动设备上有特殊的动画行为
7. **无障碍性**: GitHub 链接包含 aria-label 属性，提高可访问性

## 相关文件
- config.json - 提供 intro.title、intro.subtitle、intro.enter、intro.supportAuthor、intro.background 等数据
- src/js/background.js - 背景动画脚本（当 intro.background 为 true 时加载）
- src/css/intro/intro.less - 介绍区域样式文件
- src/index.pug - 主页面模板（引入此组件）
