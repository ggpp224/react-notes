# babel配置

1. 进入项目根目录
   
2. 执行 $ npm install --save-dev babel-cli    
   
3. 在package.json中的scripts下添加build配置, +号对应部分
   
4. ``` json
    {
       "name": "my-project",
       "version": "1.0.0",
   +   "scripts": {
   +     "build": "babel src -d dist"
   +   },
       "devDependencies": {
         "babel-cli": "^6.0.0"
       }
     }
   ```
   
5. 执行 npm install babel-preset-es2015 --save-dev
   
6. 根目录下创建 .babelrc文件
   
7. 执行 echo '{ "presets": ["es2015"] }' > .babelrc      会向.babelrc文件中添加es2015支持
   
8. 执行 $ npm run build



注： "build": "babel src -d dist"       src目录源路径， dist指编译输出路径

