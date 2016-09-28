# angularLesson
## 设置快捷键模板

- file -> settings  -> live Template -> javascript -> 添加快捷键 -> define  

## 创建指定文件后缀  

- new -> edit file template -> + ->设置文件扩展名和文件的名字即可    

## 安装markdown插件  

- file -> settings -> plugin -> browser responstory  - > markdown navigator


## 框架和库
- 一个是提供房子的，另一个需要自己搭建房子，给你提供方法，放东西的

## MVC MVVM
- MVC:model数据 view 视图 controller控制器
- MVVM: model view viewModel视图模型
- 命名空间的缺点 调用过长，不能完全避免名字不冲突
- seajs(cmd) r commonjsequirejs(amd) 

## 安装angularjs
- npm node package manager 我们安装node就会提供一个包管理器
- 安装软件时名字不能叫同名
```
npm install angular
```

> 可以通过webstorm自带的命令行进行安装，(view->toolwindow> terminal)安装后会产生node_modules文件夹

## 使用angular
- 引入angularjs
- ng-app($rootScope)
- 想双向绑定的增加ng-model
- {{}}三元，做表达式运算

## 防止闪烁
- ng-bind
- ng-bind-template
- ng-cloak

## 模块化
- 声明模块
```
var app = angular.model('appName',[],fn);
//参数的位置可以改变，但是名字不能变
app.run(['$rootScope',function(){}]);
app.controller('ctrlName',['$rootScope','$scope',function($rootScope,$scope){ //$scope实现双向绑定的桥梁viewModel
    
}]);
```
> 在标签上增加ng-controller指定控制器的作用范围

## ng-click
```
<button ng-click="fn(1,2,3)"></button>
$scope.fn = function(a,b,c){
}
```

## 绑定对象类型的数据
- 数组和对象
```
<div ng-repeat="(key,value) in arrs track by $index" ng-init>
    {{$index}}{{$last}}....
<div>
```
## bootstrap
- 样式的框架,提供了美丽的样式库，还封装了很多插件基于jquery的
```
npm i bootstrap
```

## ng-disabled禁用  

> 所有表单元素 想双向绑定必须增加ng-model属性  

## 数组的方法
- filter 为false过滤掉
- find 找到为true的那一项
- forEach 遍历
- map 映射新的数组

## 指令
- 指令是不依赖于控制的（一般还是需要控制器的） spa框架

```
<my-text></my-text>
app.directive('myText',function(){
    return {
        template:'<div></div>', //模板
        templateUrl:'tmpl/index.html', //模板的引用路径
        restrict:'ECMA', //限制使用范围
        link:function(scope,element,attrs){
            //scope 当前作用域
            //element 当前元素jq对象
            //attrs 属性集合
        },
        replace:true,//将我们的指令标签替换掉，替换成我们的template
        trasclude:true将指令之间的内容保留下来插入到带有ng-transclude的标签内
        scope:true/scope:{}
    }
})
```

## 指令中的scope
- scope独立作用域 scope:{} 完全断绝，完全断绝需要数据，只能通过指令的标签上的属性进行传递
- 引用字符串 @ （取到的是attr对应的字符串）
- 引用的是变量 =（取到的是当前指令所在的作用域的变量）
- 引用函数 &  传递参数的时候使用对象格式

