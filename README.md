### 手动搭建vue-cli
这是一篇手动搭建`vue-cli`的教程，也是自己的一些心得，欢迎star

1. `npm init`初始化仓库
出现`package.json`的文件
2. 安装`vue`
```
npm install vue -g
```
如果报`permission denied`，说明是需要管理员的身份登录
```
sudo npm install vue -g
```
3. 安装`webpack`和`webpack-cli`
```
npm install webpack -g//全局安装
npm install webpack --save-dev//项目安装
```
4. 创建`index.html`以及相对应的`main.js和App.vue`，进行初始化

5. 创建`webpack.config.js`进行配置相关
* 配置入口和出口，即`entry`和`output`
* 安装插件`plugin`,`html-webpack-plugin`用于为应用程序生成 `HTML` 一个文件`
```
npm install html-webpack-plugin --save-dev
```
* 安装`loader`,由于`webpack`只能打包`Javascript`和`Json`文件，所以`loader`让它也能打包其他类型文件，不过需要自己手动安装

`test`表示识别那些被`loader`进行转化的文件类型

`use`表示进行转化的时候，使用哪个`loader`
```
module:{
    rules:[{
        test:/\.vue$/,
        use:'vue-loader'
    }]
}
```
* 配置`webpack-dev-serve`,进行代码更改的时候，在浏览器实时更新
```
npm install webpack-dev-server -g
```
在`package.json`中配置`dev`，能在终端输入`npm run dev`启动整个项目
```
dev:'webpack-dev-server --hot --open --progress'
```
>这时运行`npm run dev`，会报错`Module not found: Error: Can't resolve './App' in '/Users/foreo/Desktop/learn/vue-cli/src`

>注意：在`main.js`中引入`App.vue`时，后缀不能省略

>如果是报`vue-template-compiler must be installed as a peer dependency, or a compatible compiler implementation must be passed via options.`

>则是需要安装`template`编译器，`npm install vue-template-compiler`

>报错`webpack Entrypoint undefined = index.html`,可以配置`stats: { children: false },`具体原因不清楚。。

虽然目前运行的时候，出现很多杂乱的命令，但是运行结果还是正确的，期待以后有时间去优化，谢谢观看～