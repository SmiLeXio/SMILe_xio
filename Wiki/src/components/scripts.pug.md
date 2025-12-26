# src/components/scripts.pug

## 文件用途
脚本引入组件，负责加载页面所需的所有 JavaScript 文件和配置，包括第三方库、自定义脚本和配置参数。

## 核心功能
1. **第三方库引入**：引入 anime.js 动画库
2. **全局配置**：定义流体动画的配置参数
3. **工具函数**：提供全局工具函数
4. **脚本加载**：根据配置条件加载自定义脚本
5. **日志记录**：可选的访问日志记录

## 关键实现逻辑

### anime.js 引入
```pug
script(src="https://cdn.jsdelivr.net/npm/animejs@3.2.1/lib/anime.min.js")
```
- **CDN 地址**: 使用 jsDelivr CDN 加载 anime.js
- **版本**: 3.2.1
- **用途**: 用于页面动画效果

### 工具函数
```javascript
script.
  window.$ = selector => document.querySelector(selector)
  const getOriginalContent = selector => $(selector).getAttribute("original-content")
  window.subtitle = getOriginalContent(".content-subtitle")
  window.signature = getOriginalContent("#signature")
```
- **window.$**: 简化的选择器函数，等同于 document.querySelector
- **getOriginalContent**: 获取元素的 original-content 属性值
- **window.subtitle**: 存储副标题的原始内容
- **window.signature**: 存储个性签名的原始内容

### 流体动画配置
```javascript
script.
  window.config = {
    SIM_RESOLUTION: 128,
    DYE_RESOLUTION: 1024,
    CAPTURE_RESOLUTION: 512,
    DENSITY_DISSIPATION: 1,
    VELOCITY_DISSIPATION: 0.2,
    PRESSURE: 0.8,
    PRESSURE_ITERATIONS: 20,
    CURL: 30,
    SPLAT_RADIUS: 0.25,
    SPLAT_FORCE: 6000,
    SHADING: true,
    COLORFUL: true,
    COLOR_UPDATE_SPEED: 10,
    PAUSED: false,
    BACK_COLOR: { r: 30, g: 31, b: 33 },
    TRANSPARENT: false,
    BLOOM: true,
    BLOOM_ITERATIONS: 8,
    BLOOM_RESOLUTION: 256,
    BLOOM_INTENSITY: 0.4,
    BLOOM_THRESHOLD: 0.8,
    BLOOM_SOFT_KNEE: 0.7,
    SUNRAYS: true,
    SUNRAYS_RESOLUTION: 196,
    SUNRAYS_WEIGHT: 1.0,
  }
```
- **window.config**: 全局配置对象，供 background.js 使用
- **配置项**: 包含模拟、交互、视觉效果、背景、辉光、光线等参数

### 自定义脚本加载
```pug
script(src='js/main.js')

if intro.background
  script(src='js/background.js')
```
- **main.js**: 始终加载，实现网格动画
- **background.js**: 条件加载，当 intro.background 为 true 时加载

### 日志记录
```pug
if intro.supportAuthor
  script(src="https://cdn.jsdelivr.net/gh/SimonAKing/js/log.min.js")
```
- **条件加载**: 当 intro.supportAuthor 为 true 时加载
- **用途**: 记录访问日志

## 重要注意事项
1. **CDN 依赖**: anime.js 和 log.min.js 依赖外部 CDN，确保网络连接正常
2. **配置对象**: window.config 对象必须在 background.js 加载前定义
3. **条件加载**: background.js 和 log.min.js 根据配置条件加载
4. **全局变量**: window.$、window.subtitle、window.signature 为全局变量，避免命名冲突
5. **脚本顺序**: 脚本加载顺序很重要，确保依赖关系正确
6. **配置修改**: 可通过修改 window.config 对象调整动画效果
7. **性能考虑**: 流体动画配置参数会影响性能，低端设备可能需要降低分辨率

## 相关文件
- src/js/main.js - 网格动画脚本
- src/js/background.js - 流体动画脚本（条件加载）
- config.json - 提供 intro.background、intro.supportAuthor 等配置
- src/index.pug - 主页面模板（引入此组件）
