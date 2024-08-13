# js基础

## 注释

1. 单行注释“//”，快捷键：<mark>Ctrl+/</mark>

2. 多行注释“/**/”,快捷键：<mark>Ctrl+Alt+A</mark>

## 输入输出语法

> alert()和 prompt() 它们会跳过页面渲染先被执行

### 输入语法

1. document.write("要输出的内容")

作用：向body标签内输出内容，<u>引号内可写标签且能被正常解析为标签</u>

2. alert("弹出内容")

作用：页面弹出警告对话框

3. console.log("控制台打印输出")

作用：控制台输出语法，用于调试使用

### 输入语法

* prompt(“弹出框的提示”)

作用：弹出一个对话框，包括提示和一个input框

## 声明多个变量

例：let a=1,b=2;

上面的方法好处是少写了一个let，但<mark>不推荐</mark>，<u>降低了代码可读性</u>

## 交换两个变量的值

1. 声明一个temp值来充当交换的中介（方法很简单，不做赘述）

2. 使用解构赋值法交换

```
let a = 1;
let b = 2; // 这里的分号不能省略
[a, b] = [b, a];
```

## 变量命名规则与规范

### 规则

1. 不能用关键词，例如：let、var、if、for等

2. 只能用下划线、字母、数字、\$组成，且数字不能开头。注：<mark>除了“_”和“\$”外的其它符号都不能参与变量名的组成。</mark>

3. 字母严格<mark>区分大小写</mark>

### 规范

1. 起名有意义（如英文）

2.  遵守小驼峰命名法，第一个单词首字母小写，后面每个单词首字母大写，如：userLoginService

## let 和 var的区别

> var常出现在一些老版本的项目中
> let的出现是为了解决var存在的问题

* var的不合理之处

1. var 可以先使用再声明

2. var声明过的变量可以重复声明

3. 比如变量提升、全局变量、没有块级作用域等等

## 数据类型

### 字符串

模版字符串
```
let age = 18;
document.write(`我今年${age}岁了`)
```

### 空类型

null
官方解释：把null作为尚未创建的对象

```
const obj = null;
typeof(obj) //object
```

### typeof 

typeof是一个可以检测数据类型的方法
1. 作为运算符：typeof x
2. 函数形式： typeof(x)

## 数据转换

### 隐式转换

+号旁边只要有一个字符串，结果就会转换成字符串

-号和乘除及其他运算符则不同，只要有数值和字符串数值，则会把字符串数值转换成数值（空字符串和null会转换成0），结果返回数值

+号可以作为正号将字符串数值转换为数值
如`console.log(typeof +"123") \\number`

### 显式转换

#### 转换为数字型

* Number(数据)  转换为数字型（不符合转换条件的返回NaN）
如：
```
Number("123") //123
Number("123px") //NaN
```
* parseInt(数据) 只保留整数
如：
```
parseInt("123") //123
parseInt("123px") //123
parseInt("123.99px") //123.99
parseInt("abc123px") //NaN
```
* parseFloat(数据) 
如：
```
parseFloat("123.123px") //123.123
parseFloat("abc123px") //NaN
```
#### 转换为布尔型
语法：`Boolean(data)`

## 分支语句

if、while、for循环里如果只有一行代码，则可以省略大括号，如：
```
if(true) console.log("示例");
```

### if语句

pass

### 三元运算符

pass

### switch语句

语法：
```
switch(data){
    case value1:
        代码1
        break
    case value2:
        代码2
        break
    case value3：
        代码3
        break
    defult:
        console.log("没有符合条件的")
}
```

switch判断值和===类似

如果case里面的语句没有break，则会向下穿透，直到遇到break，如果没有break则执行完所有代码


## for循环

语法：
```
for(let i =1; i<3; i++){
    //循环语句
}
```

退出循环：continue和break（具体区别自查）

特别的，如果出现下述代码，程序不会报错，会进入无限循环，和while(true){}类似
```
for(;;){
    //循环语句
}
```

额外补充一个for…in…语法（这个方法不建议遍历数组，可以遍历对象使用，后面会讲）
```
let arr = ["你","我","他"]
for(let i in arr){
    console.log(i) //这里打印出来的是数组中正在遍历的元素的索引值（该索引值是字符串数值）
    console.log(arr[i]) //这里打印出来的是正在遍历的数组的元素
}
//最后的输出
/*
0
你
1
我
2
他
*/
```

## 数组

### 声明

1. 使用字面量声明：let array = [1,2,3],
2. 使用构造函数：let array = new Array(1,2,3)

### 添加元素

1. 语法：arr.push()
push语法是向数组末尾添加元素并<u>返回该数组的新长度</u>，可以添加多个元素

2. 语法：arr.unshift()
unshit是向数组开头添加元素，<u>返回该数组的新长度</u>，可以添加多个元素

### 删除元素

1. 语法：arr.pop()
删除数组中最后一个元素，并<u>返回删除的那个元素的值</u>

2. 语法：arr.shift()
删除数组中第一个元素，并<u>返回删除的那个元素的值</u>

3. 语法：arr.splice(start, deleteCount, item1, item2, /* …, */ itemN)

* start：从 0 开始计算的索引，表示要开始改变数组的位置，它会被转换成整数。
> 如果start是负数且超出arr的范围，则start为0
> 如果start是正数且超出arr的范围，则不会删除任何元素，但是该方法会表现为添加元素的函数，添加所提供的那些元素到末尾
> 如果 start 被省略了（即调用 splice() 时不传递参数），则不会删除任何元素。这与传递 undefined 不同，后者会被转换为 0

* deleteCount（可选）：一个整数，表示数组中要从 start 开始删除的元素数量。
> 如果省略了 deleteCount，或者其值大于或等于由 start 指定的位置到数组末尾的元素数量，那么从 start 到数组末尾的所有元素将被删除。
> 如果 deleteCount 是 0 或者负数，则不会移除任何元素。undefined会转换成0

* item1、…、itemN（可选）：从 start 开始要加入到数组中的元素
> 如果不指定任何元素，splice() 将只从数组中删除元素

### 排序

语法：arr.sort(compareFn)
compareFn（可选）：自定义的一个函数的函数名，如果省略该函数，数组元素会被转换为字符串，然后根据每个字符的 Unicode 码位值进行排序。

注：<mark>sort方法会改变原数组</mark>

tip：保持原数组不变的方法
```
const numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5];
const sortedNumbers = [...numbers].sort();

console.log(numbers); // 输出: [3, 1, 4, 1, 5, 9, 2, 6, 5]
console.log(sortedNumbers); // 输出: [1, 1, 2, 3, 4, 5, 5, 6, 9]
```

##  函数

* 重复定义相同函数名的函数，后面定义的函数会覆盖前面定义的，和调用的位置无关，如：
```
function fn(){
    console.log(1);
}
fn() //输出2
function fn(){
    console.log(2);
}
```
* 实参的个数和形参个数可以不一样（不建议），如果形参过多，会自动填上undefined，如果实参过多，多余的实参会被忽略

函数内部有一个arguments，里面装着所有的实参
```
function fn(){
    console.log(arguments[2])
}
fn(1,2,34) //输出34
```

### 作用域

如果函数内部，变量没有声明，直接赋值，也当<mark>全局变量</mark>看，但是强烈不推荐，如：
```
function fn(){
    num = 10;
}
console.log(num) //输出10
```

> 作用域分为<u>函数作用域</u>和<u>块作用域</u>，块作用域是指被{}包围的函数块，如if、for下面的函数
> 块作用域是<mark>有可能</mark>被外面访问到的，这取决于声明的方式
> 如果用var声明，则块作用域变量可以被外面访问，用let和const则不会被访问到

### 匿名函数

<u>匿名函数不可以在声明前调用，具名函数可以</u>

定义方法（其一）：
```
function(){}
```

调用方法两种：

1. 函数表达式
将函数赋值给一个变量
`let fn = function(){}` 
调用可以直接当变量使用
`console.log(fn)`

或者`fn()`，里面可以带参数

2. 立即执行函数

场景介绍：避免全局变量之间的污染

```
//方式一
(function (){console.log(1)})();
//方式二
(function(){console.log(1)}());
//不需要调用，立即执行
//可以填写实参、形参，此处不多赘述
```

常见的写法主要是方式一，但是在日常中，往往也会有一下写法
`!function(){}()`||`+function(){}()`||`~function(){}()`（其中加感叹号的最多）
这些方法都是通过在function(){}前加算术表达式的方法省略包裹在匿名函数外的括号
甚至在一些写法中会见到`!(function(){})()`的写法，这个感叹号没有实际作用，加不加都可以

立即执行函数前面或后面一定要加分号
```
(function fn(){})();
或者
;(function fn(){})()
```


### 函数提升

```
fn() // 成功运行
function fn(){
    console.log("函数提升")
}
```
特殊的：
```
fn() // TypeError:fn is not a function!
var fn = function(){
    console.log("函数表达式不存在提升")
}
```
注意：函数提升和变量提升类似，都是仅提升到<mark>当前作用域</mark>的最前面

### 函数参数

#### 动态参数

arguments是函数内部内置的伪数组变量（只存在函数当中，<mark>箭头函数中不存在argument</mark>），它包含了调用函数时传入的所有实参
```
function fn(){
    console.log(arguments)
}
fn(1,2,3) // 伪数组：[1,2,3]
```

#### 剩余参数

剩余参数允许我们将一个不定数量的参数表示为一个数组
```
function fn(...other){
    console.log(other)
}
fn(1,2,3) // 真数组：[1,2,3]
```

### 箭头函数

目的：引入箭头函数的目的是更简短的函数写法并且不绑定this，箭头函数的语法比函数表达式更简洁
使用场景：箭头函数更适用于那些本来需要匿名函数的地方
语法：
```
const fn=()=>{
    console.log("我是箭头函数")
}
fn()
```
箭头函数有很多特点，这里就写几个我之前不知道的
当箭头函数里的内容只有一行时，可以不用写return，如：
```
const fn=(x,y)=> x+y
fn(1,2) // 3
```

箭头函数可以直接返回一个对象，例：
```
const fn=(uname)=> ({name:uname}) // 对象外面的小括号可以省略
fn("某宝")
```

### 箭头函数的this

箭头函数不会创建自己的this，它只会从自己的作用域链的上一层沿用this
DOM事件回调函数为了简便，还是不太推荐使用箭头函数


## 逻辑中断

```
function(x,y){
    let x = x || 0
    let y = y || 0
    return x+y
}
```
| 符号 |     短路条件      |
| :--: | :--------------: |
|  &&  | 左边为false就短路 |
| \|\| | 左边为true就短路  |

## 对象

* 对象的健名字最好不要叫name，容易冲突
* 对象没有length属性

声明对象的方法
```
let 对象名 = {};
let 对象名 = new Object(); // 里面可以写一个对象如：new Object({name:'你好'})
```
> 对象的健值可以加引号，也可以不加，通常省略，除非名称有特殊符号，如：空格、中横线等

### 增删改

`对象名.属性名 = 新的值`这样就可以改某个属性的值
如果该对象中没有那个属性，则会把这个属性加进去，这就是对象增加的方法

这个删除的方法做一个了解，最新的语法中是<mark>不允许</mark>使用这个的
`delete 对象名.属性名`

### 查

`对象名.属性名`这种方法可以查该属性的值

如果属性名有特殊符号，上面的方法往往会报错，则应该使用下面的方法

`对象名['属性名']`使用这种方法，中括号里面的属性名要加引号

### 对象中方法使用示例

```
let obj = {
    add: function (x,y){
        return x + y
    }
}
console.log(obj.add(1,2)) //3
```

### 遍历对象

使用for…in…方法
```
let obj = {  
    id:0,
    student:"小明"
}

for(let k in obj){
    console.log(k) //这里会打印出obj里面的属性名，String
    console.log(obj[k]) //这里会打印出k属性的value
}
```

### 内置对象

定义：JavaScript内部提供的对象，包括各种属性和方法给开发者调用
如：console.log()，document.write()都是内置对象里的方法
下面着重讲的是Math内置对象

### Math

* Math对象包含的方法有：

> random：生成0~1之间的随机数（包括0，不包括1）
> cell：向上取整
> floor：向下取整
> max：找最大数
> min：找最小数
> pow：幂运算
> abs：绝对值

[全部Math的方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math)

# Web API

## DOM

定义：DOM（Document Object Model——文档对象模型）是用来呈现以及与任意HTML或XML文档交互的API
简单讲就是：DOM是浏览器提供的一套专门用来操作<mark>网页内容</mark>的功能

### DOM树

以下是DOM树的例图：
![u=1222456862,309964943&fm=253&fmt=auto&app=138&f=PNG?w=818&h=451](vx_images/321804501246839 "DOM树")

### DOM对象

浏览器根据HTML标签生成的<u>JS对象</u>
> 所有的标签属性都可以在这个对象上面找到
>修改这个对象的属性会自动映射到标签上

* document对象
> 是最大的DOM对象
> 网页所有内容都在document里面

### 获取DOM元素

#### 根据css选择器来获取DOM元素

1. 选择匹配的第一个元素
语法：`document.querySelector('css选择器')`
注：匹配到返回一个HTMLElement对象，可以直接修改，如果没有匹配到，返回null
修改示例：
```
<body>
    <div>123</div>
</body>
<script>
    const div = document.querySelector('div')
    div.style.color = "red"
</script>
```

2. 选择匹配的多个元素
语法：`document.querySelectorAll('css选择器')`
注：匹配到返回一个NodeList对象集合（只要用的这种方法，哪怕匹配的只有一个，得到的也是NodeList），与前者不同，它不能直接修改。

* 这种方法得到的是一个<u>伪数组</u>
> 有length属性，也有索引号
> 但是没有pop() push()等数组方法
想要得到里面的每一个对象，则需要通过遍历（for）的方式获得，例：
```
<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
</body>
<script>
    const li = document.querySelector('ul li')
    for (let i = 0; i < li.length; i++) {
        console.log(li[i]) //这个li[i]和前面的HTMLElement一样，可以直接操作
    }
</script>
```

#### 其他获取DOM元素方法

根据id获取一个元素
`document.getElementById('id值')`

根据标签获取一类元素，如：获取页面所有的div
`document.getElementByTagName('div')`

根据类名获取元素
`document.getElementByClassName('类名')`

> 了解就行，现在用的少了

### 修改DOM元素

#### 操作元素常用属性
1. 修改innerText属性
这个属性显示纯文本，不解析标签

2. 修改innerHTML属性
这个属性可以解析标签，多标签建议使用模板字符

3. 其他属性
如：src，href，title等

#### 操作元素样式属性

1. 通过style属性修改
```
const box = document.querySelector(".box");
box.style.width = '300px' //这里的width可以切换成其他css属性，300px一定要带单位
box.style.backgroundColor = 'hotpink' //这里写background-color会报错，要用小驼峰命名法
```

2. 修改DOM元素类名

（1）通过className属性修改类名
对DOM元素的className属性修改，可以修改这个元素的类名

使用这种方法修改类名后，新修改的类名会<mark>覆盖原来的类名</mark>

（2）通过classList属性下的方法修改类名
`DOM对象.classList.add("newClassName") //添加这个类名`
 这里的添加类名就相当于直接将原来的类名修改为`"原来的类名 newClassName"`
 
`DOM对象.classList.remove("oldClassName") //删除这个类名`
`DOM对象.classList.toggle("className") //有这个类名就删掉，没有就加上`

#### 操作表单元素属性

表单内的内容是value属性（如：input标签），innerHTML是那不到内容的
修改表单类型是修改type属性，如：利用js将type从password修改为text就可以实现查看密码的功能

部分属性的值用布尔值表示，如：selected、disabled、checked

#### 自定义属性

格式：`data-自定义属性名`
省略data-也可以，但是不建议，而且我不知道省略后怎么写，所以了解就行了

如何获取到自定义属性的值：
`DOM元素.dataset.自定义属性名`

## 定时器

1. 开启定时器
`setInterval(函数,间隔时间)`（时间单位是毫秒）
>  函数可以直接在里面定义，如：`setInterval(function(){},1000)`
>也可以调用已经定义的函数，如：
```
function fn(){
    console.log("nihk")
}
setInterval(fn,1000) //这里的函数fn后面不能跟小括号
```
>一种极为少见的可以加小括号的写法：`setInterval("fn()",1000)`（了解即可）

注：开启定时器后函数<mark>不是立即调用</mark>，而是等定义的时间过了后才开始第一次调用

2. 给定时器编号
一般情况下使用`let timmer = setInterval(fn,1000)`的方式
这里的let不能换成const，因为定时器的序号可能会发生改变（比如关开定时器就会使序号发生改变），可以使用log打印出来timmer的值，是一个数字。每一个定时器的序号都是独一无二的。

3. 关闭定时器
`clearInterval(timmer) //这个timmer是前面let定时器的变量名`

## 事件监听

### addEventListener
语法：`DOM元素.addEventListener("事件类型",function(){},useCapture)`
> 事件监听三要素：
> 事件源：哪个DOM元素被事件触发了，要获取DOM元素
> 事件类型：用什么方式触发，比如鼠标单击click，鼠标经过mouseover等
> 事件调用的函数：要做什么事

* 相较于on事件，addEventListener方法可以给同一个元素重复创建同一种事件且不会覆盖，都会生效
* useCapture接受一个布尔值，默认是false，表示是否开启事件捕获（部分浏览器不支持捕获，如：IE）

### on方法监听
使用on方法进行事件监听
语法：`DOM元素.on事件类型 = function(){}`

这种方法是比较老的方法，存在许多缺陷：

当对同一个DOM元素多次使用on方法监听时，后面定义的on事件会覆盖前面的，导致前面的事件失效
这种方法<mark>只有冒泡，没有捕获</mark>

### 事件类型及回调事件对象
对于上面的事件类型，可以查看[MDN官网](https://developer.mozilla.org/zh-CN/docs/Web/Events)
其中，常用的事件有：click、mouseenter、mouseleaver、focus、blur、keydown、keyup、input

> mouseover和mouseout会有冒泡效果
> mouseenter和mouseleave没有冒泡效果（推荐）

* 回调事件对象：事件监听中接收的参数event
里面常用的属性有：
type：当前的事件类型
clientX / clientY：获取光标相对于浏览器可见窗口左上角的位置
offsetX / offsetY：获取光标相对于当前DOM元素左上角的位置
key：用户按下的键盘的值 //现在不提倡使用keyCode（老版本浏览器考虑兼容性）

## 环境对象

环境对象指的是函数内部特殊的变量<mark>this</mark>，它代表着当前函数运行时所处的环境

this指向的是函数的调用者，如：`window.fn()`指向window，事件监听回调函数指向调用它的DOM元素

## 回调函数

如果将函数A作为参数传递给函数B时，我们称函数A为<u>回调函数</u>

## 事件流

### 事件流与两个阶段说明

<u>事件流</u>指的是事件完整执行过程中的流动路径


![事件流图片](vx_images/248603110240642.jpg)

* 实际工作都是使用事件冒泡为主

### 阻止冒泡

语法：`事件对象.stopPropagation()`，例：
```
son.addEventListener("click",function (e){
    console.log("Hello")
    e.stopPropagation()
}) //on方法也类似
```

此方法可以阻断事件流动传播，不光在冒泡阶段有效，捕获阶段也有效


### 解绑事件

on事件解绑直接将其赋值为null即可，例：
`son.onclick = null`

addEventListener方法移除事件要用removeEventListener函数解绑，例：
`son.removeEventListener("click",fn) //匿名函数无法被解绑`

### 事件委托

* 优点：减少注册次数，可以提高程序性能
* 原理：事件委托其实是利用事件冒泡的特点。

给父元素注册事件，当我们触发子元素的时候，会冒泡到父元素身上，从而触发父元素的事件

实现方法：[event.target](https://developer.mozilla.org/zh-CN/docs/Web/API/Event/target)
```
father.addEventListener("click",function(e){
    console.log(e.target) //这个e.target就是点击的子元素
    const son = e.target
    son.style.color = "red" //这里可以向操作DOM元素一样对其操作
})
```
注意：如果子元素里有孙子元素，那么在孙子元素里触发的事件，父元素的event.target返回的是孙子元素


### 阻止元素默认行为

方法：`event.preventDefault()`
如：
```
const form = document.querySeIector('form'）
form.addEventListener('submit'function(e){
    e·preventDefau1t() //阻止form表单默认的提交事件
})
```

## 日期对象


1. 实例化
`const date = new Date()`
下面提供一种Date()里面接受参数的格式
`new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]])`
Date里可以接受一个指定的日期作为指定实例化的日期，详细格式及方法参考[Date](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)

2. 时间戳

伦敦时间从1970年1月1日0点0分0秒0毫秒开始的毫秒数

计算倒计时的效果时都是使用时间戳

> 三种获取时间戳的方法
> 
> 1. getTime()方法
> ```
> const date = new Date()
> console.log(date.getTime())
> ```
> 
> 2. +new Date()
> `cnosole.log(+new Date()) //利用隐式转换，加号作为正号会倾向于把字符串转换为数值`
> 
> 3. Date.now()
> `console.log(Date.now()) //无需实例化，但是只能获取当前的时间戳，前面两种方法可以获取指定时间的时间戳`

## 节点操作

DOM树里每一个内容都称之为节点
节点类型：元素节点（如body、div等，html是根节点）、属性节点（如：class、href等）、文本节点（所有的文本）、其他。

### 查找节点

查找父元素节点：
语法：`子元素.parentNode`，找不到则返回null
示例：
```
const baby = document.querySelector('.baby')
console.log(baby)//返回DOM对象
console.log(baby.parentNode)//返回baby的父元素DOM对象，如果想操作祖父元素，可以叠加parentNode，如：baby.parentNode.parentNode
```

查找子元素节点：

* childNodes：获取所有子节点、包括文本节点（空格、换行）、注释节点

* children：仅获取所有元素节点，返回的还是一个伪数组

两个的使用方法和上面的parentNode类似，<mark>一般都使用children</mark>


查找兄弟节点：

* nextElementSibling：下一个兄弟节点

* previousElementSibling：上一个兄弟节点

### 新增节点

* 创建节点：`document.createElement('标签名')`

* 追加节点：`父元素.appendChild(要插入的元素)`，创建的节点想要在界面看到还要插入某个父元素中，这个方法是插入到父元素的<u>最后</u>。下面这个方法则可以实现插入<u>某个元素的前面</u>，`父元素.insertBefore(要插入的元素,在哪个元素前面)`

> 与appendChild相似的方法还有append方法：`父元素.append(要插入的元素)`，它也是插入到父元素的最后，他们两者的区别是
> 
> * `Element.append()` 允许附加字符串对象（被插入的字符串对象等价为 [Text](https://developer.mozilla.org/zh-CN/docs/Web/API/Text) 节点），而 `Node.appendChild()` 只接受 [Node](https://developer.mozilla.org/zh-CN/docs/Web/API/Node) 对象。
> * `Element.append()` 没有返回值，而 `Node.appendChild()` 返回附加的 [Node](https://developer.mozilla.org/zh-CN/docs/Web/API/Node) 对象。
> * `Element.append()` 可以附加多个节点和字符串（`append(param1, param2, /* …, */ paramN)`），而 `Node.appendChild()` 只能附加一个节点。

使用示例：
```
const ul = document.querySelector("ul") //选择ul元素
const li = document.createElement("li") //创建li元素，这里的创建的元素名称可以自定义，即使没有这个标签，也能创建，比如写ab，创建后可以得到<ab></ab>

ul.insertBefore(li,ul.children[0]) //将创建的li元素插入到选中的ul元素中，插入位置在ul元素的第一子元素前面
```

### 克隆节点

语法：`元素.coloneNode(布尔值)`

> cloneNode会克隆出一个跟原标签一样的元素，括号内传入布尔值
> 若为true,则代表克隆时会包含后代节点一起克隆
> 若为false,则代表克隆时不包含后代节点
> 默认为false


### 删除节点

语法：`父元素.removeChild(要删除的元素)`

在JavaScript原生DOM操作中，要删除元素<mark>必须通过父元素删除</mark>

注：如果不存在父子关系则删除不成功

> 这里补充一个`Element.remove()` 方法（romove方法和removeChild有略微不同），把对象从它所属的 DOM 树中删除。
> ```
> <-- html代码 -- >
> <div id="div-01">Here is div-01</div>
> <div id="div-02">Here is div-02</div>
> <div id="div-03">Here is div-03</div>
> ```
> ```
> // js代码
> var el = document.getElementById("div-02");
> el.remove();
> // id 为 'div-02' 的 div 被删掉了
> ```

## M端事件

M端是指移动端
这里以touch事件为例

| 触碰touch事件 |            说明             |
| :-----------: | :-------------------------: |
|  touchstart   |   手指摸到一个DOM元素时触发   |
|   touchmove   | 手指在一个DOM元素上滑动时触发 |
|   touchend    | 手指从一个DOM元素上移开时触发 |


## Window对象

## BOM（浏览器对象模型）

BOM（Browser Object Model）

![](vx_images/286142317240645)


> window对象是一个全局对象，也可以说是javascript中的顶级对象
> 像document、alert()、console.log()这些都是window的属性，基本BOM的属性和方法都是window的。
> 所有通过var定义在全局作用域中的变量、函数都会变成window对象的属性和方法
> window对象下的属性和方法调用的时候可以省略window

## 延时函数

语法：
```
let timmer = setTimeout(回调函数,等待的毫秒数); //创建延时函数
clearTimerout(timer) //清除延时函数
```
相较于setInterval，setTimeout只执行一次

## location对象

[location](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/location)的数据类型是对象，它拆分并保存了URL地址的各个组成部分
常用的属性：

* href
location.href可以获取当前的网页链接，这个href是可以修改的，可以通过修改这个的方式在js上实现页面跳转

* search
search属性获取地址中携带的参数，location.search返回一个字符串，字符串包括问号和后面的所有内容

* hash
hash获取地址中的哈希值（经常用于不刷新页面显示不同页面）

* reload()
reload方法用来刷新当前页面，传入参数true时表示强制刷新

## navigator对象

[Navigator](https://developer.mozilla.org/zh-CN/docs/Web/API/Navigator)下的userAgent属性可以判断IOS/Android还是PC端

## history对象

[history](https://developer.mozilla.org/zh-CN/docs/Web/API/History)的数据类型是对象，主要管理历史记录，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等

| history对象方法 |                                                                                                                                                                                作用                                                                                                                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| back()          | 页面后退                                                                                                                                                                                                                                                                                                                                                            |
| forward()       | 页面前进                                                                                                                                                                                                                                                                                                                                                            |
| go(num)         | 通过当前页面的相对位置从浏览器历史记录（会话记录）异步加载页面。比如：参数为 -1 的时候为上一页，参数为 1 的时候为下一页。当你指定了一个越界值（例如：当会话历史记录中没有之前访问的页面时，则传参的值为 -1，那么这个方法没有任何效果也不会报错。调用没有参数的 go() 方法或者参数值为 0 时，重新载入当前页面。Internet Explorer 允许你指定一个字符串，而不是整数，以转到历史记录列表中的特定 URL。 |

## localStorage

[localStorage](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/localStorage)

储存方式：`localStorage.setItem("key","value") // 这种方式只能储存字符串`
获取方式：`localStorage.getItem("key")`
删除键值：`localStorage.removeItem("key")`

因为这种方式只能存储字符串，所以，存储复杂数据源类型时需要将复杂数据类型转换成JSON字符串，再存储到本地
转换语法：`JSON.stringify(复杂数据类型)`
转回语法：`JSON.parse(json字符串)`

实际使用8示例：
```
const obj = {
    hello:"world"
}

localStroage.setItem("key",JSON.stringify(obj)) //如果不转换，存储进去的会是[object object]

JSON.parse(localStorage.getItem("obj")) //拿到存储对象并转换为对象
```

## map() 和 join()

### [map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
arr.map(callbackFn, thisArg)
> callbackFn为数组中的每个元素执行的函数。它的返回值作为一个元素被添加为新数组中。该函数被调用时将传入以下参数：
> >element
> >数组中当前正在处理的元素。
> >index
> >正在处理的元素在数组中的索引。
> >array
> >调用了 map() 的数组本身。
> 
> thisArg（可选）
> 执行 callbackFn 时用作 this 的值。参见迭代方法。

`map()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它为数组中的每个元素调用一次提供的 `callbackFn` 函数，并用结果构建一个新数组。

`callbackFn` 仅在已分配值的数组索引处被调用。它不会在[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)中的空槽处被调用。

`map()` 方法是一个[复制方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E5%A4%8D%E5%88%B6%E6%96%B9%E6%B3%95%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%95)。它不会改变 `this`。然而，作为 `callbackFn` 提供的函数可以更改数组。请注意，在第一次调用 `callbackFn` *之前*，数组的长度已经被保存。因此：

*   当开始调用 `map()` 时，`callbackFn` 将不会访问超出数组初始长度的任何元素。
*   对已访问索引的更改不会导致再次在这些元素上调用 `callbackFn`。
*   如果数组中一个现有的、尚未访问的元素被 `callbackFn` 更改，则它传递给 `callbackFn` 的值将是该元素被修改后的值。被[删除](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/delete)的元素则不会被访问。

> 注意：在map方法回调函数中return后面可以写加减运算，但不能写比较运算符（如：>、<等），如果写了则返回的是true或者false

### [join](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

arr.join(separator)
> separator 可选
> 指定一个字符串来分隔数组的每个元素。如果需要，将分隔符转换为字符串。如果省略，数组元素用逗号（,）分隔。如果 separator 是空字符串（""），则所有元素之间都没有任何字符。

所有数组元素被转换成字符串并连接到一个字符串中。如果一个元素是 `undefined` 或 `null`，它将被转换为空字符串，而不是字符串 `"undefined"` 或 `"null"`。

[`Array.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) 会在内部访问 `join` 方法，不带参数。覆盖一个数组实例的 `join` 也将覆盖它的 `toString` 行为。

当在[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)上使用时，`join()` 方法迭代空槽，就像它们的值为 `undefined` 一样。

`join()` 方法是[通用的](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E9%80%9A%E7%94%A8%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95)。它只期望 `this` 值具有 `length` 属性和整数键属性。


## 正则表达式

[Regular_expressions](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_expressions)
定义正则表达式语法：`const 变量名 = /表达式/`，其中//是正则表达式字面量

下面是官网扒下来的可以使用正则表达式的方法
<table>
  <thead>
    <tr>
      <th>方法</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec"><code>exec</code></a></td>
      <td>一个在字符串中执行查找匹配的 RegExp 方法，它返回一个数组（未匹配到则返回 null）。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test"><code>test</code></a></td>
      <td>一个在字符串中测试是否匹配的 RegExp 方法，它返回 true 或 false。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/match"><code>match</code></a></td>
      <td>一个在字符串中执行查找匹配的 String 方法，它返回一个数组，在未匹配到时会返回 null。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll"><code>matchAll</code></a></td>
      <td>一个在字符串中执行查找所有匹配的 String 方法，它返回一个迭代器（iterator）。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/search"><code>search</code></a></td>
      <td>一个在字符串中测试匹配的 String 方法，它返回匹配到的位置索引，或者在失败时返回 -1。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace"><code>replace</code></a></td>
      <td>一个在字符串中执行查找匹配的 String 方法，并且使用替换字符串替换掉匹配到的子字符串。</td>
    </tr>
    <tr>
      <td><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split"><code>split</code></a></td>
      <td>一个使用正则表达式或者一个固定字符串分隔一个字符串，并将分隔后的子字符串存储到数组中的 <code>String</code> 方法。</td>
    </tr>
  </tbody>
</table>

### 元字符

单个数字和字符的元字符
       .           匹配单个的任意字符
        [范围]   	匹配单个范围内的字符
        [0-9]
        [a-zA-Z0-9_]匹配单个的数字、字母下划线
        [^范围]         匹配任意一个除括号范围内的字符
        [^0-9]      匹配任意一个非数字字符
        \w          匹配单个的数字、字母下划线(同上)
        \W          匹配单个非数字、字母下划线
        \d          匹配单个数字，等价于[0-9]
        \D          匹配单个非数字，等价于[^0-9]

重复字符    x(任意的单个字符)
        x?      匹配0个或者1个x
        x+      匹配至少一个x字符
        x*      匹配任意个x字符
        x{m,n}  匹配至少m个，最多n个字符，包括n
        x{n}    必须匹配n个字符
        (xyz)+  小括号括起来的部分是当作单个字符处理

空白字符     
        \s      匹配任意单个的空白字符
        \S      匹配任意单个非空白字符

锚字符
        ^       行首匹配    必须以这个正则开头
        $       行尾匹配    必须以这个正则结尾

替代字符
        |   
        
转义字符
            \.      代表本来.的意思
            \*      代表本来*的意思
            
# JS进阶

## 垃圾回收机制

内存的生命周期：

1. 内存分配：当我们声明变量、函数、对象的时候，系统会自动为他们分配内存
2. 内存使用：即读写内存，也就是使用变量、函数等
3. 内存回收：使用完毕，由垃圾回收器自动回收不再使用的内存

说明：
全局变量一般不会回收（关闭页面回收）
一般情况下局部变量的值，不用了，就会被自动回收掉

* 内存泄漏：程序中分配的内存由于某种原因程序未释放或无法释放叫做内存泄漏

* 算法说明

堆栈空间分配区别：

1. 栈（操作系统）：由操作系统自动分配释放函数的参数值、局部变量等，基本数据类型放到栈里面。
2. 堆（操作系统）：一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。复杂数据类型放到堆里面。

下面介绍两种常见的浏览器垃圾回收算法：<mark>引用计数法</mark>和<mark>标记清除法</mark>

* <mark>引用计数</mark>
|E采用的引用计数算法，定义“内存不再使用"，就是看一个对象是否有指向它的引用，没有引用了就回收对象

算法：

1. 跟踪记录被引用的次数
2. 如果被引用了一次，那么就记录次数1，多次引用会累加++
3. 如果减少一个引用就减1--
4. 如果引用次数是0，则释放内存
   
这种方法存在一个致命的问题：嵌套引用（循环引用）
如果两个对象相互引用，尽管他们已不再使用，垃圾回收器不会进行回收，导致内存泄露。
如：
```
function fn(){
    let a = {};
    let b = {};
    a.c = b;
    b.c = a;
    return "一般函数执行完毕后局部变量会被回收，但这里相互调用，引用次数不为零，造成内存泄漏"
}
fn()
```

* <mark>标记清除法</mark>

现代的浏览器已经不再使用引用计数算法了。
现代浏览器通用的大多是基于标记清除算法的某些改进算法，总体思想都是一致的。

核心：

1. 标记清除算法将“不再使用的对象"定义为"无法达到的对象"
2. 就是从根部（在js中就是全局对象）出发定时扫描内存中的对象。凡是能从根部到达的对象，都是还需要使用的。
3. 那些无法由根部出发触及到的对象被标记为不再使用，稍后进行回收。

## 闭包（closure）

闭包是一种特殊的作用域，能够让内部函数访问其所在外部函数作用域中的变量，即使外部函数已经执行完毕。简单来说，闭包就是函数和其词法环境的组合。
例：
```
function a(){
    const num = 1;
    function b(){
        console.log(num) // 这里就涉及了闭包，因为在b函数中访问了a函数中的变量
    }
}
```
除了访问上级函数的变量，访问上级函数的形参也可以形成闭包
```
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log('outerVariable:', outerVariable);
        console.log('innerVariable:', innerVariable);
    };
}

const newFunction = outerFunction('outside');
newFunction('inside'); // 输出: outerVariable: outside, innerVariable: inside
```
闭包的特点：

1. 数据封装：闭包允许你封装变量，避免全局污染。
2. 状态维持：可以让变量的值在函数调用之间保持不变。
3. 实现私有变量：在JavaScript中，通过闭包可以模拟实现类的私有成员。

应用示例：
```
function counter() {
    let count = 0;
    return function() {
        return ++count;
    };
}

const myCounter = counter();
console.log(myCounter()); // 输出: 1
console.log(myCounter()); // 输出: 2

// 如果count是定义在全局中，那么每运行一次函数count都会被重置
// const count = 0;
// function counter(){
//     console.log(count++)
// }
// console.log(counter()) // 1
// console.log(counter()) // 1
```

私有变量模拟：
```
function Person(name) {
    var _name = name; // 私有变量

    this.sayName = function() {
        console.log(_name);
    };
}

var person = new Person('Alice');
person.sayName(); // 输出: Alice
// 但无法直接访问_person，保护了私有变量
// 这种方法主要运用了全局访问不了局部变量的特点，同时又使局部变量不被释放，成为私有变量
```

* 闭包的缺点：
避免循环引用：特别是在使用闭包处理DOM事件或定时器时，注意不要造成函数与DOM元素之间的循环引用，这<mark>可能导致内存泄漏</mark>。

## 变量提升

```
console.log(num)
var num = 10
```
上面的例子打印出来的是undefined，如果声明num时使用let则会报错，因为num在打印的时候还并未被声明
之所以上述例子中打印出undefined，是因为var的变量提升，其效果类似：
```
var num
console.log(num)
num = 10 // 只提升声明，不提升定义
```
注：var声明产生的变量提升只会将变量提升到<mark>当前作用域</mark>的最前面

## 解构赋值

JavaScript中的结构赋值是一种允许你将数组或对象的属性解包到独立变量中的特性。这种赋值方式使得代码更加简洁、易读。结构赋值主要包括解构赋值（Destructuring Assignment）和展开操作符（Spread Operator）。下面我将分别对这两种方式进行详细讲解。

### 解构赋值 （Destructuring Assignment）

解构赋值可以用于数组和对象，让我们逐一来看：

#### 数组解构

在数组中，解构赋值让你可以直接将数组中的元素赋值给变量。

```javascript
let [a, b, c] = [1, 2, 3];
console.log(a); // 输出: 1
console.log(b); // 输出: 2
console.log(c); // 输出: 3
```

- 如果变量数量少于数组元素数量，多余的元素会被忽略。
- 反之，如果变量多于元素数量，额外的变量会被赋值为`undefined`。
- 你还可以在变量使用空位跳过某些元素。

#### 对象解构

对象解构允许你将对象的属性直接赋值给变量，匹配属性名即可。

```javascript
let { foo, bar } = { foo: 'hello', bar: 'world' };
console.log(foo); // 输出: hello
console.log(bar); // 输出: world
```

- 你可以使用不同的变量名接收属性值，通过冒号指定源属性名，例：

```javascript
let { foo:fooooo, bar } = { foo: 'hello', bar: 'world' };
console.log(fooooo); // 输出: hello
console.log(bar); // 输出: world
```

- 默认值可以在解构失败时提供一个默认的值给变量。
- 可以设置默认值来处理可能未定义的属性。

#### 解构的默认值

无论是数组还是对象解构，都可以为变量设置默认值，以防解构失败或值为`undefined`。

```javascript
// 数组解构默认值
let [x = 10] = []; // x = 10
console.log(x);

// 对象解构默认值
let { y = 20 } = {}; // y = 20
console.log(y);
```

### 展开操作符（Spread Operator）

展开操作符使用三个点（...）表示，它允许你将数组或对象的内容“展开”到另一个数组或对象中，或者在函数调用时作为参数列表。

#### 数组展开

```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = [...arr1, ...arr2]; // 结果: [1, 2, 3, 4, 5, 6]
```

```
// 数组开头的，特别是前面有语句的，一定注意要加分号
;[a,b] = [b,a]
```
#### 对象展开

```javascript
let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1, c: 3 }; // 结果: { a: 1, b: 2, c: 3 }
```

#### 函数参数展开

```javascript
function sum(x, y, z) {
  return x + y + z;
}

let numbers = [1, 2, 3];
console.log(sum(...numbers)); // 输出: 6
```

总结来说，结构赋值极大地提高了JavaScript代码的简洁性和可读性，尤其是在处理数组和对象时。通过解构赋值可以方便地提取数据，而展开操作符则提供了灵活的数据合并和传递方式。

## [forEach()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

语法和接受值与map()一样，区别是map()有返回值，forEach()没返回值
forEach()相较于 for循环遍历，主要的优势体现在遍历数组对象及其他复杂数组时更简单

`forEach()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它按索引升序地为数组中的每个元素调用一次提供的 `callbackFn` 函数。与 [`map()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map) 不同，`forEach()` 总是返回 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)，而且不能继续链式调用。其典型的用法是在链式调用的末尾执行某些操作。

`callbackFn` 仅对已赋值的数组索引调用。对于[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)中的空槽，它不会被调用。

`forEach()` 不会改变其调用的数组，但是，作为 `callbackFn` 的函数可以更改数组。请注意，在第一次调用 `callbackFn` *之前*，数组的长度已经被保存。因此：

*   当调用 `forEach()` 时，`callbackFn` 不会访问超出数组初始长度的任何元素。
*   已经访问过的索引的更改不会导致 `callbackFn` 再次调用它们。
*   如果 `callbackFn` 更改了数组中已经存在但尚未访问的元素，则传递给 `callbackFn` 的值将是在访问该元素时的值。已经被[删除](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/delete)的元素不会被访问。

## [filter()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

`filter()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它为数组中的每个元素调用提供的 `callbackFn` 函数一次，并构造一个由所有返回[真值](https://developer.mozilla.org/zh-CN/docs/Glossary/Truthy)的元素值组成的新数组。未通过 `callbackFn` 测试的数组元素不会包含在新数组中。

`callbackFn` 仅对已分配值的数组索引调用。它不会对[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)中的空槽调用。

`filter()` 方法是一个[复制方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E5%A4%8D%E5%88%B6%E6%96%B9%E6%B3%95%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%B9%E6%B3%95)。它不会改变 `this`，而是返回一个包含与原始数组相同的元素（其中某些元素已被过滤掉）的[浅拷贝](https://developer.mozilla.org/zh-CN/docs/Glossary/Shallow_copy)。但是，作为 `callbackFn` 的函数可以更改数组。请注意，在第一次调用 `callbackFn` *之前*，数组的长度已经被保存。因此：

*   当开始调用 `filter()` 时，`callbackFn` 将不会访问超出数组初始长度的任何元素。
*   对已访问索引的更改不会导致再次在这些元素上调用 `callbackFn`。
*   如果数组中一个现有的、尚未访问的元素被 `callbackFn` 更改，则它传递给 `callbackFn` 的值将是该元素被修改后的值。被[删除](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/delete)的元素则不会被访问。

> 注意：在filter的回调函数中的return后面不能写加减等用于计算的运算符，只能写比较运算符（如：>、<等），如果写了计算的运算符

## 构造函数

构造函数：是一种特殊的函数，主要用来初始化对象

构造函数中的this指的是实例对象

构造函数在技术上是常规函数。
不过有两个约定：

1. 它们的命名以大写字母开头。
2. 它们只能由"new"操作符来执行。

语法示例：
```
function Me(mname,mage){
    this.name = mname;
    this.age = mage
}
cosnt mobj = new Me("我","18")
console.log(mobj) // {"我","18"}
```

> 说明
> 1. 使用new关键字调用函数的行为被称为实例化
> 2. 实例化构造函数时没有参数时可以省略()
> 3. 构造函数内部无需写return，返回值即为新创建的对象
> 4. 构造函数内部的return返回的值无效，所以不要写return
> 5. new Object() new Date()也是实例化构造函数


### 内置构造函数

#### 内构造函数Object的静态方法

`Object.keys(obj)` 这个方法可以得到一个数组，数组内容是所有的属性值

`Object.values(obj)`  这个方法可以得到一个数组，数组内容是所有的键值


`Object.assign()` 用于将一个或多个源对象的所有可枚举的自有属性的值复制到目标对象中。这个方法会在目标对象上进行修改，并返回修改后的目标对象。它是一个<mark>浅拷贝</mark>操作。

* 基本语法
`Object.assign(target, source1, source2, ...);`
>   `target`：必需，接收新属性的对象，也就是被赋值的对象。
>   `source1, source2, ...`：可选，一个或多个要合并到目标对象中的源对象。
示例：

```
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const returnedTarget = Object.assign(target, source);

console.log(target); // 输出：{ a: 1, b: 3, c: 4 }
console.log(returnedTarget); // 输出：{ a: 1, b: 3, c: 4 }，与target相同，因为它是target本身
```

在这个例子中，`target`对象的`b`属性值被`source`对象中的`b`属性值覆盖了，并且`source`对象中的`c`属性被添加到了`target`对象中。

#### Array

##### reduce()

`reduce()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它按升序对数组中的所有元素运行一个“reducer”回调函数，并将它们累积到一个单一的值中。每次调用时，`callbackFn` 的返回值都作为 `accumulator` 参数传递到下一次调用中。`accumulator` 的最终值（也就是在数组的最后一次迭代中从 `callbackFn` 返回的值）将作为 `reduce()` 的返回值。

```
reduce(callbackFn)
reduce(callbackFn, initialValue)
```

[参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#%E5%8F%82%E6%95%B0)

> >[`callbackFn`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#callbackfn)
> >
> >为数组中每个元素执行的函数。其返回值将作为下一次调用 `callbackFn` 时的 `accumulator` 参数。对于最后一次调用，返回值将作为 `reduce()` 的返回值。该函数被调用时将传入以下参数：
> >
> >[`accumulator`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#accumulator)
> >
>> 上一次调用 `callbackFn` 的结果。在第一次调用时，如果指定了 `initialValue` 则为指定的值，否则为 `array[0]` 的值。
> >
>> [`currentValue`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#currentvalue)
> >
> >当前元素的值。在第一次调用时，如果指定了 `initialValue`，则为 `array[0]` 的值，否则为 `array[1]`。
> >
> >[`currentIndex`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#currentindex)
>> 
> >`currentValue` 在数组中的索引位置。在第一次调用时，如果指定了 `initialValue` 则为 `0`，否则为 `1`。
> >
> >[`array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#array)
> >
> >调用了 `reduce()` 的数组本身。
> 
> [`initialValue`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#initialvalue) （可选）
> 
> 第一次调用回调时初始化 `accumulator` 的值。如果指定了 `initialValue`，则 `callbackFn` 从数组中的第一个值作为 `currentValue` 开始执行。如果没有指定 `initialValue`，则 `accumulator` 初始化为数组中的第一个值，并且 `callbackFn` 从数组中的第二个值作为 `currentValue` 开始执行。在这种情况下，如果数组为空（没有第一个值可以作为 `accumulator` 返回），则会抛出错误。

##### find()

`find()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它按索引升序顺序为数组中的每个元素调用提供的 `callbackFn` 函数，直到 `callbackFn` 返回一个[真值](https://developer.mozilla.org/zh-CN/docs/Glossary/Truthy)。然后 `find()` 返回该元素并停止迭代数组。如果 `callbackFn` 从未返回真值，则 `find()` 返回 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。

`callbackFn` 被调用来处理数组的*每一个*索引，而不仅仅是那些有值的索引。在[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)中，未赋值的空槽与 `undefined` 表现相同。

`find()` 不会改变被调用的数组，但是提供给 `callbackFn` 的函数可能会改变它。但需要注意的是，在第一次调用 `callbackFn` *之前*，数组的长度会被保存。因此：

*   当调用 `find()` 时，`callbackFn` 不会访问超出数组初始长度的任何元素。
*   对已经访问过的索引的更改不会导致再次在这些元素上调用 `callbackFn`。
*   如果 `callbackFn` 改变了数组中已存在但尚未被访问的元素，则传递给 `callbackFn` 的该元素的值将是该元素在被访问时的值。被[删除](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/delete)的元素被视为 `undefined`。

`find()` 方法是[通用的](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E9%80%9A%E7%94%A8%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95)。它只期望 `this` 值具有 `length` 属性和整数键属性。

find函数的所需参数和map、filter、forEach一样
示例：
```
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found); // 12
```

##### every()

`every()` 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它为数组中的每个元素调用一次指定的 `callbackFn` 函数，直到 `callbackFn` 返回一个[假值](https://developer.mozilla.org/zh-CN/docs/Glossary/Falsy)。如果找到这样的元素，`every()` 方法将会立即返回 `false` 并停止遍历数组。否则，如果 `callbackFn` 为每个元素返回一个[真值](https://developer.mozilla.org/zh-CN/docs/Glossary/Truthy)，`every()` 就会返回 `true`。

`every` 和数学中的全称量词"任意（∀）"类似。特别的，对于空数组，它只返回 `true`。（这种情况属于[无条件正确](https://en.wikipedia.org/wiki/Vacuous_truth)，因为[空集](https://zh.wikipedia.org/wiki/%E7%A9%BA%E9%9B%86)的所有元素都符合给定的条件。）

`callbackFn` 仅针对已分配值的数组索引调用。它不会为[稀疏数组](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#%E7%A8%80%E7%96%8F%E6%95%B0%E7%BB%84)中的空槽调用。

`every()` 不会改变调用它的数组，但指定的 `callbackFn` 函数可以。但是请注意，数组的长度是在第一次调用 `callbackFn` 之前保存的。

示例：
```
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 40];

console.log(array1.every(isBelowThreshold)); // false
```

#### String

##### split()

`split()`** 方法接受一个模式，通过搜索模式将[字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)分割成一个有序的子串列表，将这些子串放入一个数组，并返回该数组。

语法：
split(separator, limit)
> separator
> 描述每个分割应该发生在哪里的模式。可以是 undefined，一个字符串，或者一个具有 Symbol.split 方法的对象——典型的例子是正则表达式。省略 separator 或传递 undefined 会导致 split() 返回一个只包含所调用字符串数组。所有不是 undefined 的值或不具有 @@split 方法的对象都被强制转换为字符串。
> 
> limit 可选
> 一个非负整数，指定数组中包含的子字符串的数量限制。当提供此参数时，split 方法会在指定 separator 每次出现时分割该字符串，但在已经有 limit 个元素时停止分割。任何剩余的文本都不会包含在数组中。
> 
> * 如果在达到极限之前就达到了字符串的末端，那么数组包含的条目可能少于 limit。
> * 如果 limit 为 0，则返回 []。

示例：
```
const str = 'The quick brown fox jumps over the lazy dog.';

const words = str.split(' ');
console.log(words[3]);
// "fox"

const chars = str.split('');
console.log(chars[8]);
// "k"

const strCopy = str.split();
console.log(strCopy);
// ["The quick brown fox jumps over the lazy dog."]

```

##### substring()

[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 的 **`substring()`** 方法返回该字符串从起始索引到结束索引（不包括）的部分，如果未提供结束索引，则返回到字符串末尾的部分。

语法：  ```substring(indexStart, indexEnd)```
> [`indexStart`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring#indexstart)
> 
> 返回子字符串中第一个要包含的字符的索引。
> 
> [`indexEnd`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring#indexend) 可选
> 
> 返回子字符串中第一个要排除的字符的索引。

*   如果省略了 `indexEnd`，则 `substring()` 提取字符直到字符串的末尾。
*   如果 `indexStart` 等于 `indexEnd`，则 `substring()` 返回一个空字符串。
*   如果 `indexStart` 大于 `indexEnd`，则 `substring()` 的效果就像交换了这两个参数一样；请参考下面的示例。

示例：
```
const str = 'Mozilla';

console.log(str.substring(1, 3));
// Expected output: "oz"

console.log(str.substring(2));
// Expected output: "zilla"

```

##### startsWith()

[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 的 **`startsWith()`** 方法用来判断当前字符串是否以另外一个给定的子字符串开头，并根据判断结果返回 `true` 或 `false`。
这个方法能够让你确定一个字符串是否以另一个字符串开头。这个方法区分大小写。

语法：`startsWith(searchString, position)`

> [`searchString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith#searchstring)
> 
> 要在该字符串开头搜索的子串。不能是[正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp#%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E7%9A%84%E7%89%B9%E6%AE%8A%E5%A4%84%E7%90%86)。所有不是正则表达式的值都会被[强制转换为字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%BC%BA%E5%88%B6%E8%BD%AC%E6%8D%A2)，因此省略它或传递 `undefined` 将导致 `startsWith()` 搜索字符串 `"undefined"`，这应该不是你想要的结果。
> 
> [`position`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith#position) 可选
> 
> `searchString` 期望被找到的起始位置（即 `searchString` 的第一个字符的索引）。默认为 `0`。

* 如果给定的字符在字符串的开头被找到（包括当 searchString 是空字符串时），则返回 true；否则返回 false。
* 如果 searchString 是正则表达式，则抛出该异常。

示例：
```
const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));
// Expected output: true

console.log(str1.startsWith('Sat', 3));
// Expected output: false
```

##### iincludes()

[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 值的 **`includes()`** 方法执行区分大小写的搜索，以确定是否可以在一个字符串中找到另一个字符串，并根据情况返回 `true` 或 `false`。

语法：`includes(searchString, position)`

> [`searchString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes#searchstring)
> 
> 一个要在 `str` 中查找的字符串。[不能是正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp#%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E7%9A%84%E7%89%B9%E6%AE%8A%E5%A4%84%E7%90%86)。所有非正则表达式的值都会被[强制转换为字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%BC%BA%E5%88%B6%E8%BD%AC%E6%8D%A2)，因此如果该参数被省略或传入 `undefined`，`includes()` 方法会在字符串中搜索 `"undefined"`，这通常不是你想要的。
> 
> [`position`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes#position) 可选
> 
> 在字符串中开始搜索 `searchString` 的位置。默认值为 `0`。

如果在给定的字符串中找到了要搜索的字符串（包括 searchString 为空字符串的情况），则返回 true，否则返回 false（此方法区分大小写）。

示例：
```
const str = "To be, or not to be, that is the question.";

console.log(str.includes("To be")); // true
console.log(str.includes("question")); // true
console.log(str.includes("nonexistent")); // false
console.log(str.includes("To be", 1)); // false
console.log(str.includes("TO BE")); // false
console.log(str.includes("")); // true
```

#### Number

##### toFixed()

[`Number`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number) 值的 **`toFixed()`** 方法使用定点表示法来格式化该数值。

语法：`toFixed(digits)`
> [`digits`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed#digits) 可选
> 
> 小数点后的位数。应该是一个介于 `0` 和 `100` 之间的值，包括 `0` 和 `100`。如果这个参数被省略，则被视为 `0`。

`toFixed()` 方法返回一个表示 `numObj` 的字符串，但不使用指数计数法，并且小数点后有精确到 `digits` 位的数字。如果需要截断，则将数字四舍五入；如果小数位数不足，则小数部分用零填充，以使其具有指定长度。

如果 `numObj` 的绝对值大于或等于 1021，则该方法使用与 [`Number.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toString) 相同的算法，并以指数计数法返回字符串。如果 `numObj` 的值不是有限的，则 `toFixed()` 会返回 `"Infinity"`、`"NaN"` 或 `"-Infinity"`。

`toFixed()` 对于某些值可能具有比 [`toString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/toString) 更加精确的输出，因为 `toString()` 只输出足够的有效数字来区分该数值与邻近的数值。例如：
```
(1000000000000000128).toString(); // '1000000000000000100'
(1000000000000000128).toFixed(0); // '1000000000000000128'
```

然而，选择一个过高的 `digits` 精度会导致意外的结果，因为小数部分的数字不能精确地表示成浮点数。例如：
`(0.3).toFixed(50); // '0.29999999999999998889776975374843459576368331909180'`

示例：
```
const numObj = 12345.6789;

numObj.toFixed(); // '12346'；四舍五入，没有小数部分
numObj.toFixed(1); // '12345.7'；向上舍入
numObj.toFixed(6); // '12345.678900'；用零补足位数
(1.23e20).toFixed(2); // '123000000000000000000.00'
(1.23e-10).toFixed(2); // '0.00'
(2.34).toFixed(1); // '2.3'
(2.35).toFixed(1); // '2.4'；向上舍入
(2.55).toFixed(1); // '2.5'
// 它向下舍入，因为它无法用浮点数精确表示，并且最接近的可表示浮点数较小
(2.449999999999999999).toFixed(1); // '2.5'
// 向上舍入，因为它与 2.45 的差值小于 Number.EPSILON。
// 这个字面量实际上编码和 2.45 相同的数值

(6.02 * 10 ** 23).toFixed(50); // 6.019999999999999e+23；大数仍然使用指数表示法
```


对负数使用toFixed，由于成员访问的优先级高于一元减号，你需要将负数表达式组合以获得一个字符串。
```
-2.34.toFixed(1); // -2.3，数字
(-2.34).toFixed(1); // '-2.3'
```

## 面向对象

在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。
面向对象编程具有灵活、代码可复用、容易维护和开发的优点，更适合多人合作的大型软件项目。
面向对象的特性：

1. 封装性
2. 继承性
3. 多态性


构造函数中存在一种浪费内存的情况，当构造的多个实例调用同一个方法时，它们的方法储存的位置不同，从而造成不必要的内存浪费，例：
```
function Man(){
    this.sing = function(){
        console.log("human")
    }
}

let you = new Man().sing
let me = new Man().sing
console.log(you === me) // flase
```

### 原型

* 构造函数通过原型分配的函数是所有对象所共享的。
* JavaScript规定，每一个构造函数都有一个prototype属性，指向另一个对象，所以我们也称为原型对象
* 这个对象可以挂载函数，对象实例化不会多次创建原型上函数，节约内存
* 我们可以把那些不变的方法，直接定义在prototype对象上，这样所有对象的实例就可以共享这些方法。
* 构造函数和原型对象中的this都指向实例化的对象

使用原型为构造函数创建函数：
```
function Me(){
    this.type = "这是一个构造函数"
}
Me.prototype.sing = function (){
    print("这是创建在原型上的函数")
}

Me.sing() // 这是创建在原型上的函数
```

#### constructor属性

作用：该属性指向该原型对象的构造函数

注意：如果对prototype赋值，会覆盖原先的方法，导致没有constructor属性，例如：
```
function Func(){}
Func.prototype = {
    sing:function {
        console.log("唱歌")
    }
}
// 在上述代码中，给prototype赋值了一个新的对象，覆盖了原先的对象，所以prototype本来自带的属性和方法也就没有了，使用Func.prototype.sing = function {console.log("唱歌")}这种方法则不受影响，也可以在赋值的对象中自己添加constructor属性，上述代码中可以添加constructor:Func即可。

```

#### 对象原型

所有实例对象都会有一个属性<mark>__prot__</mark>指向构造函数的prototype原型对象，之所以我们对象可以使用构造函数prototype原型对象的属性和方法，就是因为对象__proto__原型的存在。

在Chrome版本较久的时候，也是写的__proto__属性，后来改写 [[prototype]]了，两者意义相同，也都可以执行，详见下
> 注意：
> __proto__是JS非标准属性
> [[prototype]]和__proto__意义相同
> 用来表明当前实例对象指向哪个原型对象prototype
> __proto__是一个只读对象，不能赋值
> __proto__对象原型里面也有一个constructor属性，指向创建该实例对象的构造函数

#### 原型继承

通过原型中的属性可以直接调用的特点，可以利用给原型赋值的方法，继承一个对象，例：
```
const people = {
    name = "molly"
}

function Girl(){
    
}
Girl.prototype =new people //这里是通过原型赋值继承people对象，加new的作用是避免指针问题导致在Girl原型上添加新的函数时people对象也发生改变，（便于理解）可以简单的看做对people对象的深拷贝
Girl.prototype.constructor = Girl 

const woman = new Girl 
console.log(woman.name) // "molly"
```

#### 原型链

每个对象（null除外）都有一个__proto__属性（也可叫[[prototype]])这个属性是指向该对象的原型，原型呢也是一个对象也有自己的__proto__属性指向它的原型，这样顺着__proto__往上就形成了一条原型链。
![](vx_images/31342821240769.png =900x)

这里介绍一种检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上的运算符intanceof
语法：`object instanceof constructor`

使用实例：
```
// 定义构造函数
function C() {}
function D() {}

var o = new C();

o instanceof C; // true，因为 Object.getPrototypeOf(o) === C.prototype

o instanceof D; // false，因为 D.prototype 不在 o 的原型链上

o instanceof Object; // true，因为 Object.prototype.isPrototypeOf(o) 返回 true
C.prototype instanceof Object; // true，同上
```

## 浅拷贝和深拷贝

### 浅拷贝

```
const obj = {
    name:"molly"
}

1.扩展运算符
const o = {...obj}

2.assign方法
const o = {}
Object.assign{o,obj} // 这个方法前面有讲过，详细可以翻前面
```
<mark>浅拷贝对第一层的数据没有影响，但是对于更深层的有影响</mark>，详见下例
```
const obj = {
    name:"molly"
}
const o = {...obj} // 另一个方法也一样适用
o.name = "jason"
console.log(o) // {name:"jason"}
console.log(obj) // {name:"molly"}
```

### 深拷贝

常见方法有

1. 通过递归实现深拷贝
2. lodash库里的cIoneDeep方法
3. 通过JSON.stringify()实现

#### 递归实现深拷贝

下面是一个使用递归简单的深拷贝的函数

```
function deepCopy(newObj,oldObj){
    for(let i in oldObj){
        if(oldObj[i] instanceof Array){ // 这里Array判断一定要写在Object前面，因为数组也是属于对象的一种
            newObj[i] = []
            deepCopy(newObj[i],oldObj[i])
        }else if(oldObj[i] instanceof Object){
            newObj[i] = {}
            deepCopy()
        }else{
            newObj[i] = oldObj[i]
        }
    }
}
```

#### lodash库（cloneDeep方法）

lodash是一个js第三方库，使用前要先引用，[官方文档在这里](https://www.lodashjs.com/docs/lodash.cloneDeep#_clonedeepvalue)

* 下面是使用实例

```
var objects = [{ 'a': 1 }, { 'b': 2 }];
 
var deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]);
// => false

```

#### JSON字符串转换

```
const obj = {
    name:"molly"
}

const newObj = JSON.parse(JSON.stringfy(obj)) // 这种方法对一些数据类型可能不能很好的转换
```

## 异常处理

### throw抛出异常

```
function fn(x,y){
    if(!x || !y){  
        // throw "没有参数"（这行注释的代码也可以抛出异常，但是没有那么明确，一般用下面那行）
        throw new Error("没有参数")    
    }
}
```

### try/catch捕获异常

```
function fn(){
    try{  
        const col = document.querySelector(".col")
        col.style.color = "red"
    }catch(err){
        console.log(err.message)
    }finally{
        // finally表示无论对错都会执行的代码
    }
}
```
try/catch语句在报错时会执行catch里的代码，不会中断程序，如果要中断函数，可以在catch语句里加return

### debugger

debugger是一个关键字，其作用和打断点大致相同

## 改变this指向

1. call ()

这种方法一般使用较少

语法：`func.call(thisArg, arg1, arg2, /* …, */ argN)`

> [`thisArg`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call#thisarg)
> 
> 在调用 `func` 时要使用的 `this` 值。如果函数不在[严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)下，[`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/null) 和 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined) 将被替换为全局对象，并且原始值将被转换为对象。
> 
> [`arg1, …, argN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call#arg1_%E2%80%A6_argn) 可选
> 
> 函数的参数。

2. apply()

语法：`func.apply(thisArg, argsArray)`

> [`thisArg`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply#thisarg)
> 
> 调用 `func` 时提供的 `this` 值。如果函数不处于[严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)，则 [`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/null) 和 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined) 会被替换为全局对象，原始值会被转换为对象。
> 
> [`argsArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply#argsarray) 可选
> 
> 一个类数组对象，用于指定调用 `func` 时的参数，或者如果不需要向函数提供参数，则为 [`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/null) 或 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。

apply()和call()最大的区别在于函数传递的参数，apply是把要传递的参数作为一个数组传递到第二个参数，而call则是以参数的形式传递

3. bind()

语法：`func.bind(thisArg, arg1, arg2, /* …, */ argN)`

> [`thisArg`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#thisarg)
> 
> 在调用绑定函数时，作为 `this` 参数传入目标函数 `func` 的值。如果函数不在[严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)下，[`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/null) 和 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined) 会被替换为全局对象，并且原始值会被转换为对象。如果使用 [`new`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new) 运算符构造绑定函数，则忽略该值。
> 
> [`arg1, …, argN`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#arg1_%E2%80%A6_argn) 可选
> 
> 在调用 `func` 时，插入到传入绑定函数的参数前的参数。

<mark>bind()方法不会调用函数。但是能改变函数内部this指向</mark>
bind()方法和前两个方法的返回值不同，前两个方法的返回值就是调用的函数的返回值，而bind的返回值是一个函数，这个函数就是调用的函数改变this值后的函数

##  防抖函数（debounce）

1. 使用lodash库中提供的[_.debounce(func,\[wait=0\], \[options=\])](https://www.lodashjs.com/docs/lodash.debounce#_debouncefunc-wait0-options)函数

使用实例（记得导入库）：
```
let i = 0;
const catchMoveBox = document.queryselector("#catchMoveBox")
catchMoveBox.addEventListener("mousemove",_.debounce(()=>{
    i++;
},150)) // 这段代码的作用就是检测在#catchMoveBox上鼠标的移动事件，防抖时长是150
```

2. 手写防抖函数

```
function debounce(t){ // 这个t是防抖函数的延迟时间
    let timer;
    return function(){
        timer && clearTimeout(timer)
        timer = setTimeout(function(){
            // 这里写自己要执行的函数
        },t)
    }
};
const catchMoveBox = document.querySelector("#catchMoveBox");
catchMoveBox.addEventListener("mousemove",debounce(150))
```

## 节流（throttle）

1. loadsh库里提供的[_.throttle(func, \[wait=0\], \[options=\])](https://www.lodashjs.com/docs/lodash.throttle)函数

用法和防抖函数一致

2. 手写节流函数

```
function throttle(t){ // 这个t是防抖函数的延迟时间
    let timer;
    return function(){
        if(!timer){ // 如果计时器不存在才执行
            timer = setTimeout(function(){
                // 这里写自己要执行的函数
            
                // 清空计时器
                timer = null
            },t)
        }
    }
};
const catchMoveBox = document.querySelector("#catchMoveBox");
catchMoveBox.addEventListener("mousemove",throttle(150))
```

# 致谢

这个笔记写了两千多行终于迎来了它的终篇：

笔记顺序是根据黑马pink老师发布的视频[【黑马程序员前端JavaScript入门到精通全套视频教程，javascript核心进阶ES6语法、API、js高级等基础知识和实战教程】](https://www.bilibili.com/video/BV1Y84y1L7Nn?p=198&vd_source=56a9230d242cae9e218aabbf9211dcfc)写的，其中很多内容都是参考的[Mmdn网站](https://developer.mozilla.org/zh-CN/)，线上指导是AI[通义千问](https://tongyi.aliyun.com/qianwen/)。

遇到过许多bug，也搞懂了很多难题，感谢在我的学习中为我提供知识和遍历的各位老师，也感谢自己的坚持，但是，学习之路仍然漫长，js这一段也只是一小部分，希望自己能坚持下去。
