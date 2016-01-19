# Express 4

## 自动生成Express项目

1. npm install express-generator -g     安装自动生成项目工具（已安装过可跳过）
2. 执行 express myapp     会在当前目录下创建一个叫myapp的项目

##### 知识点：

* express4与3做了部分改动，在app.js中我们找不到配置端口和项目启动的代码，项目启动命令也由 node app.js 改为 npm start . 启动由node交给了npm管理， 如何修改配置呢？ 答案在package.json中

``` 
{
  "name": "babel",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "start": "node ./bin/www",
    "build": "babel public/src -d public/dist"
  },
  "dependencies": {
    "express": "~4.9.0",
    "body-parser": "~1.8.1",
    "cookie-parser": "~1.3.3",
    "morgan": "~1.3.0",
    "serve-favicon": "~2.1.3",
    "debug": "~2.0.0",
    "jade": "~1.6.0",
    "babel-cli": "^6.0.0"
  }
}
```

‘ scripts ’配置下的start ,node启动了bin下的www文件，在www文件中我们可以找到服务的启动和配置代码

* ​