# gulpfile.js

## 文件用途
项目的构建配置文件，使用 Gulp 自动化构建工具定义项目的构建流程、任务和开发服务器配置。

## 核心功能
1. **文件编译与转换**：将 LESS、Pug、ES6+ 等源文件编译为浏览器可识别的 CSS、HTML、JavaScript
2. **代码优化**：压缩、清理、添加浏览器前缀等优化操作
3. **开发服务器**：提供本地开发服务器和热重载功能
4. **文件监听**：监听源文件变化并自动重新构建

## 关键实现逻辑

### 依赖引入
```javascript
const gulp = require('gulp')
const minifycss = require('gulp-clean-css')
const uglify = require('gulp-uglify')
const htmlmin = require('gulp-htmlmin')
const cssnano = require('gulp-cssnano')
const htmlclean = require('gulp-htmlclean')
const del = require('del')
const babel = require('gulp-babel')
const autoprefixer = require('gulp-autoprefixer')
const connect = require('gulp-connect')
const pug = require('gulp-pug')
const less = require('gulp-less')
const config = require('./config.json')
```

### 任务定义

#### clean 任务
清理构建输出目录中的 CSS 和 JavaScript 文件
```javascript
gulp.task('clean', function () {
	return del(['./dist/css/', './dist/js/'])
})
```

#### css 任务
处理 LESS 文件并转换为压缩的 CSS
1. 读取 src/css/*.less 文件
2. 使用 LESS 编译器转换为 CSS
3. 使用 clean-css 压缩 CSS（兼容 IE8）
4. 添加浏览器前缀（支持最近 2 个版本）
5. 使用 cssnano 进一步优化
6. 输出到 dist/css 目录

```javascript
gulp.task('css', function () {
	return gulp
		.src('./src/css/*.less')
		.pipe(less().on('error', function (err) {
			console.log(err);
			this.emit('end');
		}))
		.pipe(minifycss({ compatibility: 'ie8' }))
		.pipe(autoprefixer({ overrideBrowserslist: ['last 2 version'] }))
		.pipe(cssnano({ reduceIdents: false }))
		.pipe(gulp.dest('./dist/css'))
})
```

#### js 任务
处理 JavaScript 文件并转换为压缩的 ES5 代码
1. 读取 src/js/*.js 文件
2. 使用 Babel 转换 ES6+ 代码为 ES5
3. 使用 Uglify 压缩 JavaScript
4. 输出到 dist/js 目录

```javascript
gulp.task('js', function () {
	return gulp
		.src('./src/js/*.js')
		.pipe(babel({ presets: ['@babel/preset-env'] }))
		.pipe(uglify())
		.pipe(gulp.dest('./dist/js'))
})
```

#### pug 任务
编译 Pug 模板为 HTML
1. 读取 src/index.pug 文件
2. 使用 config.json 中的数据渲染模板
3. 输出到 dist 目录

```javascript
gulp.task('pug', function () {
	return gulp
		.src('./src/index.pug')
		.pipe(pug({ data: config }))
		.pipe(gulp.dest('./dist'))
})
```

#### html 任务
优化 HTML 文件
1. 读取 dist/index.html 文件
2. 使用 htmlclean 清理 HTML
3. 使用 htmlmin 压缩 HTML
4. 输出到 dist 目录

```javascript
gulp.task('html', function () {
	return gulp
		.src('./dist/index.html')
		.pipe(htmlclean())
		.pipe(htmlmin())
		.pipe(gulp.dest('./dist'))
})
```

#### assets 任务
复制静态资源文件
1. 读取 src/assets/**/* 文件
2. 复制到 dist/assets 目录

```javascript
gulp.task('assets', function () {
	return gulp
		.src(['./src/assets/**/*'])
		.pipe(gulp.dest('./dist/assets'));
})
```

#### build 任务
完整构建流程，按顺序执行：clean → assets → pug → css → js → html

```javascript
gulp.task('build', gulp.series('clean', 'assets', 'pug', 'css', 'js', 'html'))
```

#### watch 任务
开发模式，监听文件变化并启动开发服务器
1. 监听 src/components/*.pug 和 src/index.pug，变化时执行 pug 任务
2. 监听 src/css/**/*.scss，变化时执行 css 任务
3. 监听 src/js/*.js，变化时执行 js 任务
4. 启动开发服务器（端口 3000，支持热重载）

```javascript
gulp.task('watch', function () {
	gulp.watch('./src/components/*.pug', gulp.parallel('pug'))
	gulp.watch('./src/index.pug', gulp.parallel('pug'))
	gulp.watch('./src/css/**/*.scss', gulp.parallel(['css']))
	gulp.watch('./src/js/*.js', gulp.parallel(['js']))
	connect.server({
		root: 'dist',
		livereload: true,
		port: 3000
	})
})
```

## 重要注意事项
1. **端口配置**：开发服务器使用端口 3000，确保端口未被占用
2. **错误处理**：LESS 编译错误会打印到控制台但不会中断构建流程
3. **构建顺序**：build 任务严格按照 clean → assets → pug → css → js → html 的顺序执行
4. **文件监听**：watch 任务中的 scss 监听路径可能是笔误，实际项目使用的是 less 文件
5. **热重载**：开发服务器支持 livereload，文件变化后自动刷新浏览器
6. **浏览器兼容性**：CSS 添加了最近 2 个版本的浏览器前缀，JavaScript 转换为 ES5 以支持旧浏览器
7. **配置数据**：Pug 模板使用 config.json 中的数据进行渲染

## 相关文件
- config.json - Pug 模板渲染的数据源
- src/index.pug - 主页面模板
- src/css/*.less - 样式源文件
- src/js/*.js - JavaScript 源文件
- src/components/*.pug - 组件模板文件
- src/assets/**/* - 静态资源文件
- package.json - 依赖包定义
