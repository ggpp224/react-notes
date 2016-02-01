# webpack

#### #  在项目根目录中添加package.json

``` json
"devDependencies": {
  "webpack": "1.12.11"
}
```

#### #  执行 npm install

#### 编译目标js文件

进入项目根目录执行

``` 
$ webpack ./entry.js bundle.js
```

./entry.js 为目标文件路径， bundle.js为编译后输出文件路径

#### # 编译css

在package.json中添加依赖：

``` json
"devDependencies": {
  "webpack": "1.12.11",
 + "css-loader": "0.23.1",
 + "style-loader": "0.13.0"
}
```

entry.js中添加：

`require("!style!css!./style.css");`

或者：

`require("./style.css");`

执行: `webpack ./entry.js bundle.js --module-bind 'css=style!css'`

#### # 配置文件

``` 
module.exports = {
    entry: './public/javascripts/entry.js',
    output: {
        path: __dirname,
        filename: './public/dist/bundle.js'
    },

    module: {
        loaders:[
            {
                test: /\.css$/,
                loader: 'style!css'
            }
        ]
    }
}
```

只需要执行 `webpack` 即可

还可以`webpack --progress --colors —watch` 当文件有改动时自动编译



#### # 开发服务器

在package.json中添加依赖，并执行npm install

``` 
"devDependencies": {
  "babel-preset-es2015": "^6.3.13",
  "webpack": "1.12.11",
  "webpack-dev-server": "^1.14.1",
  "css-loader": "0.23.1",
  "style-loader": "0.13.0"
}
```

``` 
webpack-dev-server --progress --colors
```

提供了一个小型的express 的静态资源和自动打包服务(自动编译): localhost:8080，当一个bundle重新编译时它能够自动更新浏览器页面（通过SockJS） 

> dev server 使用webpack的观察模式。 他不会将文件提交到磁盘，而是将文件保存在内存中提供服务。