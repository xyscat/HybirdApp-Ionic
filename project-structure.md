# 项目结构

让我们剖析一下 Ionic 2 应用。在我们创建的文件夹里，有一个典型的 Cordova 项目结构，我们能安装本地插件、创建平台相关的项目文件。

## ./src/index.html

`src/index.html` 是应用的主入口点，通过它来启动脚本、 CSS 和 bootstrap，或者运行应用。我们不必花过多的时间在这个文件。

对于应用的运行，Ionic 会在HTML中寻找 `<ion-app>` 标签。如：

```
<ion-app></ion-app>
```

在它的下面添加脚本：

```
<script src="build/polyfills.js"></script>
<script src="build/main.js"></script>
```

`build/main.js` 是一个链接文件包含 Ionic，Angular 和 应用的 JavaScript。

`cordova.js` 在本地开发时会 404，在 Cordova 的运行过程它被注入到项目。

## ./src/

在 `src` 目录下，是我们未编译的代码。我们在这块儿完成大量的开发工作。当我们运行 `ionic serve`，`src` 里的代码会被编译为浏览器支持的 JavaScript 版本(目前是 ES5)。这意味着使用 TypeScript 可以在更高版本下工作，但代码会编译为浏览器需要的JavaScript版本。

`src/app/app.module.ts` 是应用的入口点。

这个文件的顶部，如：

```
@NgModule({
  declarations: [
    MyApp,
    HelloIonicPage,
    ItemDetailsPage,
    ListPage
  ],
  imports: [
    IonicModule.forRoot(MyApp)
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    MyApp,
    HelloIonicPage,
    ItemDetailsPage,
    ListPage
  ],
  providers: []
})
export class AppModule {}
```
每个应用都有一个根模块来控制其余的应用。这和 Ionic 和 Angular 1 中的 `ng-app` 很类似。在这块我们也使用`ionicBootstrap`来引导我们的应用。

在这个模块，我们为应用设置了一个根组件在`src/app/app.component.ts`。这是我们应用加载的第一个组件，并且它是为之后加载的其他组件提供了一个容器。在`app.component.ts`，我们给`src/app/app.html`展示模板。

## ./src/app/app.html

`src/app/app.html` 是应用的主模板：

```
<ion-menu [content]="content">

  <ion-header>
    <ion-toolbar>
      <ion-title>Pages</ion-title>
    </ion-toolbar>
  </ion-header>

  <ion-content>
    <ion-list>
      <button ion-item *ngFor="let p of pages" (click)="openPage(p)">
        {{p.title}}
      </button>
    </ion-list>
  </ion-content>

</ion-menu>

<ion-nav [root]="rootPage" #content swipeBackEnabled="false"></ion-nav>
```

在这个模板，我们设置的一个 `ion-menu` 作为一个侧菜单，一个 `ion-nav` 组件去填充主内容区。

`ion-menu`的`[conent]`属性一定要被绑定到`ion-nav`里的本地变量 `content`，所以就明白了它该在哪儿执行。

下一节学习如何创建更多的页面，执行基本的导航。
