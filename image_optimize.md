# 图片优化

主要说一下图片大小和图片合并的方法。

### 图片合并

*说明：这里的教程基于windows环境，以及认为你已经大概知道`gulp`的使用方法。*

为了减少图片的请求次数，可以把多张图片合并成一张图片，合并的图片叫雪碧图，也可以叫精灵图。以前是依靠ps一张张图片手工合并在一起，现在可以把需要合并的图片放在同一个文件夹，然后通过工具生成雪碧图以及样式文件。

首先需要先下载安装[GraphicsMagick](http://www.graphicsmagick.org/)和[ImageMagick](http://www.imagemagick.org/script/index.php)。（这里说下为什么需要安装这两个软件，因为`sprity`默认使用的图片引擎是`lwip`，而在`windows`环境下，`lwip`是个坑，很难安装成功，所以把引擎换成`gm`，也就需要安装前面那两个软件，当然如果你是`mac`环境，可以选用`lwip`的引擎。）

安装成功之后，请重启一下电脑。接着安装`sprity`和`sprity-gm`。
````
$ npm install sprity
$ npm install sprity-gm
````

接着在`gulpfile.js`里写一个合并的任务：
````
gulp.task('sprites', function(){
    var sprity = require('sprity');
    sprity.src({
        name: 'icon',  //需要合并的图片文件夹的名称
        src: 'path/*.png', //图片的路径
        style: '_icon.scss', //定义生成的样式文件名
        format: 'png', //指定需要合并的图片的格式
        engine: 'gm', //设定图片引擎
        'gm-use-imagemagick': true,
        orientation: 'binary-tree',  //合并图片的排列方式
        template: './sprity-css.hbs', //生成样式的模板
        processor: 'scss' //设定生成样式的格式
    })
    .pipe(gulpif('*.png', gulp.dest('img/'), gulp.dest('css/'))); //生成的雪碧图的存放位置和样式的存放位置

});
````

安装成功之后，把图片放到相应的文件夹中，运行`gulp TASKNAME`，就可以了。相关的操作任务和生成模板项目都已经存在有了，如果不清楚，请询问相关同事。

