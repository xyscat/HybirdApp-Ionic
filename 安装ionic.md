# 安装 Ionic

ionic 2 应用程序是通过 ionic 命令行界面(CLI)和使用 Cordova 构建并部署为一个 native 应用。这意味着我们需要安装几个工具来搭建我们的开发环境。

## Ionic CLI 和 Cordova

要开始 Ionic 2 项目，我们需要安装最新版本的 CLI 和 Cordova。在此之前，我们好需要一个最近版本的 Node.js。下载安装 Node.js6 或者更高版本，然后开始安装 Ionic CLI 和 Cordova。

```
$ npm install -g ionic cordova
```
上面安装完成，创建第一个 Ionic 应用：

```
$ ionic start cutePuppyPics --v2
```
然后，开始运行应用，`cd` 到刚被创建的目录下，运行`ionic serve`命令在浏览器测试应用。

```
$ cd cutePuppyPics
$ ionic serve
```
## 平台指导

对于为了创建 iOS 和 Android native 应用的开发者，在你能够充分利用 Ionic 和 Cordova之前，每个平台都要特定的功能和安装须知。

对于 IOS 开发者，请查看 [Cordova iOS Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/)。

对于 Android 开发者，请查看 [Cordova Android Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/android/)。 

