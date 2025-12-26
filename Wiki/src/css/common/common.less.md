# src/css/common/common.less

## 文件用途
通用样式文件，定义全局样式重置、基础样式和通用样式规则。

## 核心功能
1. **样式重置**：重置浏览器默认样式
2. **基础样式**：定义 HTML 和 body 的基础样式
3. **通用样式**：定义链接、图片等通用元素的样式
4. **自定义光标**：定义自定义光标样式

## 关键实现逻辑

### 盒模型重置
```less
* {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  -webkit-text-size-adjust: none;
}
```
- **box-sizing**: 使用 border-box 盒模型，包含 padding 和 border 在元素尺寸内
- **-webkit-text-size-adjust**: 禁用 iOS 设备的文本大小自动调整

### HTML 样式
```less
html {
  font-size: 20px !important;
}
```
- **font-size**: 设置根元素字体大小为 20px，使用 !important 确保优先级
- **用途**: 作为 rem 单位的基础

### HTML 和 Body 样式
```less
html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
  border: 0;
}
```
- **height**: 设置高度为 100%，确保页面占满视口
- **margin/padding/border**: 重置为 0，移除默认间距

### Body 样式
```less
body {
  font-family: 'Comic Sans MS', 'Helvetica Neue', 'Microsoft Yahei',
    -apple-system, sans-serif !important;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  min-height: 100vh;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-touch-callout: none;
}
```
- **font-family**: 设置字体族，使用 !important 确保优先级
- **align-items/justify-content**: 使用 Flexbox 居中对齐内容
- **min-height**: 设置最小高度为 100vh，确保内容至少占满视口
- **-webkit-font-smoothing**: 启用字体抗锯齿（Webkit）
- **-moz-osx-font-smoothing**: 启用字体抗锯齿（Firefox）
- **-webkit-touch-callout**: 禁用 iOS 长按菜单

### 列表样式重置
```less
ul {
  margin: 0;
  padding: 0;
}
```
- **margin/padding**: 重置为 0，移除默认间距

### 图片样式
```less
img {
  border: 0;
  vertical-align: middle;
}
```
- **border**: 移除边框
- **vertical-align**: 垂直居中对齐

### 自定义光标
```less
body {
  cursor: url('https://cdn.jsdelivr.net/gh/SimonAKing/images/blog/default.cur'),
    auto !important;
}

img,
a {
  cursor: url('https://cdn.jsdelivr.net/gh/SimonAKing/images/blog/pointer.cur'),
    auto !important;
}
```
- **body**: 默认光标使用自定义 default.cur
- **img/a**: 图片和链接使用自定义 pointer.cur
- **CDN**: 光标文件从 CDN 加载
- **!important**: 确保自定义光标优先级

### 链接样式
```less
a {
  text-decoration: none;
  color: var(--color-link);
  outline: none;
}
```
- **text-decoration**: 移除下划线
- **color**: 使用 CSS 变量 --color-link
- **outline**: 移除焦点轮廓

## 重要注意事项
1. **字体优先级**：字体族使用 !important 确保不被覆盖
2. **盒模型**：使用 border-box 确保元素尺寸计算一致
3. **自定义光标**：依赖外部 CDN，确保网络连接正常
4. **字体抗锯齿**：启用字体抗锯齿提高文字显示质量
5. **Flexbox 居中**：使用 Flexbox 实现内容居中
6. **CSS 变量**：链接颜色使用 CSS 变量，便于动态修改
7. **浏览器兼容性**：包含 Webkit 和 Mozilla 前缀，确保跨浏览器兼容

## 相关文件
- src/css/style.less - 主样式文件（导入此文件）
- src/css/common/variable.less - 变量定义文件（定义 --color-link 变量）
