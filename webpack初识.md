# webpack初识

## 1. 详细文档网址

### 1.1https://juejin.cn/post/6986896605420978189

### 1.2什么是webpack

- webpack 是前端的一个**资源构建工具**，一个**静态模块打包器**；
- 在 webpack 看来，前端的所有资源文件(js/json/css/less/scss/img...)都是一个个**模块**；
- webpack 会根据资源的依赖关系生成一个**依赖关系图**，再打包成对应的**静态资源bundle**。

## 2. webpack五大核心

### 2.1 entry-入口

```
module.exports = {
  entry: './path/to/my/entry/file.js'
};
```

### 2.2 output-出口

output 属性告诉 webpack 在哪里输出它所创建的 bundles，以及如何命名这些文件，默认值为 ./dist。

```
// webpack.config.js:
const path = require('path');
module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    // 输出路径：
    //    --dirname: nodeJs的变量，代表当前文件的绝对路径
    //    resolve: nodeJs里path模块的方法，用来拼接绝对路径
    path: path.resolve(__dirname, 'dist'),
    // 输出文件名
    filename: 'bundle.js'
  }
};
```

指定将 `src/index.js` 文件打包到 `dist/bundle.js` 文件中。其中，`path.resolve` 方法用于解析文件路径，`__dirname` 表示当前文件所在的目录

### 2.3 loader

- loader 让 webpack 能够去处理那些非 JavaScript 文件（webpack 自身只理解 JavaScript）；
- loader 可以将所有类型的文件转换为 webpack 能够处理的有效模块。

```
// webpack.config.js:
const config = {
  module: {
    rules: [
      // 不同类型的文件必须配置不同的规则来处理
      {
        test: /\.css$/, // 匹配什么样的文件
        // use数组中loader的执行顺序：从下到上，从右到左（后进先出）
        use: [
          'style-loader', 
          'css-loader' 
        ]
      }
    ]
  }
};
module.exports = config;
```



### 2.4 plugins-插件

```
// webpack.config.js:
const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装
const webpack = require('webpack'); // 用于访问内置插件
const config = {
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};
module.exports = config;
```



### 2.5 mode-生产模式

- 模式(Mode)指示 webpack 使用相应模式的配置；
- `mode: 'development' | 'production'`;
- 生产环境和开发环境将ES6模块化编译成浏览其能识别的模块化；
- 生产环境比开发环境多一个压缩js代码；

```
// webpack.config.js:
module.exports = {
  mode: 'production'
};
```

## 3. webpack使用

### 第一步：准备

- 与不使用配置文件一样，需要安装 webpack 和 webpack-cli；
- 还需要安装使用的 loader 和 plugins。

```
npm i webpack webpack-cli -D

// 下载loader和plugins
npm i xxx-loader xxx-plugin -D
```

### 第二步：写代码

需要在项目的根目录写一个名为`webpack.config.js`的配置文件。

#### 目录结构

```
webpack初体验2
├── src
│   └── index.js
│   └── test.json
├── webpack.config.js
```

#### 代码

```
// 1. src/index.js
import data from './test.json';
console.log(data);
function add(x, y) {
  return x + y;
}
add(1, 2)
console.log(add(1, 2))

// 2. src/test.json
{
  "testJson": "test json"
}

// 3. webpack.config.js
const { resolve } = require('path'); // 
module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'build.js',
    path: resolve(__dirname, 'build')
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          'style-loader',
          'css-loader' 
        ]
      }
    ]
  },
  plugins: [],
  mode: 'development'
}
```

### 第三步：打包

项目根目录中输入命令`npx webpack`即可。打包好后，控制台还会显示一些打包相关的信息，有兴趣的可以仔细瞅瞅。