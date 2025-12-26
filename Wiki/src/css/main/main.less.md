# src/css/main/main.less

## 文件用途
主卡片样式文件，定义主卡片区域的样式，包括卡片容器、头像、用户名、个性签名和导航链接。

## 核心功能
1. **卡片容器样式**：定义主卡片的布局和样式
2. **头部样式**：定义头像、用户名和个性签名的样式
3. **导航链接样式**：定义导航链接的布局和样式
4. **响应式设计**：适配不同屏幕尺寸

## 关键实现逻辑

### 卡片容器样式
```less
#card {
  position: relative;
  width: 100vw;
  height: 100vh;
  color: #93979e;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  transition: width ease 0.5s, height ease 0.5s;

  .card-inner {
    padding: 0;
    border: 0;
    width: 100%;
    max-width: 700px;

    @media screen and (max-width: 540px) {
      header {
        h1 {
          font-size: 1rem !important;
        }

        h2 {
          font-size: 0.8rem !important;
        }
      }

      ul {
        li {
          font-size: 0.8rem !important;
        }
      }
    }
  }
}
```

#### #card
- **position**: 设置为 relative，相对定位
- **width/height**: 设置为 100vw 和 100vh，占满视口
- **color**: 设置为 #93979e，灰色文本
- **display**: 设置为 flex，启用 Flexbox 布局
- **justify-content**: 设置为 center，水平居中
- **align-items**: 设置为 center，垂直居中
- **text-align**: 设置为 center，文本居中
- **transition**: 设置宽度和高度的过渡效果

#### .card-inner
- **padding/border**: 设置为 0，移除内边距和边框
- **width**: 设置为 100%，占满父容器
- **max-width**: 设置为 700px，限制最大宽度
- **@media**: 响应式设计，小屏幕调整字体大小

### 头部样式
```less
header {
  margin-bottom: 40px;

  img {
    border: 3px solid #fff;
    border-radius: 50%;
    box-shadow: 0 0 1px 1px rgba(0, 0, 0, 0.3);
    transition: 0.4s ease-in-out;
    z-index: 2;
    position: relative;
  }

  h1 {
    margin: 15px 15px 0px;
    color: #fff;
    font-size: 2rem;
    line-height: 1.2em;
    font-weight: 300;
    z-index: 2;
    position: relative;
  }

  h2 {
    color: #ccc;
    letter-spacing: 3px;
    font-size: 0.8rem;
    font-weight: lighter;
    z-index: 2;
    position: relative;
  }
}
```
- **header**: 头部容器
  - **margin-bottom**: 设置为 40px，底部间距
- **img**: 头像图片
  - **border**: 设置为 3px solid #fff，白色边框
  - **border-radius**: 设置为 50%，圆形
  - **box-shadow**: 添加阴影效果
  - **transition**: 设置过渡效果
  - **z-index**: 设置为 2，确保在上层
  - **position**: 设置为 relative，相对定位
- **h1**: 用户名
  - **margin**: 设置上下左右边距
  - **color**: 设置为 #fff，白色
  - **font-size**: 设置为 2rem
  - **line-height**: 设置为 1.2em
  - **font-weight**: 设置为 300，细字体
  - **z-index**: 设置为 2，确保在上层
  - **position**: 设置为 relative，相对定位
- **h2**: 个性签名
  - **color**: 设置为 #ccc，浅灰色
  - **letter-spacing**: 设置为 3px，增加字间距
  - **font-size**: 设置为 0.8rem
  - **font-weight**: 设置为 lighter，更细字体
  - **z-index**: 设置为 2，确保在上层
  - **position**: 设置为 relative，相对定位

### 导航链接样式
```less
ul {
  position: relative;
  margin: 0;
  list-style-type: none;
  display: inline-flex;
  width: 100%;
  justify-content: space-around;
  padding-bottom: 40px;

  li {
    z-index: 2;
    position: relative;
    display: inline-block;
    transition: all 0.2s;
    width: 100%;
    height: 100%;

    a {
      color: #b6b6b6;
      transition: all 0.2s;

      &:hover {
        color: #f6f6f6;
        text-shadow: 0 0 2px #f6f6f6;
      }
    }
  }
}
```
- **ul**: 无序列表容器
  - **position**: 设置为 relative，相对定位
  - **margin**: 设置为 0，移除默认边距
  - **list-style-type**: 设置为 none，移除列表样式
  - **display**: 设置为 inline-flex，内联 Flexbox
  - **width**: 设置为 100%，占满父容器
  - **justify-content**: 设置为 space-around，均匀分布
  - **padding-bottom**: 设置为 40px，底部内边距
- **li**: 列表项
  - **z-index**: 设置为 2，确保在上层
  - **position**: 设置为 relative，相对定位
  - **display**: 设置为 inline-block，内联块级元素
  - **transition**: 设置过渡效果
  - **width/height**: 设置为 100%，占满父容器
- **a**: 链接元素
  - **color**: 设置为 #b6b6b6，浅灰色
  - **transition**: 设置过渡效果
  - **&:hover**: 悬停状态
    - **color**: 设置为 #f6f6f6，浅白色
    - **text-shadow**: 添加文字阴影

## 重要注意事项
1. **Flexbox 布局**：使用 Flexbox 实现内容居中和均匀分布
2. **圆形头像**：使用 border-radius: 50% 创建圆形头像
3. **响应式设计**：使用媒体查询适配小屏幕设备
4. **过渡效果**：使用 transition 实现平滑的过渡效果
5. **层级管理**：使用 z-index 管理元素层级
6. **阴影效果**：使用 box-shadow 添加阴影效果
7. **悬停效果**：使用 :hover 伪类实现悬停效果

## 相关文件
- src/css/style.less - 主样式文件（导入此文件）
- src/css/layout/layout.less - 布局样式文件（定义 .content-main）
- src/components/main.pug - 主卡片模板
- src/css/common/icon.less - 图标样式文件（定义图标样式）
