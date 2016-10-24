
# 迁移的概念

Ionic 2 是建立在 Angular 2 之上的，Angular 2 完全重写了原有的框架。所有已知的 Angular 的功能块仍然存在，但是开发者应该了解到它们采用了新的语法并且进行了结构性的变化。想要了解Angular 2 的改变，可以阅读 [Learn Angular 2](http://learnangular2.com/)。

在 Ionic 2，事情会变得更简单。Ionic v1 的所有概念也都存在与 Ionic v2，但是看起来会稍有不同。你仍然要像在 v1 里那样设置视图和控制器，但是在 v2，它们被合并为了一个实例。

v1举例：

```
.config(function($stateProvider){
  $stateProvider
  .state('main', {
    url: '/',
    templateUrl: 'templates/main.html',
    controller: 'MainCtrl'
  })
})

.controller('MainCtrl', function(){

})
```

你可以在V2重写它，如：

```
@Component({
  templateUrl:'main/main.html'
})
export class MainCmp {
  constructor(){

  }
}
```

对于其它的改变，如导航，为了更好的改进，做了很大的改变。现在你可以把组件看作任意的视图并把视图导航到你指定的位置。这使得导航更加灵活，允许更加native 风格的导航 stacks。

## 从 Angular 1 的迁移

虽然 Angular 2 要求应用在语法变化进行更新，开发者应该通过下面的练习来预先确保应用是可更新的。这些提供给你了使你的代码可迁移的预备操作。

### ControllerAs 语法

ControllerAs 语法是 Angular 1.x 的一个特性，它替代了绑定数据到`$scope`，你能绑定到控制器直接的实例。这使得 Angular 1.x 控制器到 Angular 2 类的迁移更加容易。从传统的控制器迁移到 `ControllerAs` 是很容易的。

```
// index.html
<ion-content ng-controller="MainCtrl">
  <ion-item>
    {{data.text}}
  </ion-item>
</ion-content>
```
app.js

```
.controller('MainCtrl', function($scope){
  $scope.data ={
    text: 'Hello World'
  }
})
```
转变为 `controllerAs` 语法，你只需要做几处改变。

index.html

```
<ion-content ng-controller="MainCtrl as main">
  <ion-item>
    {{main.data.text}}
  </ion-item>
</ion-content>
```

app.js

```
.controller('MainCtrl', function(){
  this.data ={
    text: 'Hello World'
  }
})
```

### TypeScript

TypeScript 是 JavaScript 的一个超集，它提供了ES6类和类型注释。通过适配 TypeScript，你可以使用 ES6 来编写代码，这更容易迁移到 Ionic 2。最优的地方是所有JavaScript所支持的 TypeScript 都支持，所以你可以一点一点地转变你的代码。如果你像上面修改了你的控制器，那么你就能很容易地把它转变为一个 TypeScript 类。

app.js

```
.controller('MainCtrl', function(){
  this.data ={
    text: 'Hello World'
  }
})
```
app.ts

```
export class MainCtrl{
  constructor(){
    this.data ={
      text: 'Hello World'
    }
  }
}
```
### 项目结构

在 Angular 1，把所有的JavaScript放在一起，并且都和模板所分离。Ionic 2 和 Angular 2 将会把它们移动到一个组件，这能整理你的项目并使你专注与运行的概念。项目结构就像这样：

![image](http://ww4.sinaimg.cn/mw690/005wQZvtjw1f93e53escvj307308pglf.jpg)

被整理为：

![image](http://ww4.sinaimg.cn/mw690/005wQZvtjw1f93e4znamsj306l08vdfn.jpg)

像这样整理你的项目能帮助你把每个视图和状态作为一个具有模板和控制器的组件。