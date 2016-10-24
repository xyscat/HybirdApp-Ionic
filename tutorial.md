# Ionic 2教程

现在，我们已经安装好了 Ionic 的开发环境，可以开始构建我们的第一个应用了。这部分带领你开始一个新的应用，添加页面，给面添加导航，等等。开始吧！

## 从零开始一个 Ionic 2 应用

使用 `start` 命令来初始化一个新的 Ionic 应用。如果想创建 Ionic2 应用需要添加 `--v2`。我们还要使用 `tutorial` 模板。Ionic2 应用是用 TypeScript 来编写的。

```
$ ionic start Ionic2Project tutorial --v2
```
这行命令会拉下来 Icnic 2，为应用安装 npm modules，并使得 Cordova 建立起来准备运行。

## 在浏览器查看应用

现在，可以`cd`到新建的项目下。在浏览器里预览一下使用模板创建的应用，使用 `serve`命令。

```
$ cd Ionic2Project
$ ionic serve
```
![image](http://ww4.sinaimg.cn/mw690/005wQZvtgw1f9348lnplnj30cl0bbmx7.jpg)

如果成功的话，你将看到上面的欢迎信息。

在下一节，我们来看看通过`ionic start`命令所创建的项目结构是怎样的。

