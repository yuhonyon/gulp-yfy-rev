## gulp-yfy-rev

gulp 插件--添加hash

## Installation

```bash
yarn add gulp-yfy-rev --dev
```

## Usage

```js
var gulp = require('gulp');
var yfyRev = require('gulp-yfy-rev');

gulp.task('rev',function() {
    gulp.src("./test/demo.html")
        .pipe(yfyRev())
        .pipe(gulp.dest('./'));
});
```

## Options

### hashLen: hash长度
Type: `Number` default: 7

### tail: hash位置是否在最后
Type: `Blooean` default: false

### verConnecter: 连接符
Type: `String` default: '-'

### rootPath: root目录（绝对路径）
Type: `String` default: ""

### verStr: 自定义版本号 
Type: `String` 

## Example

```js
var gulp = require('gulp');
var yfyRev = require('./index.js');

gulp.task('rev',['revCss'],function() {
    gulp.src("./test/demo.html")
        .pipe(yfyRev())
        .pipe(gulp.dest('./dest'));
});

gulp.task('revCss',function () {
    return gulp.src('./test/styles/demo.css')
        .pipe(yfyRev())
        .pipe(gulp.dest('./dest/styles/'))
});
gulp.task('default',['rev']);
```

### before: test.css
```css
body{background:url('../images/bg.png')}
```

### after: test.css
```css
body{background:url("../images/bg_2769acd.png"}
```
### before: test.html
```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test.css" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test.png" />
    </div>
    <script src="./scripts/test.js" type="text/javascript"></script>
</body>
</html>
```
### after: test.html

```html
<html lang="en">
<head>
    <meta charset="utf-8"/>
    <title></title>
    <link rel="stylesheet" href="./styles/test_0ede2cf.css" type="text/css" />
</head>
<body>
    <div>
        <img src="./images/test_25cf2b4.png" />
    </div>
    <script src="./scripts/test_8ced4e6.js" type="text/javascript"></script>
</body>
</html>
```



