# src/js/background.js

## 文件用途
页面背景动画脚本，实现流体粒子效果和交互式背景动画，使用 WebGL 或 Canvas 技术创建动态视觉体验。

## 核心功能
1. **流体粒子效果**：创建流动的粒子动画效果
2. **交互式背景**：响应鼠标移动等用户交互
3. **视觉特效**：实现辉光、光晕等视觉特效
4. **性能优化**：使用高效的渲染算法

## 关键实现逻辑

### 配置参数
```javascript
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

### 配置参数说明

#### 模拟参数
- **SIM_RESOLUTION**: 128 - 模拟分辨率，影响粒子数量和性能
- **DYE_RESOLUTION**: 1024 - 染色分辨率，影响颜色渲染质量
- **CAPTURE_RESOLUTION**: 512 - 捕获分辨率，用于交互效果
- **DENSITY_DISSIPATION**: 1 - 密度消散速度
- **VELOCITY_DISSIPATION**: 0.2 - 速度消散速度
- **PRESSURE**: 0.8 - 压力参数，影响流体行为
- **PRESSURE_ITERATIONS**: 20 - 压力迭代次数，影响流体模拟精度
- **CURL**: 30 - 旋度参数，影响流体旋转效果

#### 交互参数
- **SPLAT_RADIUS**: 0.25 - 飞溅半径，鼠标交互的影响范围
- **SPLAT_FORCE**: 6000 - 飞溅力度，鼠标交互的强度

#### 视觉效果参数
- **SHADING**: true - 是否启用着色效果
- **COLORFUL**: true - 是否启用彩色效果
- **COLOR_UPDATE_SPEED**: 10 - 颜色更新速度
- **PAUSED**: false - 是否暂停动画

#### 背景参数
- **BACK_COLOR**: { r: 30, g: 31, b: 33 } - 背景颜色（RGB）
- **TRANSPARENT**: false - 是否透明背景

#### 辉光效果参数
- **BLOOM**: true - 是否启用辉光效果
- **BLOOM_ITERATIONS**: 8 - 辉光迭代次数
- **BLOOM_RESOLUTION**: 256 - 辉光分辨率
- **BLOOM_INTENSITY**: 0.4 - 辉光强度
- **BLOOM_THRESHOLD**: 0.8 - 辉光阈值
- **BLOOM_SOFT_KNEE**: 0.7 - 辉光柔和度

#### 光线效果参数
- **SUNRAYS**: true - 是否启用光线效果
- **SUNRAYS_RESOLUTION**: 196 - 光线分辨率
- **SUNRAYS_WEIGHT**: 1.0 - 光线权重

### 初始化逻辑
```javascript
// Canvas 初始化
const canvas = document.getElementById('background');
// WebGL context setup
// Shader compilation
// Buffer setup
// Animation loop start
```

### 渲染循环
```javascript
function render() {
  if (!config.PAUSED) {
    // Update simulation
    // Render dye
    // Apply bloom
    // Apply sunrays
    // Render to screen
  }
  requestAnimationFrame(render);
}
```

### 交互处理
```javascript
// Mouse move events
// Touch events
// Splat particles on interaction
```

## 重要注意事项
1. **性能考虑**：高分辨率设置会增加 GPU 负载，低端设备可能需要降低分辨率
2. **浏览器兼容性**：需要支持 WebGL 的现代浏览器
3. **配置调整**：可通过修改 window.config 对象调整动画效果
4. **内存使用**：WebGL 纹理会占用较多显存，注意内存管理
5. **移动设备**：移动设备上可能需要降低分辨率以保证性能
6. **透明背景**：TRANSPARENT 设置为 true 时会影响性能
7. **效果叠加**：BLOOM 和 SUNRAYS 效果叠加会增加渲染负担

## 相关文件
- src/index.pug - 主页面模板
- src/components/intro.pug - 介绍区域组件（包含 background canvas）
- src/components/scripts.pug - 脚本引入组件（根据 config.background 条件加载）
- config.json - 配置文件（控制是否加载此脚本）
