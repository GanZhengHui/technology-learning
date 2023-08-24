## 1.用脚手架vue-cli创建vue项目

1. 新建文件，在文件中打开cmd
2. 在cmd中输入：vue create 项目名



## 2.在项目名终端下引入依赖

1. 引入less：npm i less  和 npm i less-loader@6
2. 引入路由：np i vue-router@3
3. 删除依赖：npm uninstall vue-router
4. 引入进度条：npm i --save nprogress
5. 引入vuex(状态管理，数据容器)：npm i --save vuex@3    装3版本



## 2.项目上线之--打包Vue文件为dist

1. 在终端运行:npm run build
2. 即可打包在dist文件中



## 3.node用express新建一个服务器

1. 新建一个文件，用vscode打开
2. 打开终端，声明合法：npm init
3. 安装express：npm i express
4. 新建server.js文件，写服务器代码
5. 写好服务代码后，在终端运行服务器文件：node server

部署环境完毕后

1. 新建static文件夹
2. 把dist里的所有文件复制到static文件夹里
3. 回到server文件中添加一句代码：app.use(express.static(__dirname + '/static'))
4. 运行server文件即可

![image-20230701163731498](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230701163731498.png)



## 4.UI组件库

**移动端常用 UI 组件库**

1. Vant https://youzan.github.io/vant

2. Cube UI https://didi.github.io/cube-ui

3. Mint UI http://mint-ui.github.io

**PC 端常用 UI 组件库**

1. Element UI https://element.eleme.cn

2. IView UI https://www.iviewui.com