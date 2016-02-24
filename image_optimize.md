# 图片优化

主要说一下图片合并和图片压缩的方法。

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
具体的配置可以参考`sprity`的[README](https://github.com/sprity/sprity)

最后在命令行中输入命令：
````
$ gulp sprites
````
done.

### 图片压缩

先说下`jpeg`格式的图片，尽可能的压缩图片大小，其实`jpeg`的格式是比较容易压缩的，在存储为web所用格式的时候，选择一下图片的质量或品质就可以了，选择“非常高”或者“高”就可以了，也就是品质60到80之间，尽量保证图片是小于`300kb`的。

尺寸中或大的`jpeg`格式的图片请勾选`连续`模式，而不是优化模式。为什么呢，因为优化模式的图片加载方式是从上到下加载，而`连续`模式的加载方式是从低像素到高像素加载的。