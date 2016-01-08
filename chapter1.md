# 部署开发环境


### 安装nodejs

去[官网](https://nodejs.org/en/)下载安装，暂时不建议安装5.0以上版本。

命令行运行以下命令查看是否安装成功：

![是否安装成功](1.png)


### 选择开发工具

很多种开发工具，你要使用记事本我也没意见啦。推荐使用`sublime text 3`，因为开发过程`css`使用`sass`，所以需要安装`sass`的插件，可以先安装`package control`，然后安装`sass`。如果不清楚请查阅[sublime text 3官网](http://www.sublimetext.com/3)。


### 安装项目依赖

在项目根目录打开命令行，安装`package.json`里面的依赖模块。
````
$ npm install
````


### 可以开始了

开启一个本地服务，配合浏览器进行开发。
````
$ gulp watch
````

*如果是因为监听端口被占用报错，请修改`gulpfile.js`里面的监听端口。*


### 补充

如果需要合并雪碧图，有一个很好使的插件。需要先下载安装[GraphicsMagick](http://www.graphicsmagick.org/)和[ImageMagick](http://www.imagemagick.org/script/index.php)，然后在项目根目录打开命令行安装：
````
$ npm install sprity
$ npm install sprity-gm
````

安装成功之后，把图片放到相应的文件夹中，运行`gulp TASKNAME`，就可以了。相关的操作任务和生成模板项目都已经存在有了，如果不清楚，请询问相关同事。