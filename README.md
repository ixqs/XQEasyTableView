XQEasyTableView 使用说明
======================

XQEasyTableView
-----------------

##简介
`XQTableView` 的赋值方式主要有两种，根据直接给定的数据进行生成，和基于 URL 进行生成。

###直接给定数据

**步骤:**

1. 使用`TableView`的初始化方法创建`TableView`并添加到视图上；
2. 指定`TableView`的`cellType`类型；（`cellType`的**命名规则**：`TableView`所用`cell`的类名）
3. 直接对`dataArray`进行赋值；

###基于URL生成

**步骤:**

1. 使用`TableView`的初始化方法创建`TableView`并添加到视图上；
2. 指定`TableView`的`cellType`类型；（`cellType`的**命名规则**：`TableView`所用`cell`的类名）
3. 调用`- setDataWithUrl: paramDic:pageSize`方法；


##API

####cellType

类型：*Property*

当前页面｀cell｀的类型

**声明**

>  @property (nonatomic, copy) NSString *cellType;

**描述**

  该类型所对应｀cell｀的类名



####dataArray 

类型：*Property＊

页面内容

**声明**
>  @property (nonatomic, copy) NSArray *dataArray;

**描述**
  当前页面对应的数据列表



#### - setDataWithUrl: paramDic: pageSize:
 设置当前页面为网络请求方式
 
**声明**
>  `- (void)setDataWithUrl:(NSString *)url paramDic:(NSDictionary *)paramDic pageSize:(NSInteger)pageSize;`

**参数**

url:网络请求地址

paramDic:请求参数

pageSize:页面大小

**描述**

  设置网络请求链接及参数，同时将自动将数据获取方式设置为网络获取，并进行了一系列操作。


####- refreshWithParamDic:

刷新页面

**声明**
>  `- (void)refreshWithParamDic:(NSDictionary *)parmdic;`

**参数**

parmdic:网络请求参数

**描述**

  设置网络请求链接及参数，再次发起网络请求并刷新页面。


XQEasyTableViewBasicCell
------------------------

##简介##
XQTableViewBasicCell 和XQEasyTableView搭配使用，即在XQEasyTableView中使用的cell类，最好都是继承于XQTableViewBasicCell，XQTableViewBasicCell提供了一系列方便使用的方法。

##使用方法：##
创建继承于XQTableViewBasicCell的cell， 调用configCell方法进行cell的初始化设置及动作的指定。

##API##

####actionBlock

block块属性，用于点击按钮后的回调

**声明**
> `@property (nonatomic, copy) void (^actionBlock)(XQEasyTableViewBasicCell*, NSInteger*);`

**参数**

`XQEasyTableViewBasicCell`：当前`cell`

`NSInteger`：操作标记值


**描述**

在点击按钮或者其它改变cell内容的事件发生后，用来向外传递改变过的值，并进行相应的操作。


#####click

block块属性，用于点击`cell`后的回调

**声明**

> `@property (nonatomic, copy) void (^click)(XQEasyTableViewBasicCell*, NSIndexPath*);`

**参数**

`XQEasyTableViewBasicCell`：当前`cell`

`NSIndexPath`：在`TableView`中的位置

**描述**

相当于代理方法中的 `- tableView:didSelectRowAtIndexPath：`

#####createContent

block块属性，设置数据后`cell`内部的刷新操作

**声明**

> `@property (nonatomic, copy) void (^createContent)(XQEasyTableViewBasicCell*, NSDictionary*);`

**参数**

`XQEasyTableViewBasicCell`: 当前`cell`

`NSDictionary`:  设置内容所用的字典

**描述**
每次进行 `cell.content ＝ dic；`时都会调用，**避免在其中创建控件**。


####height 

类型：*Property*

cell的高度

**声明**

> `@property (nonatomic, assign) CGFloat height;`

**描述**
在`createContent`中进行设置，可以动态改变`cell`的高度。


####- configCell
`cell` 的初始化设置方法

**声明**

> `- (void)configCell;`

**描述**

在里边对`cell`的内部控件及各个属性进行初始化。


####- currentViewController

当前cell所在的ViewController

**声明**

> `- (UIViewController *)currentViewController;`

**描述**

获取当前cell所在的ViewController


