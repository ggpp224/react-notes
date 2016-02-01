# PostCSS - preCSS

> precss 是postcss的预处理插件， 功能类似于less、sass. 其语法也与scss最为接近。

## 配置插件

### webPack

1 . 在package.json下的devDependencies中配置：

``` json
"postcss-import": "^7.0.0",
"postcss-simple-vars": "^1.0.0",
"precss": "^1.4.0",
```

2 . webpack.config.js的postcss项配置：

``` javascript
postcss: function () {
    return [
        require('postcss-import')({ // Import all the css files...
            glob: true,
            onImport: function (files) {
                files.forEach(this.addDependency); // ...and add dependecies from the main.css files to the other css files...
            }.bind(this) // ...so they get hot–reloaded when something changes...
        }),
        require('precss')
    ];
}
```

3 . npm install 添加依赖包

4 . 启动服务

## 使用说明

### 变量

使用 $作为声明

``` scss
$light-grey: #EDEDED;
background-color: $light-grey;
```

编译后生成：

`background-color: #EDEDED;`

### 嵌套

``` 
.customer-list{
    padding: 20px;

    li{
        padding: 15px;
    }
}
```

编译后：

``` scss
.customer-list {
    padding: 20px;
}
.customer-list li {
    padding: 15px;
}
```

### 函数声明

@define-mixin 函数名 参数, 参数, ….｛｝

``` scss

@define-mixin icon $network, $color {

    .button.$(network) { 

      	 background-image: url('img/$(network).png');

         background-color: $color;

 }}

```

编译后

``` scss

.button.twitter {
    background-image: url('img/twitter.png');
    background-color: blue;
    width: 3rem;
}

.button.youtube {
    background-image: url('img/youtube.png');
    background-color: red;
    width: 4rem;
}

```



### 继承

> 定义一个可重复使用的代码块

@define-extend 名称 { }

``` scss
@define-extend rounded_button {
    border-radius: 0.5rem;
    padding: 1em;
    border-width: 0.0625rem;
    border-style: solid;
}

.blue_button {
    @extend rounded_button;
    border-color: #2F74D1;
    background-color: #3B8EFF;
}

.red_button {
    @extend rounded_button;
    border-color: #C41A1E;
    background-color: #FF2025;
}

```

编译后

``` scss
.blue_button,
.red_button {
    border-radius: 0.5rem;
    padding: 1em;
    border-width: 0.0625rem;
    border-style: solid;
}

.blue_button {
    border-color: #2F74D1;
    background-color: #3B8EFF;
}

.red_button {
    border-color: #C41A1E;
    background-color: #FF2025;
}
```

### imports

推荐使用 postcss-import 可以引入整个文件夹，而且可以配置热更新。

``` 
@charset "UTF-8";

@import "_variables.css";

@import "_helper.css";

@import "_base.css";

@import "components/*.css";

@import "pages/*.css";
```



### 其它

条件判断和遍历在开发中很少使用，为节省时间暂不描述，以后补上。有兴趣的可以参考https://github.com/jonathantneal/precss

### webstorm 编写preCss

webstorm中有自带的.less, .sass, .scss文件编辑器，但搜不到专门的precss的插件， 因为precss与scss的语法最为接近，可以将 .css与scss文件类型关联起来。

1. Preferences -> Editor -> File Types -> Cascading Style Sheet 在Registered Patterns中删除 .css关联
2. Preferences -> Editor -> File Types -> SCSS 下在Registered Patterns中添加 .css关联
3. 随便找一个css文件，右键，将文件类型关联改成scss就可以了。