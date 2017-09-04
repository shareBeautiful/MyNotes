title: javaScript基础(1)
tags:
  - JavaScript
categories:
  - JavaScript
date: 2017-08-29 10:07:00
---
## Number,String,Boolean,强制类型转换
> 
Number() 当转换一个 对象 时，先调用 valueOf()方法，如果返回对象，则调用 toString()方法
String() 当转换一个 对象 时，先调用 toString()方法，如果返回对象，则调用 valueOf()方法
Object.prototype.valueOf();
Object.prototype.toString();

valueOf()方法返回的是对象的 ‘值’，默认返回对象本身；
toString()返回对象字符串的形式

## Object 上的的属性有:

### Object.prototype

> 
Object.prototype.writable //默认为false 
Object.prototype.enumerable //默认为false 
Object.prototype.configurable //默认为false 
Object.prototype.constructor //用于创建一个对象的原型。

> 
Object.assign(target, …sources) //把任意多个的源对象自身的可枚举属性拷贝给目标对象，然后返回目标对象。
Object.create(proto,[propertiesobject]) //创建一个拥有指定原型和若干个指定属性的对象。
Object.entries(obj) //返回一个包含由给定对象所有可枚举属性的属性名和属性值组成的 
//[属性名，属性值] 键值对的数组，数组中键值对的排列顺序和使用for…in循环遍历该对象时返回的顺序一致。 
Object.keys(obj) //返回一个由给定对象的所有可枚举自身属性的属性名组成的数组

> 
Object.getOwnPropertyNames(obj) //返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性）组成的数组。 
Object.defineProperties(obj,{'prop1':{},'prop2':{}}) //在一个对象上添加或修改一个或者多个自有属性，并返回该对象。
Object.defineProperty(obj,'property',{}) //直接在一个对象上定义一个新属性，或者修改一个已经存在的属性， 并返回这个对象
Object.getOwnPropertyDescriptor(obj, prop) //返回指定对象上一个自有属性对应的属性描述符。
Object.freeze(obj)  //冻结一个对象 冻结指的是不能向这个对象添加新的属性,删除、修改、属性
Object.getPrototypeOf(object) //返回该对象的原型。
Object.is(value1, value2) //判断两个值是否是同一个值。
Object.isExtensible(obj) //判断一个对象是否是可扩展的（是否可以在它上面添加新的属性）
Object.isFrozen(obj) //判断一个对象是否被冻结（frozen）
Object.isSealed(obj) //判断一个对象是否是密封的（sealed）
Object.preventExtensions(obj) //让一个对象变的不可扩展，也就是永远不能再添加新的属性。
Object.setPrototypeOf(obj, prototype) //将一个指定的对象的原型设置为另一个对象或者null
Object.values(obj) //返回一个包含指定对象所有的可枚举属性值的数组

> 
Object.prototype 上的的属性有：Object又继承自Object.prototype,所以Object上也有prototype的方法

> 
Object.prototype.hasOwnProperty('prop') //返回一个布尔值，表示某个对象是否含有指定的属性，而且此属性非原型链继承。
Object.prototype.isPrototypeOf(obj) //返回一个布尔值，表示指定的对象是否在本对象的原型链中。
Object.prototype.propertyIsEnumerable() //判断指定属性是否可枚举。
Object.prototype.toString() //返回对象的字符串表示。
Object.prototype.valueOf() //返回指定对象的原始值。


### Array.prototype 上的属性：

slice(),splice(),indexOf(),join()
...
### Function.prototype 上的属性:
> 
Function.prototype.length //返回函数参数的个数
Function.prototype.call(); //改变函数调用的对象
Function.prototype.apply();
Function.prototype.bind(this,arg1,arg2); //bind方法每运行一次，就返回一个新函数

### 自定义的函数、Object、Array、String、Number、Boolean、包括 Function 都是 Function构造出的实例
> 
所以有这些函数的__proto__ 引用指向 Function.prototype 
而Function
而 Function.prototype.__proto__的引用 又 指向 Object.prototype
Object.__proto__  === Function.__proto__ === Function.prototype
Function.prototype.__proto__ === Object.prototype
Object.__proto__.__proto__ === Object.prototype
Object.prototype.__proto__ === null


## 函数：
> 
arguments.callee当前函数的引用
arguments.callee.caller调用当前函数的函数的引用
length命名参数个数 和prototype属性
apply(this,[a1,a2])和call(this,a1,a2),bind(this,a1,a2)

> 
函数中参数是按 “值” 传递的而不是按引用传递的,
在传递一个引用类型作为参数时，传递的是这个对象的地址，而不是引用(指针)
每个执行环境都有一个与之关联的 变量对象 ，环境中定义的所有变量和函数都
保存在这个对象中。
在函数中 执行环境 就是这个函数中的作用域，“活动对象” 就作为这个函数的 “变量对象”，
开始这个活动对象只包含 arguments对象 (在全局作用域中是不存在的)，
作用域中下一个变量对象就是包含 “外部的环境”，而再下一个变量对象则来自下一个包含环境。
这样一直延续到下一全局执行环境(全局环境中的变量对象始终是作用域链中的最后一个对象)。

## 数组：
> 
1. 队列方法：push(),pop(),unshift(),shift();
2. 排序方法: resverse(),sort(call);
3. 操作方法: splice(star,num,ars3...),slice(star,end),join();
4. 位置方法: indexOf(),lastIndexOf();//返回给定元素在数组中第一次出现的位置 如果没有返回-1
5. 迭代方法: every(),some(),map(),filter(function(val,index,arr){},this),forEach()无返回
6. 缩小方法: reduce(),reduceRight(function(val1,val2,index.arr){},val);val累积变量初始值
    
## 字符串：
> 
1. 字符方法: charAt(),charCodeAt();
2. 字符串操作方法: concat(),slice(),substring(),substr(),trim();
3. 字符串位置方法: indexOf(),lastIndexOf();
4. 匹配方法: match()返回数组,search(),splite(',',num)
    
## 数值:
> 
1. 数字转字符串方法: toString(2) 转2进制，toFixed(2) //转保留小数,toExponential 转科学计数法toPrecision(2) 转有效数字
2. Math方法: Math.ceil(),Math.floor().Math.pow(),Math.random()随机,PI
    
## JSON:
> 
1. 字符串必须使用双引号表示，不能使用单引号。
2. 对象的键名必须放在双引号里面
3. 数组或对象最后一个成员的后面，不能加逗号。
4. 复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
5. 简单类型的值只有四种：字符串、数值（必须以十进制表示）、布尔值和null（不能使用NaN, Infinity, -Infinity和undefined）。合格的JSON值

> 
["one", "two", "three"]
{ "one": 1, "two": 2, "three": 3 }
{"names": ["张三", "李四"] }
[ { "name": "张三"}, {"name": "李四"} ]

6. JSON.stringfy() 将一个json值转为字符串 JSON字符串以 单引号''第二个参数接受一个数组指定需要转成字符串的属性
7. toJSON 方法
> 
JSON.stringify发现参数对象有toJSON方法，
就直接使用这个方法的返回值作为参数，而忽略原对象的其他参数。
8.JSON.parse方法用于将JSON字符串转化成对象。


## Date对象:
1. Date() 带有参数，Date对象作为普通函数使用时，返回的还是当前时间。
> 
1> Date.now() 返回当前距离1970年1月1日 00:00:00 UTC的毫秒数
2> Date.parse() 用来解析日期字符串，返回距离1970年1月1日 00:00:00的毫秒数
3> Date.UTC() Date.UTC方法可以返回UTC时间

2. new Date()
> 
注意：月份从0开始计算，但是，天数从1开始计算。
另外，除了日期默认为1，小时、分钟、秒钟和毫秒默认都是0。
1> 如果不加参数，生成的就是代表当前时间的对象。
2> new Date('2008,4,28')支持多种写法'-','/'
3> new Date(2008,4) 最少需要提供两个参数（年和月）

3. data = new Date():
get类：
> 
getTime()：返回距离1970年1月1日00:00:00的毫秒数，等同于valueOf方法。
getDate()：返回实例对象对应每个月的几号（从1开始）。
getDay()：返回星期几，星期日为0，星期一为1，以此类推。
getYear()：返回距离1900的年数。
getFullYear()：返回四位的年份。
getMonth()：返回月份（0表示1月，11表示12月）。
getHours()：返回小时（0-23）。
getMilliseconds()：返回毫秒（0-999）。
getMinutes()：返回分钟（0-59）。
getSeconds()：返回秒（0-59）。
getTimezoneOffset()：返回当前时间与UTC的时区差异，以分钟表示，返回结果考虑到了夏令时因素。
set类：
setDate(date)：设置实例对象对应的每个月的几号（1-31），返回改变后毫秒时间戳。
setYear(year): 设置距离1900年的年数。
setFullYear(year [, month, date])：设置四位年份。
setHours(hour [, min, sec, ms])：设置小时（0-23）。
setMilliseconds()：设置毫秒（0-999）。
setMinutes(min [, sec, ms])：设置分钟（0-59）。
setMonth(month [, date])：设置月份（0-11）。
setSeconds(sec [, ms])：设置秒（0-59）。
setTime(milliseconds)：设置毫秒时间戳。

## RegExp对象:
1. 写法：字面量，构造函数
> 
var regex = /xyz/i;
var regex = new RegExp('xyz',"i");
test(),exec();