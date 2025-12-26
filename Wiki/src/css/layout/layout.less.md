# src/css/layout/layout.less

## 文件用途
布局样式文件，定义页面布局、容器结构和网格背景的样式。

## 核心功能
1. **主容器布局**：定义 main 元素的布局
2. **内容区域布局**：定义介绍区域和主卡片区域的布局
3. **包装器布局**：定义内容包装器的布局
4. **网格背景布局**：定义网格背景的定位

## 关键实现逻辑

### 主容器布局
```less
main {
  height: 100vh;
  width: 100%;
  overflow: hidden;
  position: relative;
}
```
- **height**: 设置高度为 100vh，占满视口高度
- **width**: 设置宽度为 100%，占满视口宽度
- **overflow**: 设置为 hidden，隐藏溢出内容
- **position**: 设置为 relative，为绝对定位子元素提供参考

### 内容区域布局
```less
.content {
  width: 100%;
  height: 100vh;
  position: relative;
  background: transparent;

  &-intro {
    z-index: 100;
    height: 200vh;
  }

  &-main {
    position: fixed;
    top: 0;
    left: 0;
    background: #060606;
  }

  &-inner {
    width: 100%;
    height: 100vh;
    position: relative;
  }
}
```

#### .content
- **width/height**: 设置为 100% 和 100vh，占满视口
- **position**: 设置为 relative，为绝对定位子元素提供参考
- **background**: 设置为 transparent，透明背景

#### .content-intro
- **z-index**: 设置为 100，确保在其他内容之上
- **height**: 设置为 200vh，为滚动效果提供空间

#### .content-main
- **position**: 设置为 fixed，固定定位
- **top/left**: 设置为 0，固定在左上角
- **background**: 设置为 #060606，深色背景

#### .content-inner
- **width/height**: 设置为 100% 和 100vh，占满视口
- **position**: 设置为 relative，为绝对定位子元素提供参考

### 包装器布局
```less
.wrap {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}
```
- **width/height**: 设置为 100% 和 100vh，占满视口
- **display**: 设置为 flex，启用 Flexbox 布局
- **flex-wrap**: 设置为 wrap，允许换行
- **flex-direction**: 设置为 column，垂直排列
- **align-items**: 设置为 center，水平居中
- **justify-content**: 设置为 center，垂直居中
- **text-align**: 设置为 center，文本居中

### 网格背景布局
```less
.grid-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
```
- **position**: 设置为 absolute，绝对定位
- **top/left**: 设置为 0，定位到左上角
- **width/height**: 设置为 100%，占满父容器
- **z-index**: 设置为 1，确保在内容下方

## 重要注意事项
1. **视口单位**：使用 vh 单位确保布局适应视口高度
2. **固定定位**：.content-main 使用 fixed 定位，滚动时保持固定
3. **Flexbox 布局**：.wrap 使用 Flexbox 实现内容居中
4. **层级管理**：使用 z-index 管理元素层级
5. **溢出隐藏**：main 使用 overflow hidden 隐藏溢出内容
6. **透明背景**：.content 使用透明背景，允许背景动画显示
7. **响应式设计**：布局使用百分比和视口单位，适应不同屏幕尺寸

## 相关文件
- src/css/style.less - 主样式文件（导入此文件）
- src/css/intro/intro.less - 介绍区域样式文件（使用 .content-intro）
- src/css/main/main.less - 主卡片样式文件（使用 .content-main）
- src/components/intro.pug - 介绍区域模板（使用 .wrap）
- src/components/main.pug - 主卡片模板（使用 .grid-background）
