# src/js/main.js

## 文件用途
页面的核心 JavaScript 文件，实现网格动画效果和页面交互功能，使用 Canvas API 绘制动态网格背景。

## 核心功能
1. **网格动画系统**：实现可配置的网格背景动画效果
2. **Canvas 绘制**：使用 HTML5 Canvas API 绘制网格线条
3. **动画控制**：支持方向、速度、颜色等参数配置
4. **响应式设计**：自动适应窗口大小变化
5. **交互效果**：支持鼠标悬停等交互效果

## 关键实现逻辑

### GridAnimation 类
```javascript
class GridAnimation {
  constructor(canvas, options = {}) {
    this.canvas = canvas;
    this.ctx = canvas.getContext("2d");
    this.options = {
      direction: options.direction || "right",
      speed: options.speed || 1,
      borderColor: options.borderColor || "rgba(255, 255, 255, 0.05)",
      squareSize: options.squareSize || 40,
      // Additional configuration options...
    };
    // Initialization code...
  }
}
```
- **构造函数**：接收 Canvas 元素和配置选项
- **配置选项**：
  - direction: 动画方向（right/left/up/down）
  - speed: 动画速度
  - borderColor: 网格线条颜色
  - squareSize: 网格单元大小

### 初始化方法
```javascript
init() {
  this.resizeCanvas();
  this.setupEventListeners();
  this.animate();
  // Additional initialization...
}
```
- **resizeCanvas()**: 调整 Canvas 尺寸以适应窗口
- **setupEventListeners()**: 设置事件监听器
- **animate()**: 启动动画循环

### Canvas 尺寸调整
```javascript
resizeCanvas() {
  this.canvas.width = window.innerWidth;
  this.canvas.height = window.innerHeight;
}
```
- 将 Canvas 尺寸设置为窗口大小
- 确保动画覆盖整个视口

### 事件监听设置
```javascript
setupEventListeners() {
  window.addEventListener('resize', () => this.resizeCanvas());
  // Additional event listeners...
}
```
- 监听窗口大小变化事件
- 窗口调整时重新设置 Canvas 尺寸

### 动画循环
```javascript
animate() {
  this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
  this.drawGrid();
  this.updateAnimation();
  requestAnimationFrame(() => this.animate());
}
```
- **clearRect()**: 清除上一帧的绘制内容
- **drawGrid()**: 绘制网格
- **updateAnimation()**: 更新动画状态
- **requestAnimationFrame()**: 请求下一帧动画

### 网格绘制
```javascript
drawGrid() {
  // Implementation details for drawing grid lines
}
```
- 根据配置的 squareSize 绘制网格线条
- 使用配置的 borderColor 设置线条颜色
- 支持不同的绘制方向

### 动画更新
```javascript
updateAnimation() {
  // Implementation details for updating animation state
}
```
- 根据配置的 speed 更新动画状态
- 支持不同的动画方向
- 实现平滑的动画效果

## 重要注意事项
1. **性能优化**：使用 requestAnimationFrame 实现流畅动画，避免使用 setInterval
2. **内存管理**：及时清除 Canvas 内容，避免内存泄漏
3. **响应式设计**：监听窗口大小变化，确保动画始终覆盖整个视口
4. **配置灵活性**：通过构造函数参数支持多种配置选项
5. **浏览器兼容性**：使用标准 Canvas API，确保主流浏览器兼容
6. **动画性能**：避免在动画循环中进行复杂的计算，保持高帧率
7. **颜色格式**：支持 RGBA 格式的颜色值，实现透明效果

## 相关文件
- src/index.pug - 主页面模板
- src/components/scripts.pug - 脚本引入组件
- src/css/main/main.less - 主卡片样式文件
- config.json - 配置文件（可能包含动画相关配置）
