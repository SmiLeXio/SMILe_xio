# package.json

## 文件用途
项目的配置文件，定义了项目的基本信息、依赖包、脚本命令等元数据。

## 核心功能
1. **项目信息定义**：包含项目名称、版本、作者、许可证、主页、仓库地址等基本信息
2. **依赖管理**：定义项目所需的开发依赖包及其版本
3. **脚本命令**：提供开发、构建等常用命令的快捷方式

## 关键实现逻辑

### 项目基本信息
- **name**: simonaking-homepage - 项目名称
- **version**: 1.0.0 - 当前版本号
- **author**: SimonAKing <hi@simonaking.com> - 作者信息
- **license**: LGPI-3.0 - 开源许可证类型
- **homepage**: http://simonaking.com - 项目主页地址
- **repository**: https://github.com/SimonAKing/HomePage - 代码仓库地址
- **bugs**: https://github.com/SimonAKing/HomePage/issues - 问题反馈地址
- **description**: SimonAKing-homepage - 项目描述

### 脚本命令
项目定义了三个主要脚本命令：
- **predev**: 在运行 dev 命令前执行 gulp build，确保构建最新代码
- **dev**: 运行 gulp watch 启动开发服务器并监听文件变化
- **build**: 运行 gulp build 执行完整构建流程

### 开发依赖
项目使用以下主要依赖包：
- **构建工具**: gulp@4.0.2 - 自动化构建工具
- **模板引擎**: gulp-pug@4.0.1 - Pug 模板编译
- **样式处理**: gulp-less@5.0.0 - LESS 预处理器
- **代码压缩**: 
  - gulp-clean-css@4.2.0 - CSS 压缩
  - gulp-uglify@3.0.2 - JavaScript 压缩
  - gulp-htmlmin@5.0.1 - HTML 压缩
  - gulp-minify@3.1.0 - 代码最小化
- **代码转换**: 
  - @babel/core@7.4.4 - Babel 核心
  - @babel/preset-env@7.4.4 - Babel 环境预设
  - gulp-babel@8.0.0 - Gulp Babel 插件
- **开发服务器**: gulp-connect@5.7.0 - 本地开发服务器
- **其他工具**:
  - del@4.1.1 - 文件删除工具
  - gulp-autoprefixer@6.1.0 - CSS 自动添加浏览器前缀
  - gulp-htmlclean@2.7.22 - HTML 清理

## 重要注意事项
1. **依赖版本锁定**：所有依赖包都指定了具体版本号，确保构建环境的一致性
2. **开发依赖**：所有依赖都是 devDependencies，仅用于开发阶段
3. **脚本执行顺序**：predev 脚本会在 dev 前自动执行，确保代码已构建
4. **许可证**：使用 LGPI-3.0 许可证，需注意开源协议的合规性
5. **作者信息**：包含联系邮箱 hi@simonaking.com，可用于项目咨询

## 相关文件
- gulpfile.js - 构建脚本实现
- config.json - 项目配置文件
- package-lock.json - 依赖版本锁定文件（如存在）
