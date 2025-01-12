# 1. 风格
`一千个读者有一千个哈姆雷特`，每个人都有自己的code style。我也曾为了要不要加分号给同事闹个脸红脖子粗，实际上有必要吗？ 其实JavaScript已经有了比较流行的几个风格

- [JavaScript Standard Style ](https://standardjs.com/readme-zhcn.html)
- [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

我自己使用的是`JavaScript Standard Style`, 我之所以使用这个，是因为它有一些工具。可以让你写完代码后，一旦保存，就自动帮你把你的风格的代码修正成标准风格，而不是死记硬背应该怎么写。看完这个页面，你就应该立马爱上[JavaScript Standard Style ](https://standardjs.com/readme-zhcn.html), 如果你用vscode, 恰好你有写vue, 你想在.vue文件中使用standard风格，那么你需要看看[这篇文章](https://segmentfault.com/a/1190000012468438)


# 2. 可维护性
> 很多时候，我们不是从零开始，开发新代码。而是去维护别人的代码，以他人的工作成果为基础。确保自己的代码可维护，是赠人玫瑰，手留余香的好事。一方面让别人看的舒服，另一方面也防止自己长时间没看过自己的代码，自己都难以理解。

## 2.1. 什么是可维护代码
可维护的代码的一些特征

- `可理解`易于理解代码的用途
- `可适应`数据的变化，不需要完全重写代码
- `可扩展`要考虑未来对核心功能的扩展
- `可调试`给出足够的信息，让调试的时候，确定问题所在
- `不可分割`函数的功能要单一，功能粒度不可分割，可复用性增强

## 2.2. 代码约定
### 2.2.1. 可读性
- 统一的缩进方式
- 注释
- 空白行

#### 2.2.1.1. 缩进：
- 一般使用4个空格
- 不用制表符的原因是它在不同编辑器里显示效果不同

#### 2.2.1.2. 注释：哪些地方需要注释？
- 函数和方法
- 大段代码
- 复杂的算法
- hack

#### 2.2.1.3. 空白行：哪些地方需要空白行？
- 方法之间
- 方法里的局部变量和第一个语句之间
- 单行或者多行注释
- 方法内每个逻辑单元之间
```
// Good
if (wl && wl.length) {

    for (i = 0, l = wl.length; i < l; ++i) {
        p = wl[i];
        type = Y.Lang.type(r[p]);
        
        if (s.hasOwnProperty(p)) {
        
            if (merge && type == 'object') {
                Y.mix(r[p], s[p]);
            } else if (ov || !(p in r)) {
                r[p] = s[p];
            }
        }
    }
}
```

#### 2.2.1.4. 代码应当易于理解
- 唯一标准：`让别人理解的时间最小`

#### 2.2.1.5. 把信息装到名字里
- 选择专业的词
- 避免泛泛的名字
- 使用具体的名字代替抽象的名字
- 为名字携带更多的信息
- 名字的作用域越大，最好名字越长
- 丢掉没用的词

单词 |	更多选择
--- | ---
send | deliver, dispatch, announce, distribute,route
find | search, extract, locate, recover
start | launch, create, begin, open
make | create, set up, build, generate, compose, add ,new 

#### 2.2.1.6. 审美

我之前学设计的时候看过一本书，[写给大家看的设计书（第3版）](https://book.douban.com/subject/3323633/)将这本书中的设计审美原理应用到写代码上，真实十分贴切，如果你读过此书，你的审美能力会大幅提高。

- 对齐
- 重复
- 对比
- 亲密性 按照亲密关系分段
- 顺序

![](http://p3alsaatj.bkt.clouddn.com/20180315182604_54Imyu_.jpeg)

#### 2.2.1.7. 写什么样的注释
- 不要写一眼就能看懂的注释，类似于此地无银三百两
- 与其写注释，不如把变量名函数名写好，可以从名字中理解
- 记录你的思想
- 加入评论
- 指出哪里有陷阱，需要注意
- 言简意赅，不要啰嗦
- 不要使用不明确的代词，不要像算命先生，如何解释都对


#### 2.2.1.8. 可读性控制流
- `追求最小理解时间`，而不是最少代码行
- `尽可能提前return结果`
- `少点嵌套，要尽可能扁平化`
- 理解执行流程。有些是连续执行。有些是随时都可能执行，像事件回调
- 避免使用while, 一般我们循环都是为了遍历数组，为什么不用forEach呢？


#### 2.2.1.9. 拆分超长表达式
- 拆分超长的表达式
- 拆分巨大的语句
- `尽量把逻辑包裹在函数中，不要重复你自己 DRY`

#### 2.2.1.10. 变量与可读性
- 减少变量，变量越少越好
- 减少中间结果，垂直消费
- 减少用于控制流的变量
- 缩小变量的作用域
- 用到变量再定义，不要提前定义，不然还要随时想着，之前定义的变量是用干嘛的呢？

#### 2.2.1.11. 重构
- 抽取不相关的自子问题
- 抽取各种配置性的变量在一起，他们都是配置
- 尽量写纯函数
- 创建大量通用代码
- 打造自己的武器装备库
- 简化接口传参
- 过犹不及，不要太苛刻

#### 2.2.1.12. 一次只做一件事

#### 2.2.1.13. 少写代码
- `最好的代码就是没有代码`
- 别费神实现那个功能，你不会需要的
- 质疑和拆分的需求
- 保持小代码库
- 删除没用的代码
- 删除没有的注释

#### 2.2.1.14. 调试
- 尽可能将错误打印出来，不要隐藏

### 2.2.2. 变量名和函数名
> There are only two hard problem in Computer Science cache invalidation and naming things.---Phil Karlton
- 驼峰式命名
- 变量名以名词开头
- 方法名以动词开头
- 常量全部大写
- 构造函数以大写字母开头
- jQuery对象以"$"符号开头
- 自定义事件处理函数以“on”开头

```
// Good
var count = 10;
var myName = "wdd";
var found = true;

// Bad: Easily confused with functions
var getCount = 10;
var isFound = true;

// Good
function getName() {
    return myName;
}

// Bad: Easily confused with variable
function theName() {
    return myName;
}

// Bad:
var btnOfSubmit = $('#submit');

// Good:
var $btnOfSubmit = $('#submit');

// Bad:给App添加一个处理聊天事件的函数，一般都是和websocket服务端推送消息相关
App.addMethod('createChat',function(res){
    App.log(res);
});
// Bad: 此处调用,这里很容易误以为这个函数是处理创建聊天的逻辑函数
App.createChat();

// Good: 
App.addMethod('onCreateChat',function(res){
    App.log(res);
});
// Good：此处调用
App.onCreateChat();
```
> 变量命名不仅仅是一种科学，更是一种艺术。总之，要短小精悍，见名知意。有些名词可以反应出变量的类型。

#### 2.2.2.1. `变量名`

名词 | 数据类型含义
--- | ---
count, length,size |  数值
name, title,message | 字符串
i, j, k | 用来循环
car,person,student,user | 对象
success,fail | 布尔值
payload | post数据的请求体
method | 请求方式

#### 2.2.2.2. `函数名`

动词 | 含义
--- | ---
can | Function returns a boolean
has | Function returns a boolean
is | Function returns a boolean
get | Function returns a nonboolean
set |　Function is used to save a value

#### 2.2.2.3. `一些与函数名搭配的常用动词`
动词 | 用法
--- | ---
send | 发送
resend | 重发
validate | 验证
query | 查询
create | 创建
add | 添加
delete | 删除
remove | 移除
insert | 插入
update | 更新，编辑
copy | 复制
render | 渲染
close | 关闭
open | 开启
clear | 清除
edit | 编辑
query | 查询
on | 当事件发生
list | 渲染一个列表，如用户列表renderUsersList()
content | 渲染内容，如用户详情的页面 renderUserContent()

#### 2.2.2.4. `接口常用的动词`
对于http请求的最常用的四种方法，get,post,put,delete，有一些常用的名词与其对应

含义 | 请求方法 | 词语 | 栗子
--- | --- | --- | ---
增加 | post | create | createUser,createCall
删除 | delete | delete | deleteUser
修改 | put | update | updateUser,updateProfile
查询 | get | get,query | getUser,queryUser(无条件查询使用get，有条件查询使用query) 


#### 2.2.2.5. `学会使用单复数命名函数`

函数名 | 含义
--- | ---
getUser() | 获取一个用户，一般是通过唯一的id来获取
getUsers() | 获取一组用户，一般是通过一些条件来获取
createUser() | 创建一个用户
createUsers() | 创建一组用户

#### 2.2.2.6. `常量`

```
var MAX_COUNT = 10;
var URL = "http://www.nczonline.net/";
```

#### 2.2.2.7. `构造函数`

```
// Good
function Person(name) {
    this.name = name;
}
Person.prototype.sayName = function() {
    alert(this.name);
};
var me = new Person("wdd");
```

#### 2.2.2.8. `底层http请求接口函数`

- 建议使用“_”开头，例如App._getUsers();而对于接口函数的封装，例如App.getUsers(),内部逻辑调用App._getUsers();

### 2.2.3. 文件名
- 全部使用小写字母
- 单词之间的间隔使用“-”

eg：
```
app-main.js
app-event.js
app-user-manger.js
```

### 2.2.4. 文件归类
自己写的js文件最好和引用的一些第三方js分别放置在不同的文件夹下。

### 2.2.5. 千万别用alert

`alert的缺点`

- 如果你用alert来显示提醒消息，那么用户除了点击alert上的的确定按钮外，就只能点击上面的关闭，或者选择禁止再选择对话框，除此以外什么都不能操作。
- 有些浏览器如果禁止了alert的选项，那么你的alert是不会显示的
- 如果你在try catch语句里使用alert，那么console里将不会输出错误信息，你都没办法查看错误的详细原因，以及储出错的位置。

`更优雅的提醒方式`

- console.log() 普通提示消息
- console.error() 错误提示消息
- console.info() 信息提示消息
- console.warn() 警告提示消息


## 2.3. 松散耦合
- html文件中尽可能避免写js语句
- 尽量避免在js更改某个css类的属性，而使用更改类的方法
- 不要在css中写js的表达式
- 解耦应用逻辑和事件处理程序

### 2.3.1. 将应用逻辑和事件处理程序的解耦
```
//一般事件订阅的写法，以jQuery的写法为栗子
$(document).on('click','#btn-get-users',function(event){
    event.stopPropagation();
    
    //下面的省略号表示执行获取所有用于并显示在页面上的逻辑
    // Bad
    ...
    ...
    ...
    //
});
```
如果增加了需求，当点击另外一个按钮的时候，也要执行获取所有用户并显示在页面上，那么上面省略的代码又要复制一份。如果接口有改动，那么需要在两个不同的地方都要修改。
所以，应该这样。
```
$(document).on('click','#btn-get-users',function(event){
    event.stopPropagation();
    
    //将应用逻辑分离在其他个函数中
    // Good
    App.getUsers();
    App.renderUsers();
});
```
### 2.3.2. 松散解耦规则

- 不要将event对象传给其他方法，只传递来自event对象中的某些数据
- 任何事件处理程序都应该只处理事件，然后把处理转交给应用逻辑。

### 2.3.3. 将异步请求和数据处理解耦
```
// Bad
ReqApi.tenant.queryUsers({},function(res){
    if(!res.success){
        console.error(res);
        return;
    }
    
    //对数据的处理
    ...
    ...
    ...
});    
```
上面代码对数据的处理直接写死在异步请求里面，如果换了一个请求，但是数据处理方式是一样的，那么又要复制一遍数据处理的代码。最好的方式是将数据处理模块化成为一个函数。
```
// Good
ReqApi.tenant.queryUsers({},function(res){
    if(!res.success){
        console.error(res);
        return;
    }
    
    //对数据的处理
    App.renderUsers(res.data);
}); 
```
**异步请求只处理请求，不处理数据。函数的功能要专一，功能粒度不可分割。**

### 2.3.4. 不要将某个变量写死在函数中，尽量使用参数传递进来
如果你需要一个函数去验证输入框是否是空，如下。这种方式就会绑定死了这个只能验证id为test的输入框，换成其他的就不行
```
// bad
function checkInputIsEmpty(){
    var value = $('#test').val();
    if(value){
        return true;
    }
    else{
        return false;
    }
}

// good 
function isEmptyInput(id){
    var value = $('#'+id).val();
    if(value){
        return true;
    }
    else{
        return false;
    }
}
```


## 2.4. 编程实践
### 2.4.1. 尊重对象所有权
javascript动态性质使得几乎任何东西在任何时间都能更改，这样就很容易覆写了一些默认的方法。导致一些灾难性的后果。`如果你不负责或者维护某个对象，那么你就不能对它进行修改。`

- 不要为实例或原型添加属性
- 不要为实例或者原型添加方法
- 不要重复定义已存在的方法

### 2.4.2. 避免全局变量
```
// Bad 两个全局变量
var name = "wdd";
function getName(){
    console.log(name);
}

// Good 一个全局变量
var App = {
    name:"wdd",
    sayName:function(){
        console.log(this.name);//如果这个函数当做回调数使用，这个this可能指向window,
    }
};
```
单一的全局变量便是命名空间的概念，例如雅虎的YUI,jQuery的$等。

### 2.4.3. 避免与null进行比较
```
function sortArray(values){
    // 避免
    if(values != null){
        values.sort(comparator);
    }
}
```
```
function sortArray(values){
    // 推荐
    if(values instanceof Array){
        values.sort(comparator);
    }
}
```
#### 2.4.3.1. 与null进行比较的代码，可以用以下技术进行替换

- 如果值是一个应用类型，使用**instanceof**操作符，检查其构造函数
- 如果值是基本类型，使用**typeof**检查其类型
- 如果是希望对象包含某个特定的方法名，则只用**typeof**操作符确保指定名字的方法存在于对象上。

`代码中与null比较越少，就越容易确定代码的目的，消除不必要的错误。`

### 2.4.4. 从代码中分离配置文件
配置数据是一些硬代码(hardcoded)，看下面的栗子
```
function validate(value){
    if(!value){
        alert('Invalid value');
        location.href = '/errors/invalid.php';
    }
}
```
上面代码里有两个配置数据，一个是UI字符串('Invalid value'),另一个是一个Url('/error/invalid.php')。如果你把他们写死在代码里，那么如果当你需要修改这些地方的时候，那么你必须一处一处的检查并修改，而且还可能会遗漏。

#### 2.4.4.1. 所以第一步是要区分，哪些代码应该写成配置文件的形式？

- 显示在UI元素中的字符串
- URL
- 一些重复的唯一值
- 一些设置变量
- 任何可能改变的值 

#### 2.4.4.2. 一些例子
```
var Config = {
    "MSG_INVALID_VALUE":"Invalid value",
    "URL_INVALID":"/errors/invalid.php"
}
```

### 2.4.5. 调试信息开关
在开发过程中，可能随处留下几个**console.log**,或者**alert**语句，这些语句在开发过程中是很有价值的。但是项目一旦进入生产环境，过多的console.log可能影响到浏览器的运行效率，过多的alert会降低程序的用户体验。而我们最好不要在进入生产环境前，一处一处像扫雷一样删除或者注释掉这些调试语句。

`最好的方式是设置一个开关。`
```
//全局命令空间
var App = {
    debug:true,
    log:function(msg){
        if(debug){
            console.log(msg);
        }
    },
    alert:function(msg){
        if(debug){
            alert(msg);
        }
    }
};

//使用
App.log('获取用户信息成功');
App.alert('密码不匹配');

//关闭日志输出与alert
App.debug = false;
```

### 2.4.6. 使用jQuery Promise
没使用promise之前的回调函数写法
```
// bad：没使用promise之前的回调函数写法
function sendRequest(req,successCallback,errorCallback){
    var inputData = req.data || {};
    inputData = JSON.stringify(inputData);
    $.ajax({
        url:req.base+req.destination,
        type:req.type || "get",
        headers:{
            sessionId:session.id
        },
        data:inputData,
        dataType:"json",
        contentType : 'application/json; charset=UTF-8',
        success:function(data){
            successCallback(data);
        },
        error:function(data){
            console.error(data);
            errorCallback(data);
        }
    });
}

//调用
sendRequest(req,function(res){
    ...
},function(res){
    ...
});
```
使用promise之后
```
function sendRequest(req){
    var dfd = $.Deferred();
    var inputData = req.data || {};
    inputData = JSON.stringify(inputData);
    $.ajax({
        url:req.base+req.destination,
        type:req.type || "get",
        headers:{
            sessionId:session.id
        },
        data:inputData,
        dataType:"json",
        contentType : 'application/json; charset=UTF-8',
        success:function(data){
            dfd.resolve(data);
        },
        error:function(data){
            dfd.reject(data);
        }
    });
    
    return dfd.promise();
}

//调用
sendRequest(req)
.done(function(){
    //请求成功
    ...
})
.fail(function(){
    //请求失败
    ...
});
```

### 2.4.7. 显示错误提醒，不要给后端接口背锅

假如前端要去接口获取用户信息并显示出来，如果你的请求格式是正确的，但是接口返回400以上的错误，你必须通过提醒来告知测试，这个错误是接口的返回错误，而不是前端的逻辑错误。

### 2.4.8. REST化接口请求
> 对资源的操作包括获取、创建、修改和删除资源，这些操作正好对应HTTP协议提供的GET、POST、PUT和DELETE方法。

`对应方式`

请求类型 | 接口前缀
--- | ---
GET | .get,
POST | .create 或者 .get
PUT | .update
DELETE | .delete

`说明`

- 有些接口虽然是获取某一个资源，但是它使用的却是POST请求，所以建议使用.get比较好

示例：
```
// 与用户相关的接口
App.api.user = {};

// 获取一个用户: 一般来说是一个指定的Id，例如userId
App.api.user.getUser = function(){
    ...
};

// 获取一组用户: 一般来说是一些条件，获取条件下的用户，筛选符合条件的用户
App.api.user.getUsers = function(){
    ...
};

// 创建一个用户
App.api.user.createUser = function(){
    
};

// 创建一组用户
App.api.user.createUsers = function(){
    
};

// 更新一个用户
App.api.user.updateUser = function(){
    
};

// 更新一组用户
App.api.user.updateUsers = function(){
    
};

// 更新一个用户
App.api.user.updateUser = function(){
    
};

// 更新一组用户
App.api.user.updateUsers = function(){
    
};

// 删除一个用户
App.api.user.deleteUser = function(){
    
};

// 删除一组用户
App.api.user.deleteUsers = function(){
    
};
```


# 3. 性能

## 3.1. 注意作用域
- 避免全局查找
- 避免with语句

## 3.2. 选择正确的方法
- 优化循环
    - `减值迭代`：从最大值开始，在循环中不断减值的迭代器更加高效
    - `简化终止条件`：由于每次循环过程都会计算终止条件，所以必须保证它尽可能快。也就是避免其他属性查找
    - `简化循环体`：由于循环体是执行最多的，所以要确保其最大限度地优化。
- 展开循环
- 避免双重解释：


```
// **Bad** 某些代码求值
eval("alert('hello')");

// **Bad** 创建新函数
var sayHi = new Function("alert('hello')");

// **Bad** 设置超时
setTimeout("alert('hello')");
```

- 性能的其他注意事项
    - 原生方法较快
    - switch语句较快：可以适当的替换ifelse语句`case 的分支不要超过128条`
    - 位运算符较快


## 3.3. 最小化语句数

### 3.3.1. 多个变量声明(`废弃`)

```
// 方式1：Bad
var count = 5;
var name = 'wdd';
var sex = 'male';
var age = 10;

// 方式2：Good
var count = 5,
    name = 'wdd',
    sex = 'male',
    age = 10;
```


`2017-03-07 理论上方式2可能要比方式1性能高一点。但是我在实际使用中，这个快一点几乎是没什么感受的。就像你无法感受到小草的生长一样。反而可读性更为重要。所以，每行最好只定义一个变量，并且每行都有一个var,并用分号结尾。`


### 3.3.2. 插入迭代值

```
// Good
var name = values[i++];
```

### 3.3.3. 使用数组和对象字面量


```
// Good
var values = ['a','b','c'];

var person = {
    name:'wdd',
    age:10
};
```

`只要有可能，尽量使用数组和对象字面量的表达式来消除不必要的语句`


## 3.4. 优化DOM交互

> 在JavaScript各个方面中，DOM无疑是最慢的一部分。DOM操作与交互要消耗大量的时间。因为他们往往需要重新渲染整个页面或者某一部分。进一步说，看似细微的操作也可能花很久来执行。因为DOM要处理非常多的信息。理解如何优化与DOM的交互可以极大的提高脚本完成的速度。


- 使用dom缓存技术
- 最小化现场更新
- 使用innerHTML插入大段html
- 使用事件代理

### 3.4.1. Dom缓存技术

调用频率非常高的dom查找，可以将DOM缓存在于一个变量中


```
// 最简单的dom缓存

var domCache = {};

function myGetElement(tag){
    return domCache[tag] = domCache[tag] || $(tag);
}
```


## 3.5. 避免过长的属性查找，设置一个快捷方式


```
// 先看下面的极端情况
app.user.mother.parent.home.name = 'wdd'
app.user.mother.parent.home.address = '上海'
app.user.mother.parent.home.weather = '晴天'

// 更优雅的方式
var home = app.user.mother.parent.home;
home.name = 'wdd';
home.address = '上海',
home.weather = '晴天'
```

`注意`
使用上面的方式是有前提的，必须保证app.user.mather.parent.home是一个对象，因为对象是传递的引用。如果他的类型是一个基本类型，例如：number,string,boolean，那么复制操作仅仅是值传递，新定义的home的改变，并不会影响到app.user.mather.parent.home的改变。

## 3.6. 优化循环
### 3.6.1. 不要使用超过3层for循环

如果比必须使用3层循环，那么你可以思考一下，有没有可以替代的方案。我相信应该是有的。

### 3.6.2. 尽量使用forEach遍历数组
forEach循环虽说性能上可能不如for循环，但是可读性会更好。结束箭头函数，在不用定义变量的情况下，也可以访问上层的this。

### 3.6.3. 不要使用for in ，优先使用Object.keys()

```
Object.keys(obj).forEach((key) => {
    // 我相信这样更好
})
```

# 4. 快捷方式

## 4.1. 字符串转数字

```
+'4.1' === 4.1
```

## 4.2. 数字转字符

```
4.1+'' === '4.1'
```

## 4.3. 字符串取整

```
'4.99' | 0 === 4
```

# 5. 通用编码原则

建议读者自行扩展

- `DRY(don't repeat yourself: 不要重复你自己)`
- `高内聚低耦合`
- `开放闭合`
- `最小意外`
- `单一职责(single responsibility)`
- `KISS`

## 5.1. UNIX哲学

1. 程序应该只关注一个目标，并尽可能把它做好。让程序能够互相协同工作。应该让程序处理文本数据流，因为这是一个通用的接口。
2. `做一件事，做好它`
3. 你永远不会知道你的程序会在什么地方耗费时间。程序的瓶颈常常出现在意想不到的地方，因此在你确信找到瓶颈后再动手优化代码吧
4. 功能全面的算法比简单的算法更容易产生Bug，更难实现。尽量使用简单的算法和数据结构。
5. 数据决定一切。如果选择的数据结构能很好的管理数据，算法部分往往不言自明。记住`数据结构，而非算法，才是编程的关键`
6. 小即是美。
7. 所有程序都是数据的过滤器。
8. 程序随需求而增长（Worse is better

前端方面有很多文章冠以“奇技淫巧”的名称，实际上我也写过。但是你要记住的是：`数据结构，而非算法，才是编程的关键`


# 6. 高级技巧

## 6.1. 安全类型检测
- javascript内置类型检测并不可靠
- safari某些版本（<4）typeof正则表达式返回为function

建议使用Object.prototype.toString.call()方法检测数据类型

```
function isArray(value){
    return Object.prototype.toString.call(value) === "[object Array]";
}

function isFunction(value){
    return Object.prototype.toString.call(value) === "[object Function]";
}

function isRegExp(value){
    return Object.prototype.toString.call(value) === "[object RegExp]";
}

function isNativeJSON(){
    return window.JSON && Object.prototype.toString.call(JSON) === "[object JSON]";
}
```

`对于ie中一COM对象形式实现的任何函数，isFunction都返回false，因为他们并非原生的javascript函数。`

**在web开发中，能够区分原生与非原生的对象非常重要。只有这样才能确切知道某个对象是否有哪些功能**

以上所有的正确性的前提是：Object.prototype.toString没有被修改过


## 6.2. 作用域安全的构造函数

```
function Person(name){
    this.name = name;
}

//使用new来创建一个对象
var one = new Person('wdd');

//直接调用构造函数
Person();
```

由于this是运行时分配的，如果你使用new来操作，this指向的就是one。如果直接调用构造函数，那么this会指向全局对象window,然后你的代码就会覆盖window的原生name。如果有其他地方使用过window.name, 那么你的函数将会埋下一个深藏的bug。

`那么，如何才能创建一个作用域安全的构造函数？`


```
function Person(name){
    if(this instanceof Person){
        this.name = name;
    }
    else{
        return new Person(name);
    }
}
```

## 6.3. 惰性载入函数
假设有一个方法X，在A类浏览器里叫A,在b类浏览器里叫B,有些浏览器并没有这个方法,你想实现一个跨浏览器的方法。

惰性载入函数的思想是：`在函数内部改变函数自身的执行逻辑`

```
function X(){
    if(A){
        return new A();
    }
    else{
        if(B){
            return new B();
        }
        else{
            throw new Error('no A or B');
        }
    }
}
```

换一种写法

```
function X(){
    if(A){
        X = function(){
            return new A();
        };
    }
    else{
        if(B){
            X = function(){
                return new B();
            };
        }
        else{
            throw new Error('no A or B');
        }
    }
    
    return new X();
}
```

## 6.4. 防篡改对象
### 6.4.1. 不可扩展对象 Object.preventExtensions
```
// 下面代码在谷歌浏览器中执行
> var person = {name: 'wdd'};
undefined
> Object.preventExtensions(person);
Object {name: "wdd"}
> person.age = 10
10
> person
Object {name: "wdd"}
> Object.isExtensible(person)
false
```

### 6.4.2. 密封对象Object.seal
密封对象不可扩展，并且不能删除对象的属性或者方法。但是属性值可以修改。
```
> var one = {name: 'hihi'}
undefined
> Object.seal(one)
Object {name: "hihi"}
> one.age = 12
12
> one
Object {name: "hihi"}
> delete one.name
false
> one
Object {name: "hihi"}
```

### 6.4.3. 冻结对象 Object.freeze
最严格的防篡改就是冻结对象。对象不可扩展，而且密封，不能修改。只能访问。

## 6.5. 高级定时器
### 6.5.1. 函数节流
函数节流的思想是：`某些代码不可以没有间断的连续重复执行`
```
var processor = {
	timeoutId: null,

	// 实际进行处理的方法
	performProcessing: function(){
		...
	},

	// 初始化调用方法
	process: function(){
        if (this.timeoutId) return;

		var that = this;

		this.timeoutId = setTimeout(function(){
			that.performProcessing();
            that.timeoutId = null;
		}, 100);
	}
}

// 尝试开始执行
processor.process();
```

### 6.5.2. 中央定时器
页面如果有十个区域要动态显示当前时间，一般来说，可以用10个定时来实现。其实一个中央定时器就可以搞定。


中央定时器动画 demo地址：http://wangduanduan.coding.me/my-all-demos/ninja/center-time-control.html

```
var timers = {
		timerId: 0,
		timers: [],
		add: function(fn){
			this.timers.push(fn);
		},
		start: function(){
			if(this.timerId){
				return;
			}

			(function runNext(){
				if(timers.timers.length > 0){
					for(var i=0; i < timers.timers.length ; i++){
						if(timers.timers[i]() === false){
							timers.timers.splice(i, 1);
							i--;
						}
					}

					timers.timerId = setTimeout(runNext, 16);
				}
			})();
		},
		stop: function(){
			clearTimeout(timers.timerId);
			this.timerId = 0;
		}
	};
```

# 7. 函数式编程
推荐阅读：[JS函数式编程中文版](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/)

# 8. HTML的告诫
- 使用input的时候，一定要加上maxlength属性。（你以为只需要输入一个名字的地方，用户可能复制一篇文章放进去。）
- 从input取值的时候，最好去除一下首尾空格

# 9. ajax的告诫
ajax在使用的时候，例如点击按钮，获取某个列表。需要注意以下方面
1. ajax请求还没有结束时，按钮一定要disabled，防止多次点击。请求结束时，才去掉按钮的disabled属性。
2. 请求没结束的时候，一定要显示一个gif的动画，告诉用户请求还在loading。不要让用户以为这垃圾程序又卡死了。
3. 请求的结果如果是空的，一定要告诉用户: 很抱歉，暂时没有查询到相关记录之类的话语。不要给一个空白页面给用户。
4. 最好考虑到请求报错的情况，给出友好的错误提醒。


# 10. 代码整洁之道
## 10.1. 函数整洁

- `尽量将所有代码封装在函数中，不要暴露全局变量`
- `每个函数的函数体中，代码行越少越好，最好一个函数中就一句代码`
- `一个文件中代码行尽量越少越好`。不要写一个几千行的一个文件，这样即为难你自己，也为难后来的维护者。小而美的文件尽量维持在500行以内。然后通过构建工具去打包在一起。

# 11. 工程化与模块化
## 11.1. 前端构建工具必不可少
### 11.1.1. webpack
### 11.1.2. rollup
### 11.1.3. parcel

# 12. 数据结构与算法
## 12.1. 优秀的数据结构可以让算法更简单

如果说数据结构重要还是算法重要，我一定会说：数据结构重要。优秀的数据结构可以让你用很简单的算法来进行业务工作。反之，一个很烂的数据结构，往往就会让开发者很难再上面进行CRUD，而且在数据量增大的情况下会非常影响性能。

通常情况下，算法的更新要快与数据结构的更新。一个项目换了个开发者，新的开发者可能会完全重构业务代码，但是数据结构一般不会去改变。


# 13. 协议 TCP IP HTTP

`如果你认为前端不需要关于协议的知识，那么你就是大错特错了。其实不仅仅是前端，所有的开发者都应该学习底层的协议。因为他们是互联网通信的基石。`

> 推荐三本必读的书籍

- [HTTP权威指南](https://book.douban.com/subject/10746113/)
- [图解TCP/IP : 第5版](https://book.douban.com/subject/24737674/)
- [图解HTTP](https://book.douban.com/subject/25863515/)

或者你一也可以看看关于协议方面的一些问题，以及如果你遇到过，你是否知道如何解决：

- [可能被遗漏的https与http的知识点](https://wdd.js.org/you-dont-know-https-and-http.html)
- [哑代理 - TCP链接高Recv-Q，内存泄露的罪魁祸首](https://wdd.js.org/tcp-high-recv-q-or-send-q-reasons.html)

# 14. 推荐深度阅读

## 14.1. 至少要读两遍的书籍
- [JavaScript高级程序设计（第3版）](https://book.douban.com/subject/10546125/)
- [ES6标准入门（第2版）](https://read.douban.com/ebook/35652061/?dcs=subject-rec&dcm=douban&dct=10546125)
- [JavaScript语言精粹](https://book.douban.com/subject/3590768/)

## 14.2. 推荐阅读技术书籍

- [Node.js实战](https://book.douban.com/subject/25870705/)
- [编写可读代码的艺术](https://book.douban.com/subject/10797189/)
- [编写可维护的JavaScript](https://book.douban.com/subject/21792530/)
- [JavaScript忍者秘籍（第2版）](https://book.douban.com/subject/30143702/)
- [HTTP权威指南](https://book.douban.com/subject/10746113/)
- [图解TCP/IP : 第5版](https://book.douban.com/subject/24737674/)
- [图解HTTP](https://book.douban.com/subject/25863515/)
- [代码整洁之道](https://book.douban.com/subject/4199741/)
- [js函数式编程指南](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/)

## 14.3. 推荐阅读在线文章
- [Writing Fast, Memory-Efficient JavaScript](https://www.smashingmagazine.com/2012/11/writing-fast-memory-efficient-javascript/)
- [JavaScript 秘密花园](https://bonsaiden.github.io/JavaScript-Garden/zh/)
- [You-Dont-Know-JS](https://github.com/getify/You-Dont-Know-JS)
- [关于缓存，你应该链接的一切](https://www.mnot.net/cache_docs/)
- [JS函数式编程中文版](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/content/)


## 14.4. 技术之外
- [筑巢引凤-高黏度社会化网站设计秘诀](https://book.douban.com/subject/5290566/)
- [黑客与画家](https://book.douban.com/subject/6021440/)

# 15. 务必掌握的技能
## 15.1. git
- [Pro Git](https://git-scm.com/book/zh/v2)

# 16. 务必掌握开发工具
- [vscode](https://code.visualstudio.com/)

# 17. 推荐关注的前端微信公众号

- 前端开发
- 前端大全
- 前端周刊
- 奇舞周刊
- 前端之巅
- FEX团队

# 18. 核心思想： 降低软件熵

软件熵（Software entropy）是指软件的无序程度。软件熵可用来说明软件在经过不断修改后，无序程度提高的现象。--[wiki](https://zh.wikipedia.org/wiki/%E8%BB%9F%E9%AB%94%E7%86%B5)。熵作为混乱程度的度量，在软件持续开发过程中，熵总是趋向于越大的方向发展，即代码总是会朝着越来越混乱的状态发展，而这是我们不想要的情况。

如果我们希望降低软件熵，我们需要投入更多的能量，程序员需要用更多的准则，更高的标准去要求自己写出质量更高的代码。

但是现实时，很多新的程序员加入项目开发，反而使得项目越来越混乱，这就是软件熵增高的后果。有个犯罪学理论，叫做[破窗效应](https://zh.wikipedia.org/wiki/%E7%A0%B4%E7%AA%97%E6%95%88%E5%BA%94)。以一幢有少许破窗的建筑为例，如果那些窗没修理好，可能将会有破坏者破坏更多的窗户。最终他们甚至会闯入建筑内，如果发现无人居住，也许就在那里占领、定居或者纵火。又或想像一条人行道有些许纸屑，如果无人清理，不久后就会有更多垃圾，最终人们会视为理所当然地将垃圾顺手丢弃在地上。

![](http://p3alsaatj.bkt.clouddn.com/20180524104915_Shmamt_002WGJLDzy6L08i1nBY26&690.jpeg)

当你在写代码时，你要问自己：你的闯入建筑的破窗者，还是清洁工？

## 18.1. 变量是魔鬼，减少使用变量

**如果不是非常必要，不要定义变量，变量越多，出现问题的概率就越大。**

当你需要定义一个变量的时候，你要问自己：不定义这个变量行不行？

```
// bad
var endTime = moment().format('YYYY-MM-DD')
someFunction(endTime)

// good 
someFunction(moment().format('YYYY-MM-DD'))
```

**不要定义一些没用的中间变量**

```
// bad
var someShit = createShit()
return someShit

// good
return createShit()
```

## 18.2. 代码是魔鬼，减少使用代码

## 18.3. 把应用逻辑包裹到函数中

- 不要在事件订阅里写大段应用逻辑
- 不要在条件判断的内部写大段应用逻辑

写小而美的函数，包装应用逻辑。

# 19. 参考文献
- JavaScript高级程序设计(第3版) 【美】尼古拉斯·泽卡斯
- Maintainable JavaScript (英文版) Nicholas C. Zakas(其实和上边那本书应该是同一个人)
- JavaScript忍者秘籍 John Resig / Bear Bibeault （John Resig 大名鼎鼎jQuery的创造者）
- [百度前端研发部 文档与源码编写风格](https://github.com/fex-team/styleguide)
- [JavaScript SDK Design Guide: JavaScript-sdk设计指南](https://github.com/hueitan/javascript-sdk-design)