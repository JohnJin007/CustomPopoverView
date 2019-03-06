![](https://img.shields.io/badge/platform-iOS-red.svg)&nbsp;![](https://img.shields.io/badge/language-Objective--C-orange.svg)&nbsp;[![CocoaPods](http://img.shields.io/cocoapods/v/CustomPopOverView.svg?style=flat)](http://cocoapods.org/pods/CustomPopOverView)&nbsp;![](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)


# 版本记录
- 1.0.4 添加阴影、边框粗细、边框颜色等属性（**有些API名字改了**，升级到此版本需要做下小改动）
- 1.0.3 支持设置内容相对呼出的位置的上方或者下方，支持自动调整位置
- 1.0.1 修复iOS11下，某些情况不能弹出的bug (经过测试，iOS11 在dismissViewControllerAnimated后弹出时，有时候会无法出现，demo直接跑是没有问题的   
`-showFrom:alignStyle:`下打印
`UIWindow *window = [[UIApplication sharedApplication].windows lastObject];`
这个window是`_UIInteractiveHighlightEffectWindow: 0x7fed5857f7e0`，不是keywindow。
为带来bug的兄弟说声抱歉，可以尝试下修改后的。)


# 一款自定义 弹出视图
自定义弹出视图，内容支持传一组菜单标题，也支持自定义view，或者自定义viewController， 支持任意按钮触发，会显示在按钮底部，也支持切换按钮的对齐方式：左对齐、居中、右对齐

## 预览图如下
![预览图](http://ww3.sinaimg.cn/mw690/72aba7efgw1f3ch00wwwxg20al0j3gqp.gif)
![demo2](http://ww2.sinaimg.cn/mw690/72aba7efgw1f3dcknlfphg20am0j3dm6.gif)

# 用法
- 手动下载: `CustomPopOverView`拖进去
- Cocoapods: `pod 'CustomPopOverView'`



### 自定义view
```
CustomPopOverView *view = [CustomPopOverView popOverView];
view.content = [[UITableView alloc]initWithFrame:CGRectMake(0, 0, 100, 200)];
view.containerBackgroudColor = [UIColor blueColor];
[view showFrom:_leftBtn alignStyle:CPAlignStyleLeft];

```

<pre><code>
CustomPopOverView *view = [CustomPopOverView popOverView];
    
UIButton *btn = [UIButton buttonWithType:UIButtonTypeInfoDark];
btn.bounds = CGRectMake(0, 0, 60, 40);
view.content = btn;    
[view showFrom:sender alignStyle:CPAlignStyleRight];

</code></pre>


### 自定义VC
```
	UIViewController *vc = [[UIViewController alloc]init];
    vc.view.backgroundColor = [UIColor yellowColor];
    vc.view.frame = CGRectMake(0, 0, 200, 200);
    UILabel *lab = [[UILabel alloc]initWithFrame:CGRectMake(0, 0, 140, 100)];
    lab.center = vc.view.center;
    lab.text = @"I'm viewController's view";
    lab.numberOfLines = 0;
    [vc.view addSubview:lab];
    

    CustomPopOverView *view = [CustomPopOverView popOverView];
    view.contentViewController = vc;
    
    [view showFrom:_rightBtn alignStyle:CPAlignStyleRight];
```


### 普通用法（只传一组菜单名称）
```
	_titles = @[@"Menu1", @"Menu2", @"Ah_Menu3"];
	PopOverVieConfiguration *config = [PopOverVieConfiguration new];
    config.triAngelHeight = 5.0;
    config.triAngelWidth = 7.0;
    config.containerViewCornerRadius = 3.0;
    config.roundMargin = 2.0;
    config.defaultRowHeight = 30;
    config.tableBackgroundColor = [UIColor grayColor];
    config.textColor = [UIColor orangeColor];
	
	
	CustomPopOverView *view = [[CustomPopOverView alloc]initWithBounds:CGRectMake(0, 0, 200, 44*3) titleMenus:_titles config:config];
	view.containerBackgroudColor = [UIColor blueColor];
	view.delegate = self;
	[view showFrom:sender alignStyle:CPAlignStyleCenter];
```

### 如果你有问题欢迎issue，希望你能够喜欢





<hr>

# A custom popoverView

This custom popover view, you can give an array of menu titles for normal use. It also support custom view or viewController. It’s frame depends on the button which clicked, and it provides three alignments for the button.

## The preview chart is as follows
![demo](http://ww3.sinaimg.cn/mw690/72aba7efgw1f3ch00wwwxg20al0j3gqp.gif)
![demo2](http://ww2.sinaimg.cn/mw690/72aba7efgw1f3dcknlfphg20am0j3dm6.gif)

## How to use
### custom view
```
CustomPopOverView *view = [CustomPopOverView popOverView];
view.content = [[UITableView alloc]initWithFrame:CGRectMake(0, 0, 100, 200)];
view.containerBackgroudColor = [UIColor blueColor];
[view showFrom:_leftBtn alignStyle:CPAlignStyleLeft];

```

```
CustomPopOverView *view = [CustomPopOverView popOverView];
    
UIButton *btn = [UIButton buttonWithType:UIButtonTypeInfoDark];
btn.bounds = CGRectMake(0, 0, 60, 40);
view.content = btn;    
[view showFrom:sender alignStyle:CPAlignStyleRight];

```

### custom viewController
```
	UIViewController *vc = [[UIViewController alloc]init];
    vc.view.backgroundColor = [UIColor yellowColor];
    vc.view.frame = CGRectMake(0, 0, 200, 200);
    UILabel *lab = [[UILabel alloc]initWithFrame:CGRectMake(0, 0, 140, 100)];
    lab.center = vc.view.center;
    lab.text = @"I'm viewController's view";
    lab.numberOfLines = 0;
    [vc.view addSubview:lab];
    

    CustomPopOverView *view = [CustomPopOverView popOverView];
    view.contentViewController = vc;
    
    [view showFrom:_rightBtn alignStyle:CPAlignStyleRight];
```

### normal use(only needs an array of titles)
```
	_titles = @[@"Menu1", @"Menu2", @"Ah_Menu3"];
	PopOverVieConfiguration *config = [PopOverVieConfiguration new];
    config.triAngelHeight = 5.0;
    config.triAngelWidth = 7.0;
    config.containerViewCornerRadius = 3.0;
    config.roundMargin = 2.0;
    config.defaultRowHeight = 30;
    config.tableBackgroundColor = [UIColor grayColor];
    config.textColor = [UIColor orangeColor];
	
	
	CustomPopOverView *view = [[CustomPopOverView alloc]initWithBounds:CGRectMake(0, 0, 200, 44*3) titleMenus:_titles config:config];
	view.containerBackgroudColor = [UIColor blueColor];
	view.delegate = self;
	[view showFrom:sender alignStyle:CPAlignStyleCenter];
```

### if you have any question welcome to issue to me，hope you like it!

