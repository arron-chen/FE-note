#### webpack定义
webpack是一个前端资源加载/打包工具，它将根据模块的依赖关系进行静态分析，然后将这些模块按照指定的规则生成对应的静态资源。简单来说，webpack会根据我们定义的打包规则，从入口文件（entry）开始对你的项目文件进行分析打包。
#### webpack安装
使用一个工具前，首先得安装它（这是句废话，哈哈哈！）。
在项目根目录下，命令行输入 npm init 新建一个package.json文件（全部回车即可）
``` js
npm init
```
安装webpack（安装时，可指定版本号，不然默认下载最新版本），这里使用webpack3
npm install webpack@3.* --save-dev

#### webpack打包
安装好webpack之后，其实就可以使用webpack进行项目文件打包了，entry.js为入口文件，output.js为打包完成输出的文件。
webpack entry.js output.js

若全局中没有安装webpack，那么直接运行该条命令，会报错。
解决方案：可以在package.json中的script属性中加上webpack的执行命令：
``` js
"scripts": {
    "webpack": "webpack --progressr"
  }
```
--progress：可以看到打包的进度，还有更多的webpack命令属性可以到webpack官网去了解。
这时候，只要运行npm run webpack就可以了
``` js
npm run webpack
```

项目中要使用的打包规则比较复杂，可以把这些规则定义在webpack.config.js文件中，命令行运行webpack时，webpack会根据webpack.config.js里定义的打包规则对项目进行打包。
在项目根目录下，新建一个webpack.config.js文件。
``` js
var path = require("path");

module.exports = {
    entry: "./src/main.js",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "js/main-[hash:5].js"
    }
}
```
entry：webpack打包入口文件。
path：文件输出的文件路径，
filename：输出文件的名称。
path是nodejs内置包，path模块提供了一些工具函数，用于处理文件与目录的路径。
关于path更详细的介绍可以到官方网站上了解：
运行webpack后，打包成功后可以看到：
``` js
Hash: 8875d9ab4c555b1113df
Version: webpack 3.11.0
Time: 278ms
           Asset     Size  Chunks             Chunk Names
js/main-8875d.js  2.68 kB       0  [emitted]  main
   [0] ./src/main.js 208 bytes {0} [built]
```
js/main-8875d.js是打包输出的文件，文件名称是根据webpack.config.js定义的打包规则生成的，[hash:5]表示截取hash的前5位。

#### ebpack + babel
babel是一个广泛使用的转码器，可以将es6语法转化为es5语法。
在webpack中引用babel-loader：
首先安装babel-loader：
npm install babel-loader babel-core --save-dev

定义babel的转码规则，安装babel-preset-env。
``` js
npm install babel-preset-env --save-dev
```

注意：babel还有其他的转码规则，这里就不一一列举了，大家可以到babel的官网去看看。
webpack.config.js中的配置：
``` js
const path = require("path");

module.exports = {
    entry: "./src/main.js",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "js/index.js"
    },
    module: {
        loaders: [
            {
                test: /\.js$/,
                loader: "babel-loader",
                options: {
                    presets: ["env"]
                }
            }
        ]
    }
}
```
运行webpack之后，可以发现输出的js文件中，已经把es6语法转换成es5语法了！
常用loader
以此类推，利用webpack打包其他文件类型的文件也是如此配置，这里列举一些比较常用的loader：
``` 
html
test: /\.html$/,
loader: "html-loader"

css
test: /\.css$/,
loader: "style-loader!css-loader"

less
test: /\.less$/,
loader: "style-loader!css-loader!less-loader"
```
图片
[name]：图片原本的名字；
[hash:5]：本次打包hash值得前5位；
[ext]: 图片的后缀；
test: /\.(jpg|png|gif|svg)$/i,
loader: "file-loader",
options: {
    filename: "[name]-[hash:5].[ext]"
}

与file-loader的区别是：当图片的大小不超过limit时，不会对图片进行打包放到输出的目录下，会作为一个url传过去。
test: /\.(jpg|png|gif|svg)$/i,
loader: "url-loader",
options: {
    limit: 2000，
    filename: "[name]-[hash:5].[ext]"
}

打包后的图片会被压缩。
test: /\.(jpg|png|gif|svg)$/i,
loader: "image-webpack",
options: {
    filename: "[name]-[hash:5].[ext]"
}

html-webpack-plugin插件
该插件用于生成项目所需的index.html。
主要以项目根目录下的index.html为模板，在打包好的目录下生成所需要的index.html。
关于html-webpack-plugin插件的详情可到官方网站了解。