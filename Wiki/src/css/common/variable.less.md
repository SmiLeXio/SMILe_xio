# src/css/common/variable.less

## 文件用途
变量定义文件，定义 LESS 变量和 CSS 自定义属性，用于统一管理颜色、字体等样式常量。

## 核心功能
1. **LESS 变量**：定义 LESS 预处理器变量
2. **CSS 变量**：定义 CSS 自定义属性（CSS Variables）
3. **动画类**：定义通用的淡入动画类

## 关键实现逻辑

### LESS 变量
```less
@color-link: #5f5f5f;
@color-link-hover: #5f5f5f;
@color-enter: #fff;
@color-title: #fff;
@color-content: #222325;
@font-alt: 200 6vw/1 'Comic Sans MS', 'Helvetica Neue', 'Microsoft Yahei',
  'Microsoft Yahei', -apple-system, sans-serif;
```

#### 颜色变量
- **@color-link**: 链接颜色（#5f5f5f）
- **@color-link-hover**: 链接悬停颜色（#5f5f5f）
- **@color-enter**: 进入按钮颜色（#fff）
- **@color-title**: 标题颜色（#fff）
- **@color-content**: 内容背景色（#222325）

#### 字体变量
- **@font-alt**: 备用字体
  - 字重: 200
  - 字号: 6vw（视口宽度的 6%）
  - 行高: 1
  - 字体族: Comic Sans MS, Helvetica Neue, Microsoft Yahei, -apple-system, sans-serif

### CSS 自定义属性
```less
:root {
  --color-link: @color-link;
  --color-link-hover: @color-link-hover;
  --color-enter: @color-enter;
  --color-title: @color-title;
  --color-content: @color-content;
  --font-alt: @font-alt;
}
```
- **:root**: 定义全局 CSS 变量
- **变量映射**: 将 LESS 变量映射到 CSS 变量
- **用途**: 支持动态修改样式，便于 JavaScript 操作

### 淡入动画类
```less
.fade {
  opacity: 0;
  transition: all 1s;
  transform: translateY(200px);
  &.in {
    opacity: 1;
    transform: none;
  }
}
```
- **.fade**: 淡入动画类
  - 初始状态: 透明度为 0，向下偏移 200px
  - 过渡: 1 秒
  - 激活状态: 透明度为 1，无偏移
- **&.in**: 激活状态（当元素添加 in 类时触发动画）

## 重要注意事项
1. **变量命名**：使用 @ 前缀表示 LESS 变量，使用 -- 前缀表示 CSS 变量
2. **颜色一致性**：链接颜色和悬停颜色相同，可根据需要修改
3. **字体兼容性**：字体族包含多种字体，确保跨平台兼容性
4. **响应式字体**：@font-alt 使用视口单位（vw），实现响应式字体大小
5. **CSS 变量**：CSS 变量可以在 JavaScript 中动态修改，实现主题切换等功能
6. **动画类**：.fade 类需要在 JavaScript 中添加 .in 类来触发动画
7. **浏览器兼容性**：CSS 变量在现代浏览器中支持良好，旧版浏览器可能需要 polyfill

## 相关文件
- src/css/style.less - 主样式文件（导入此文件）
- src/css/common/common.less - 通用样式文件（使用这些变量）
- src/css/intro/intro.less - 介绍区域样式文件（使用这些变量）
- src/css/main/main.less - 主卡片样式文件（使用这些变量）
