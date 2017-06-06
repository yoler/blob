---
title: vue-webpack配置文件
date: 2017-03-20 09:24:49
tags: 前端
---
今天来总结一下自己搭建vue开发环境的一些心得，其实最重要的就是webpack的配置，下面直接贴出配置代码：
```
var path = require("path");
module.exports = {
	entry: {
		app: path.resolve(__dirname, "./main.js")
		// entry:顾名思义入口文件,app/main.js,输入名字为 app.js
	},
	output: {
		path: path.resolve(__dirname, "./build"),//输出路径
		publicPath: 'build/', //调试或者 CDN 之类的域名,稍候会用到
		filename: "[name].js" //配置生成的文件名
	},
	resolve: {
	   // require时省略的扩展名，如：require('module') 不需要module.js
	   extensions: ['', '.js', '.vue'],
   },
	module: {
		loaders: [
			{
				test: /\.vue$/,
				loader: 'vue'
			},
			{   test: /\.css?$/,
				loader: 'file'
			},
			{
				test: /\.js$/,
				loader: 'babel',
				exclude: /node_modules/

			},
			{
				test: /\.(png|js?eg|gif|svg|woff2?|eot|ttf)(\?.*)?$/,
				loader: 'url',

			}

		]//模块加载器，默认null
	},
	babel: {
        presets: ['es2015'],
        plugins: ['transform-runtime']
    },
	plugins: [] //插件，默认null
};
```

以及package.json文件：
```
{
  "name": "h5app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "yoler",
  "license": "ISC",
  "devDependencies": {
    "babel-core": "^6.22.1",
    "babel-loader": "^6.2.10",
    "babel-plugin-istanbul": "^3.1.2",
    "babel-plugin-transform-runtime": "^6.22.0",
    "babel-preset-es2015": "^6.22.0",
    "babel-preset-stage-2": "^6.22.0",
    "babel-register": "^6.22.0",
    "css-loader": "^0.26.4",
    "element-ui": "^1.2.4",
    "file-loader": "^0.10.1",
    "url-loader": "^0.5.8",
    "vue": "^2.2.2",
    "vue-loader": "^11.1.4",
    "vue-resource": "^1.2.1",
    "vue-router": "^2.3.0",
    "vue-style-loader": "^2.0.0",
    "vue-template-compiler": "^2.2.2",
    "vuex": "^2.2.1"
  }
}
```