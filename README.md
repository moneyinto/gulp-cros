# gulp-cros
Dealing with Cross domain problem！

```js
var gulp = require('gulp');
var connect = require('gulp-connect');
var proxy = require('http-proxy-middleware');

gulp.task('serve', function () {
    connect.server({
        root: ['src'],  // root 目录
        livereload: true,
        port: 8000,
        middleware: function (connect, opt) {
            return [
                proxy('/api/', { // 匹配路由
                    target: 'http://xxx.xxx.com',   // 目标代理路径
                    pathRewrite: {'/api/' : '/'}, // 重新路由
                    changeOrigin: true
                })
            ]
        }
    });
})

gulp.task('default', ['serve'], function () {
    
});
```
