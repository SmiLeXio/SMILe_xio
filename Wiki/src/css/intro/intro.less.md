# src/css/intro/intro.less

## 文件用途
介绍区域样式文件，定义首页介绍区域的样式，包括标题、副标题、进入按钮、箭头、形状装饰和背景动画。

## 核心功能
1. **内容容器样式**：定义介绍区域的内容容器样式
2. **标题样式**：定义主标题和副标题的样式和动画
3. **进入按钮样式**：定义进入按钮的样式和动画
4. **箭头动画**：定义箭头的样式和下落动画
5. **形状装饰**：定义 SVG 形状的样式
6. **背景动画**：定义背景 Canvas 的样式

## 关键实现逻辑

### 内容容器样式
```less
.content-intro .content-inner {
  background: transparent;
  user-select: none;
}
```
- **background**: 设置为 transparent，透明背景
- **user-select**: 设置为 none，禁止选择文本

### 形状装饰样式
```less
.shape {
  height: 100vh;
  width: 100%;
  display: block;
  background: transparent;
  &-wrap {
    position: relative;
    z-index: 0;
    margin: -5px 0 0 0;
    will-change: scroll-position;
    background: transparent;
  }
  path {
    fill: #151515;
  }
}
```
- **.shape**: SVG 形状容器
  - **height/width**: 设置为 100vh 和 100%，占满视口
  - **display**: 设置为 block，块级元素
  - **background**: 设置为 transparent，透明背景
- **.shape-wrap**: 形状包装器
  - **position**: 设置为 relative，相对定位
  - **z-index**: 设置为 0，底层
  - **margin**: 设置为 -5px 0 0 0，调整位置
  - **will-change**: 设置为 scroll-position，优化滚动性能
- **path**: SVG 路径
  - **fill**: 设置为 #151515，深色填充

### 主标题样式
```less
.content-title {
  font-family: "Comic Sans MS", "Helvetica Neue", "Microsoft Yahei",
    -apple-system, sans-serif;
  font-size: 4.7rem;
  font-weight: 200;
  color: @color-title;
  line-height: 1;
  margin-top: 0.8em;
  margin-bottom: 0.3em;
  animation: whiteShadow 1.5s ease-in-out infinite alternate;
  text-shadow: rgb(69, 45, 45) 0 0 1px, rgb(255, 255, 251) 0 0 1px,
    rgb(255, 255, 251) 0 0 2px;
  @media screen and (max-width: 50em) {
    font-size: 2rem;
  }
}
```
- **font-family**: 设置字体族
- **font-size**: 设置为 4.7rem，大标题
- **font-weight**: 设置为 200，细字体
- **color**: 使用变量 @color-title
- **line-height**: 设置为 1，紧凑行高
- **margin**: 设置上下边距
- **animation**: 应用 whiteShadow 动画
- **text-shadow**: 添加文字阴影效果
- **@media**: 响应式设计，小屏幕字体缩小

### 白色阴影动画
```less
@keyframes whiteShadow {
  from {
    text-shadow: 0 0 1px #fff, 0 0 2px #fff, 0 0 3px #fff, 0 0 5px #333,
      0 0 8px #333, 0 0 9px #333, 0 0 10px #333, 0 0 15px #333;
  }
  to {
    text-shadow: 0 0 0.5px #fff, 0 0 1px #fff, 0 0 1.5px #fff, 0 0 2px #333,
      0 0 4px #333, 0 0 5px #333, 0 0 6px #333, 0 0 8px #333;
  }
}
```
- **from/to**: 定义动画开始和结束状态
- **text-shadow**: 动态改变文字阴影，创建闪烁效果

### 副标题样式
```less
.content-subtitle {
  color: #fff;
  font-family: "Comic Sans MS", "Helvetica Neue", "Microsoft Yahei",
    -apple-system, sans-serif;
  font-size: 1.2rem;
  font-weight: 200;
  margin-bottom: 2em;
  text-shadow: 0 0 4px #ffffff;

  @media screen and (max-width: 1024px) {
    font-size: 1rem;
  }
}
```
- **color**: 设置为 #fff，白色
- **font-family**: 设置字体族
- **font-size**: 设置为 1.2rem
- **font-weight**: 设置为 200，细字体
- **margin-bottom**: 设置为 2em
- **text-shadow**: 添加文字阴影
- **@media**: 响应式设计，小屏幕字体缩小

### 进入按钮样式
```less
.enter {
  color: @color-enter;
  font-size: 0.8rem;
  letter-spacing: 3px;
  white-space: pre;
  pointer-events: auto;
  transition: all 0.4s;
  z-index: 999;
  position: relative;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.7), transparent);
  background-size: 200% 100%;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: shimmer 2s linear infinite;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  &:hover,
  &:focus {
    color: @color-link-hover;
  }
}
```
- **color**: 使用变量 @color-enter
- **font-size**: 设置为 0.8rem
- **letter-spacing**: 设置为 3px，增加字间距
- **white-space**: 设置为 pre，保留空格
- **pointer-events**: 设置为 auto，允许点击
- **transition**: 设置过渡效果
- **z-index**: 设置为 999，确保在最上层
- **background**: 使用渐变背景
- **background-clip**: 设置为 text，背景裁剪为文字
- **-webkit-text-fill-color**: 设置为 transparent，透明文字
- **animation**: 应用 shimmer 动画
- **text-shadow**: 添加文字阴影
- **&:hover/focus**: 悬停和焦点状态

### 闪光动画
```less
@keyframes shimmer {
  0% {
    background-position: 200% center;
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  }
  50% {
    text-shadow: 0 0 20px rgba(255, 255, 255, 0.6);
  }
  100% {
    background-position: -200% center;
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  }
}
```
- **0%/50%/100%**: 定义动画三个关键帧
- **background-position**: 移动渐变背景位置
- **text-shadow**: 动态改变文字阴影

### 箭头样式
```less
.arrow {
  position: absolute;
  left: 49.5%;
  top: 95%;
  transform-origin: 50% 50%;
  transform: translate3d(-50%, 0%, 0);
  &-1 {
    animation: arrow-movement 2s ease-in-out infinite;
  }
  &-2 {
    animation: arrow-movement 2s 1s ease-in-out infinite;
  }
  &:before,
  &:after {
    background: #fff;
    content: "";
    display: block;
    height: 3px;
    position: absolute;
    top: 0;
    left: 0;
    width: 13px;
    box-shadow: 1px 1px 20px 0px #fff;
  }
  &:before {
    transform: rotate(45deg) translateX(-10%);
    transform-origin: top left;
  }
  &:after {
    transform: rotate(-45deg) translateX(10%);
    transform-origin: top right;
  }
}
```
- **position**: 设置为 absolute，绝对定位
- **left/top**: 设置位置
- **transform-origin**: 设置变换原点
- **transform**: 设置变换
- **&-1/&-2**: 两个箭头，有不同的动画延迟
- **&:before/&:after**: 使用伪元素创建箭头形状
- **box-shadow**: 添加阴影效果

### 箭头移动动画
```less
@keyframes arrow-movement {
  0% {
    opacity: 0;
    top: 92%;
  }
  70% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
```
- **0%/70%/100%**: 定义动画三个关键帧
- **opacity**: 动态改变透明度
- **top**: 动态改变垂直位置

### 字母发光动画
```less
.content-subtitle span {
  animation: letter-glow 0.7s 0s ease both;
}

@keyframes letter-glow {
  0% {
    opacity: 0;
    text-shadow: 0 0 1px rgba(255, 255, 255, 0.1);
  }
  66% {
    opacity: 1;
    text-shadow: 0 0 20px rgba(255, 255, 255, 0.9);
  }
  77% {
    opacity: 1;
  }
  100% {
    opacity: 0.7;
    text-shadow: 0 0 20px rgba(255, 255, 255, 0.2);
  }
}
```
- **span**: 副标题中的每个字母
- **animation**: 应用 letter-glow 动画
- **@keyframes**: 定义动画关键帧

### 字母动画延迟
```less
@signatureLength: 38;
.generate-delays(@n, @i: 1) when (@i =< @n) {
  .content-subtitle span:nth-child(@{i}) {
    animation-delay: 0.05s * @i;
  }
  .generate-delays(@n, (@i + 1));
}
.generate-delays(@signatureLength);
```
- **@signatureLength**: 定义字母数量
- **.generate-delays**: 递归生成动画延迟
- **nth-child**: 为每个字母设置不同的动画延迟

### 背景动画样式
```less
#background {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: -1;
}
```
- **position**: 设置为 absolute，绝对定位
- **width/height**: 设置为 100%，占满父容器
- **z-index**: 设置为 -1，在底层

## 重要注意事项
1. **动画性能**：使用 will-change 优化滚动性能
2. **响应式设计**：使用媒体查询适配不同屏幕尺寸
3. **动画延迟**：使用递归生成动画延迟，实现字母逐个显示
4. **文字效果**：使用 text-shadow 和渐变背景创建视觉效果
5. **浏览器兼容性**：包含 Webkit 前缀，确保跨浏览器兼容
6. **变量使用**：使用 LESS 变量统一管理颜色
7. **动画循环**：使用 infinite 实现无限循环动画

## 相关文件
- src/css/style.less - 主样式文件（导入此文件）
- src/css/common/variable.less - 变量定义文件（定义 @color-title、@color-enter 等变量）
- src/components/intro.pug - 介绍区域模板
- src/js/background.js - 背景动画脚本
