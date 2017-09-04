title: jQuery常用操作
tags: ['jQuery']
categories:
  - jQuery
date: 2017-08-10 14:27:00
---
## 一、简介
### 定义
　　jQuery创始人是美国John Resig，是优秀的Javascript框架；
　　jQuery是一个轻量级、快速简洁的javaScript库。[源码戳这](https://jquery.com/download/)
### jQuery对象
　　jQuery产生的对象时jQuery独有的，只能自己调用
### 书写规则
　　支持链式操作；
　　在变量前加"$"符号（var $variable = jQuery 对象）；
　　注：此规定并不是强制要求。

## 二、寻找元素
- 选择器
- 基本选择器
- 层级选择器
- 属性选择器 

### 1.基本筛选器
``` javascript
$('li:first')    //第一个元素
$('li:last')     //最后一个元素
$("tr:even")     //索引为偶数的元素，从 0 开始
$("tr:odd")      //索引为奇数的元素，从 0 开始
$("tr:eq(1)")    //给定索引值的元素
$("tr:gt(0)")    //大于给定索引值的元素
$("tr:lt(2)")    //小于给定索引值的元素
$(":focus")      //当前获取焦点的元素
$(":animated")   //正在执行动画效果的元素
```

### 2.内容选择器
``` javascript
$("div:contains('nick')")    //包含nick文本的元素
$("td:empty")    //不包含子元素或者文本的空元素
$("div:has(p)")  //含有选择器所匹配的元素
$("td:parent")   //含有子元素或者文本的元素
```

### 3.表单选择器
``` javascript
$(":input")   //匹配所有 input, textarea, select 和 button 元素
$(":text")       //所有的单行文本框
$(":password")   //所有密码框
$(":radio")      //所有单选按钮
$(":checkbox")   //所有复选框
$(":submit")     //所有提交按钮
$(":reset")      //所有重置按钮
$(":button")     //所有button按钮
$(":file")       //所有文件域
$("input:checked")    //所有选中的元素
$("select option:selected")    //select中所有选中的option元素
```

### 4.筛选器
#### 4.1 过滤
``` javascript
$("p").eq(0)       //当前操作中第N个jQuery对象,类似索引
$('li').first()    //第一个元素
$('li').last()     //最后一个元素
$(this).hasClass("test")    //元素是否含有某个特定的类,返回布尔值
$('li').has('ul')  //包含特定后代的元素
```

#### 4.2 查找
``` javascript
$("div").children()      //div中的每个子元素,第一层
$("div").find("span")    //div中的包含的所有span元素,子子孙孙
$("p").next()       　　　//紧邻p元素后的一个同辈元素
$("p").nextAll()         //p元素之后所有的同辈元素
$("#test").nextUntil("#test2")            //id为"#test"元素之后到id为'#test2'之间所有的同辈元素,掐头去尾
$("p").prev()            //紧邻p元素前的一个同辈元素
$("p").prevAll()         //p元素之前所有的同辈元素
$("#test").prevUntil("#test2")    //id为"#test"元素之前到id为'#test2'之间所有的同辈元素,掐头去尾
$("p").parent()          //每个p元素的父元素
$("p").parents()         //每个p元素的所有祖先元素,body,html
$("#test").parentsUntil("#test2")    //id为"#test"元素到id为'#test2'之间所有的父级元素,掐头去尾
$("div").siblings()      //所有的同辈元素,不包括自己
```

## 三、属性操作
### 1.基本属性操作
``` javascript
$("img").attr("src");    　　　　　　 //返回文档中所有图像的src属性值
$("img").attr("src","test.jpg");    //设置所有图像的src属性
$("img").removeAttr("src");    　　　//将文档中图像的src属性删除
$("input[type='checkbox']").prop("checked", true);    //选中复选框
$("input[type='checkbox']").prop("checked", false);
$("img").removeProp("src");    　　 //删除img的src属性
```

### 2.CSS类
``` javascript
$("p").addClass("selected");    　　//为p元素加上 'selected' 类
$("p").removeClass("selected");    //从p元素中删除 'selected' 类
$("p").toggleClass("selected");    //如果存在就删除,否则就添加HTML代码/文本/值
$('p').html();    　　　　　　　　　　 //返回p元素的html内容
$("p").html("Hello <b>nick</b>!");  //设置p元素的html内容
$('p').text();    　　　　　　　　　　 //返回p元素的文本内容
$("p").text("nick");    　　　　　　　//设置p元素的文本内容
$("input").val();    　　　　　　　　 //获取文本框中的值
$("input").val("nick");     　　　　 //设置文本框中的内容
```

## 四、CSS操作
### 1.样式 
``` javascript
$("p").css("color");          //访问查看p元素的color属性
$("p").css("color","red");    //设置p元素的color属性为red
$("p").css({ "color": "red", "background": "yellow" });    //设置p元素的color为red，background属性为yellow（设置多个属性要用{}字典形式）
```

### 2.位置
``` javascript
$('p').offset()     //元素在当前视口的相对偏移,Object {top: 122, left: 260}
$('p').offset().top
$('p').offset().left
$("p").position()   //元素相对父元素的偏移,对可见元素有效，Object {top: 117, left: 250}
$(window).scrollTop()    //获取滚轮滑的高度
$(window).scrollLeft()   //获取滚轮滑的宽度
$(window).scrollTop('100')    //设置滚轮滑的高度为100
```

### 3.尺寸
``` javascript
$("p").height();    //获取p元素的高度
$("p").width();     //获取p元素的宽度
$("p:first").innerHeight()    //获取第一个匹配元素内部区域高度(包括补白、不包括边框)
$("p:first").innerWidth()     //获取第一个匹配元素内部区域宽度(包括补白、不包括边框)
$("p:first").outerHeight()    //匹配元素外部高度(默认包括补白和边框)
$("p:first").outerWidth()     //匹配元素外部宽度(默认包括补白和边框)
$("p:first").outerHeight(true)    //为true时包括边距
```

## 五、文档处理
### 1.内部插入
``` javascript
$("p").append("<b>nick</b>");    //每个p元素内后面追加内容
$("p").appendTo("div");    　　　 //p元素追加到div内后
$("p").prepend("<b>Hello</b>");  //每个p元素内前面追加内容
$("p").prependTo("div");    　   //p元素追加到div内前外部插入
```
### 2.外部插入
``` javascript
$("p").after("<b>nick</b>");     //每个p元素同级之后插入内容
$("p").before("<b>nick</b>");    //在每个p元素同级之前插入内容
$("p").insertAfter("#test");     //所有p元素插入到id为test元素的后面
$("p").insertBefore("#test");    //所有p元素插入到id为test元素的前面替换
```

### 3.替换
``` javascript
$("p").replaceWith("<b>Paragraph. </b>");    //将所有匹配的元素替换成指定的HTML或DOM元素
$("<b>Paragraph. </b>").replaceAll("p");     //用匹配的元素替换掉所有 selector匹配到的元素删除
```

### 4.删除
``` javascript
$("p").empty();     //删除匹配的元素集合中所有的子节点，不包括本身
$("p").remove();    //删除所有匹配的元素,包括本身
$("p").detach();    //删除所有匹配的元素(和remove()不同的是:所有绑定的事件、附加的数据会保留下来)
```

### 5.复制
``` javascript
$("p").clone()    　　//克隆元素并选中克隆的副本
$("p").clone(true)   //布尔值指事件处理函数是否会被复制
```

## 六、事件
### 1.页面载入
当页面载入成功后再运行的函数事件
``` javascript
$(document).ready(function(){
	do something...
});
 
//简写
$(function($) {
  do something...
});
```

### 2.页面处理

``` javascript
//bind 为每个匹配元素绑定事件处理函数，绑定多个用{}。
$("p").bind("click", function(){
  alert( $(this).text() );
});
$(menuF).bind({
    "mouseover":function () {
    $(menuS).parent().removeClass("hide");
    },"mouseout":function () {
    $(menuS).parent().addClass("hide");
}
});         
 
$("p").one( "click", fun...)    //one 绑定一个一次性的事件处理函数
$("p").unbind( "click" )        //解绑一个事件    
```

### 3.页面委派
``` javascript
// 与bind 不同的是当时间发生时才去临时绑定。
$("p").delegate("click",function(){
  do something...
});
 
$("p").undelegate();    　　　//p元素删除由 delegate() 方法添加的所有事件
$("p").undelegate("click")   //从p元素删除由 delegate() 方法添加的所有click事件
```

### 4.事件
``` javascript
$("p").click();    　　//单击事件
$("p").dblclick();    //双击事件
$("input[type=text]").focus()  //元素获得焦点时,触发 focus 事件
$("input[type=text]").blur()   //元素失去焦点时,触发 blur事件
$("button").mousedown()//当按下鼠标时触发事件
$("button").mouseup()  //元素上放松鼠标按钮时触发事件
$("p").mousemove()     //当鼠标指针在指定的元素中移动时触发事件
$("p").mouseover()     //当鼠标指针位于元素上方时触发事件
$("p").mouseout()    　//当鼠标指针从元素上移开时触发事件
$(window).keydown()    //当键盘或按钮被按下时触发事件
$(window).keypress()   //当键盘或按钮被按下时触发事件,每输入一个字符都触发一次
$("input").keyup()     //当按钮被松开时触发事件
$(window).scroll()     //当用户滚动时触发事件
$(window).resize()     //当调整浏览器窗口的大小时触发事件
$("input[type='text']").change()    //当元素的值发生改变时触发事件
$("input").select()    //当input 元素中的文本被选择时触发事件
$("form").submit()     //当提交表单时触发事件
$(window).unload()     //用户离开页面时

```

### 5.(evnet object)属性方法：
所有的事件函数都可以传入event参数方便处理事件

``` javascript
$("p").click(function(event){
 alert(event.type); //"click"
}); 
 
(evnet object)属性方法：
event.pageX 　 //事件发生时，鼠标距离网页左上角的水平距离
event.pageY 　 //事件发生时，鼠标距离网页左上角的垂直距离
event.type 　　//事件的类型
event.which 　 //按下了哪一个键
event.data 　　//在事件对象上绑定数据，然后传入事件处理函数
event.target 　//事件针对的网页元素
event.preventDefault() 　//阻止事件的默认行为(比如点击链接，会自动打开新页面)
event.stopPropagation()  //停止事件向上层元素冒泡
```

## 七、效果
### 1.基本
``` javascript
$("p").show()    　　　　//显示隐藏的匹配元素
$("p").show("slow");    //参数表示速度,("slow","normal","fast"),也可为900毫秒
$("p").hide()    　　　　//隐藏显示的元素
$("p").toggle();   　　 //切换 显示/隐藏
```

### 2.滑动
``` javascript
$("p").slideDown("900");    //用900毫秒时间将段落滑下
$("p").slideUp("900");    　//用900毫秒时间将段落滑上
$("p").slideToggle("900");  //用900毫秒时间将段落滑上，滑下
```

### 3.淡入淡出
``` javascript
$("p").fadeIn("900");    　　  //用900毫秒时间将段落淡入
$("p").fadeOut("900");    　　 //用900毫秒时间将段落淡出
$("p").fadeToggle("900");    　//用900毫秒时间将段落淡入,淡出
$("p").fadeTo("slow", 0.6);    //用900毫秒时间将段落的透明度调整到0.6
```

## 八、对象访问
``` javascript
$.trim() 　　//去除字符串两端的空格
$.each() 　　//遍历一个数组或对象，for循环
$.inArray() //返回一个值在数组中的索引位置，不存在返回-1
$.grep() 　 //返回数组中符合某种标准的元素
$.extend()  //将多个对象，合并到第一个对象
$.makeArray() //将对象转化为数组
$.type()    //判断对象的类别（函数对象、日期对象、数组对象、正则对象等等
$.isArray() //判断某个参数是否为数组
$.isEmptyObject() //判断某个对象是否为空(不含有任何属性)
$.isFunction()    //判断某个参数是否为函数
$.isPlainObject() //判断某个参数是否为用"{}"或"new Object"建立的对象
$.support()  
```

模拟each()内部实现机制

``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        li = [11,22,33];
        $.each(li,function (k,v) {
            console.log(this);
            console.log(k,v);
            if (k == 1){
                return false;
            }
        })
    </script>


    <script>
        function myEach(obj,func) {
            for (var i=0;i<obj.length;i++){
                var current = obj[i];
                var ret = func(i,current);
                if (ret == false){
                    break;
                }
            }
        }

        var li = [10,20,30];
        myEach(li,function (k,v) {
            console.log(k,v);
            return false;
        })
    </script>
</body>
</html>
```

## 九、插件拓展机制 
### 1.方式一
``` javascript
jQuery.fn.extend({
  check: function() {
    return this.each(function() { this.checked = true; });
  },
  uncheck: function() {
    return this.each(function() { this.checked = false; });
  }
});

$("input[type=checkbox]").check();
$("input[type=radio]").uncheck();
```

### 2.方式二
``` 
jQuery.extend({
  min: function(a, b) { return a < b ? a : b; },    //三元运算
  max: function(a, b) { return a > b ? a : b; }
});

jQuery.min(2,3);     //2
jQuery.max(4,5);    //5
```
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div class="title">111</div>
    <div class="title">222</div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        jQuery.fn.extend({
            show1: function () {
                var val = this.text();
                val = val + "sb";
                return val;
            },
            show2: function () {

            }
        });
        var ret = $(".title").show1();
        console.log(ret);


        jQuery.extend({
            s1: function (arg) {
                var val = $(arg).text();
                return val + "sb";
            },
            s2: function () {

            }
        });
        var ret2 = $.s1(".title");
        console.log(ret2);
    </script>
</body>
</html>
```

## 十、实例

### 1.返回顶部

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .divH {
            height: 1800px;
        }
        .divT {
            width: 50px;
            height: 50px;
            font-size: 23px;
            background-color: #2F4F4F;
            color: white;
            position: fixed;
            right: 18px;
            bottom: 18px;
        }
        .divT:hover{
            cursor: pointer;
        }
        .hide {
            display: none;
        }
    </style>
</head>
<body>
    <div class="divH"></div>
    <div class="divT hide" onclick="ReturnTop();"><strong>返回顶部</strong></div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        window.onscroll = function () {
            var current = $(window).scrollTop();
            if (current > 180){
                $(".divT").removeClass("hide");
            }else {
                $(".divT").addClass("hide");
            }
        };

        function ReturnTop() {
            $(window).scrollTop(0);
        }
    </script>
</body>
</html>
```

### 2.左侧菜单
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
          .menu{
              height: 600px;
              width: 30%;
              background-color: #2F4F4F;
              float: left;
          }
         .title{
             line-height: 50px;
             color: #ddd;
         }
         .title:hover{
             cursor: pointer;
             color: lightcyan;
             font-size: 18px;
         }
         .hide{
             display: none;
         }
    </style>
</head>

<body>
    <div class="outer">
        <div class="menu">
            <div class="item">
                <div class="title" onclick="Show(this);">菜单一</div>
                <div class="con">
                    <div>111</div>
                    <div>111</div>
                    <div>111</div>
                </div>
            </div>
            <div class="item">
                <div class="title" onclick="Show(this);">菜单二</div>
                <div class="con hide">
                    <div>222</div>
                    <div>222</div>
                    <div>222</div>
                </div>
            </div>
            <div class="item">
                <div class="title" onclick="Show(this);">菜单三</div>
                <div class="con hide">
                    <div>333</div>
                    <div>333</div>
                    <div>333</div>
                </div>
            </div>
        </div>
    </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        function Show(self) {
            $(self).next().removeClass("hide").parent().siblings().children(".con").addClass("hide");
        }
    </script>
</body>
</html>
```

### 3.菜单切换
``` html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin: 0px;
            padding: 0px;
        }
        .tab_outer{
            margin: 0px auto;
            width: 60%;
        }
        .menu{
            background-color: #cccccc;
            border: 1px solid #ccc;
            line-height: 40px;
        }
        .menu li{
            display: inline-block;
            color: white;
        }
        .menu li:hover {
            cursor: pointer;
        }
        .menu a{
            padding: 11px;
        }
        .content{
            border: 1px solid #ccc;
            height: 300px;
            font-size: 30px;
        }
        .hide{
            display: none;
        }

        .current{
            background-color: #0099dd;
            color: black;
        }
    </style>
</head>
<body>
    <div class="tab_outer">
          <ul class="menu">
              <li xxx="c1" class="current" onclick="Tab(this);">菜单一</li>
              <li xxx="c2" onclick="Tab(this);">菜单二</li>
              <li xxx="c3" onclick="Tab(this);">菜单三</li>
          </ul>
          <div class="content">
              <div id="c1">内容一</div>
              <div id="c2" class="hide">内容二</div>
              <div id="c3" class="hide">内容三</div>
          </div>
    </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        function Tab(self) {
            $(self).addClass("current").siblings().removeClass("current");
            var x = "#" + $(self).attr("xxx");
            $(x).removeClass("hide").siblings().addClass("hide");
        }
    </script>
</body>
</html>
```

### 4.滚动菜单
``` html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        body{
            margin: 0;
            background-color: #dddddd;
        }
        .w{
            margin: 0 auto;
            width: 980px;
        }
        .pg-header{
            background-color: black;
            color: white;
            height: 48px;
        }
        .pg-body .menu{
            position: absolute;
            left: 200px;
            width: 180px;
            background-color: white;
            float: left;
        }
        li {
            list-style-type: none;
        }
        .pg-body .menu .active{
            background-color: #425a66;
            color: white;
        }
        .pg-body .fixed{
            position: fixed;
            top: 10px;
        }
        .pg-body .content{
            position: absolute;
            left: 385px;
            right: 200px;
            background-color: white;
            float: left;
        }
        .pg-body .content .item{
            height: 900px;
        }
    </style>

</head>
<body>
    <div class="pg-header">
        <div class="w"></div>
    </div>
    <div class="pg-body">
        <div id="menu" class="menu">
            <ul>
                <li menu="funcOne">第一章</li>
                <li menu="funcTwo">第二章</li>
                <li menu="funcStree">第三章</li>
            </ul>
        </div>
        <div id="content" class="content">
            <div class="item" con="funcOne">床前明月管</div>
            <div class="item" con="funcTwo">疑是地上霜</div>
            <div class="item" con="funcStree" style="height: 100px">我是郭德纲</div>
        </div>
    </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        window.onscroll = function () {
            var onTop = $(window).scrollTop();
            if (onTop >= 48){
                $("#menu").addClass("fixed");
            }else {
                $("#menu").removeClass("fixed");
            }

            var flag = false;
            $(".item").each(function () {
                var topH = $(this).offset().top;
                var HH = $(this).height() + topH;
                var wH = $(window).height();

                if ((wH + onTop) == HH){
                    $("ul .active").removeClass("active");
                    $("li:last").addClass("active");
                    flag = true;
                    return
                }
                if (flag){
                    return
                }

                var menuCon = $(this).attr("con");
                if ((topH < onTop) && (onTop < HH)){
                    $("ul [menu='" + menuCon +"']").addClass("active");
                }else {
                    $("ul [menu='" + menuCon +"']").removeClass("active");
                }
            })
        }
    </script>
</body>
</html>
```

### 5.淡入淡出
``` html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
      <button id="in">fadein</button>
      <button id="out">fadeout</button>
      <button id="toggle">fadetoggle</button>
      <button id="fadeto">fadeto</button>

      <div id="id1" style="display:none; width: 80px;height: 80px;background-color: blueviolet"></div>
      <div id="id2" style="display:none; width: 80px;height: 80px;background-color: orangered "></div>
      <div id="id3" style="display:none; width: 80px;height: 80px;background-color: darkgreen "></div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        $(document).ready(function(){
            $("#in").click(function(){
               $("#id1").fadeIn(1000);
               $("#id2").fadeIn(1000);
               $("#id3").fadeIn(1000);

            });
            $("#out").click(function(){
               $("#id1").fadeOut(1000);
               $("#id2").fadeOut(1000);
               $("#id3").fadeOut(1000);

            });
            $("#toggle").click(function(){
               $("#id1").fadeToggle(1000);
               $("#id2").fadeToggle(1000);
               $("#id3").fadeToggle(1000);

            });
            $("#fadeto").click(function(){
               $("#id1").fadeTo(1000,0.4);
               $("#id2").fadeTo(1000,0.5);
               $("#id3").fadeTo(1000,0);
            });
        });
    </script>
</body>
</html>
```

### 6.滑动
``` html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        #flipshow,#content,#fliphide,#toggle{
            padding: 5px;
            text-align: center;
            background-color: blueviolet;
            border:solid 1px red;

        }
        #content{
            padding: 50px;
            display: none;
        }
    </style>
</head>
<body>

    <div id="flipshow">出现</div>
    <div id="fliphide">隐藏</div>
    <div id="toggle">toggle</div>
    <div id="content">helloworld</div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        $(document).ready(function(){
              $("#flipshow").click(function(){
                 $("#content").slideDown(1000);
              });
              $("#fliphide").click(function(){
                 $("#content").slideUp(1000);
              });
              $("#toggle").click(function(){
                 $("#content").slideToggle(1000);
              })
          });
    </script>

</body>
</html>
```

### 7.隐藏与显示
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--1 隐藏与显示-->
    <!--2 淡入淡出-->
    <!--3 滑动-->
    <!--4 效果-回调:每一个动画执行完毕之后所能执行的函数方法或者所能做的一件事-->

    <p>hello</p>
    <button id="hide">隐藏</button>
    <button id="show">显示</button>
    <button id="toggle">隐藏/显示</button>

    <script src="../../jquery-1.12.4.js"></script>
    <script>

        $(document).ready(function(){
            $("#hide").click(function(){
                $("p").hide(1000);
            });
            $("#show").click(function(){
                $("p").show(1000);
            });

        //用于切换被选元素的 hide() 与 show() 方法。
            $("#toggle").click(function(){
                $("p").toggle(2000);
            });
        });

    </script>
</body>
</html>
```

### 8.添加与删除标签
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div class="outer">
           <div class="section">
               <div class="icons" style="display: inline-block">
                   <a onclick="Add(this);"><button>+</button></a>
               </div>
               <div class="inputs" style="display: inline-block">
                   <input type="checkbox">
                   <input type="text" value="IP">
               </div>
           </div>
       </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        function Add(self) {
            $(self).parentsUntil("outer").clone().find("a").html("<button>-</button>").attr("onclick","Remove(this);").end().eq(1).appendTo(".outer");
        }
        function Remove(self) {
            $(self).parentsUntil("outer").eq(1).remove();
        }
    </script>
</body>
</html>
```

### 9.商城商品放大镜
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta name="viewport" content="width=device-width">
    <meta http-equiv="X-UA-Compatible" content="IE=8">
    <title>购物商城</title>

    <style>
            *{
                margin: 0;
                padding: 0;
            }
            .outer{
                position:relative;
                width:350px;
                height:350px;
                border:1px solid black;
            }
            .outer .small-box{
                position: relative;
                z-index: 1;
            }
            .outer .small-box .mark{
                position: absolute;
                display: block;
                width: 350px;
                height: 350px;
                background-color: #fff;
                filter: alpha(opacity=0);
                opacity: 0;
                z-index: 10;
            }
            .outer .small-box .float-box{
                display: none;
                width: 175px;
                height: 175px;
                position: absolute;
                background: #DAEEFC;
                filter: alpha(opacity=40);
                opacity: 0.4;
            }
            .outer .big-box{
                position: absolute;
                top: 0;
                left: 351px;
                width: 350px;
                height: 350px;
                overflow: hidden;
                border: 1px solid transparent;
                z-index: 1;
            }
            .outer .big-box img{
                position: absolute;
                z-index: 5
            }
    </style>
</head>
<body>

    <div  class="outer">
        <div  class="small-box">
            <div  class="mark"></div>
            <div  class="float-box" ></div>
            <img width="350" height="350" src="../../css/1.jpg">
        </div>
        <div class="big-box">
            <img width="900px" height="900px" src="../../css/1.jpg" >
        </div>
    </div>


<script src="../../jquery-1.12.4.js"></script>

<script>
   $(function(){
        $(".mark").mouseover(function () {
            $(".float-box").css("display","block");
            $(".big-box").css("display","block");
        });

        $(".mark").mouseout(function () {
            $(".float-box").css("display","none");
            $(".big-box").css("display","none");
        });



        $(".mark").mousemove(function (e) {

            var _event = e || window.event;  //兼容多个浏览器的event参数模式

            var float_box_width  = $(".float-box")[0].offsetWidth;
            var float_box_height = $(".float-box")[0].offsetHeight;//175,175


            var float_box_width_half  =  float_box_width / 2;
            var float_box_height_half =  float_box_height/ 2;//87.5,87.5


            var small_box_width  =  $(".outer")[0].offsetWidth;
            var small_box_height =  $(".outer")[0].offsetHeight;//360,360


            var mouse_left = _event.clientX   - float_box_width_half;
            var mouse_top = _event.clientY  - float_box_height_half;


            if (mouse_left < 0) {
                mouse_left = 0;
            } else if (mouse_left > small_box_width - float_box_width) {
                mouse_left = small_box_width - float_box_width;
            }
            if (mouse_top < 0) {
                mouse_top = 0;
            } else if (mouse_top > small_box_height - float_box_height) {
                mouse_top = small_box_height - float_box_height;
            }

            $(".float-box").css("left",mouse_left + "px");
            $(".float-box").css("top",mouse_top + "px");
            
            
            var percentX = ($(".big-box img")[0].offsetWidth - $(".big-box")[0].offsetWidth) / (small_box_width - float_box_width);
            var percentY = ($(".big-box img")[0].offsetHeight - $(".big-box")[0].offsetHeight) / (small_box_height - float_box_height);
            console.log($(".big-box img")[0].offsetWidth,$(".big-box")[0].offsetWidth,small_box_width,float_box_width)
            console.log(percentX,percentY)
            $(".big-box img").css("left",-percentX * mouse_left + "px");
            $(".big-box img").css("top",-percentY * mouse_top + "px")

        })
   })

</script>
</body>
</html>
```
### 10.商城菜单
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .hide{
            display:none;
        }
        .header-nav {
            height: 39px;
            background: #c9033b;
        }
        .header-nav .bg{
            background: #c9033b;
        }
        .header-nav .nav-allgoods .menuEvent {
            display: block;
            height: 39px;
            line-height: 39px;
            text-decoration: none;
            color: #fff;
            text-align: center;
            font-weight: bold;
            font-family: 微软雅黑;
            color: #fff;
            width: 100px;
        }
        .header-nav .nav-allgoods .menuEvent .catName {
            height: 39px;
            line-height: 39px;
            font-size: 15px;
        }
        .header-nav .nav-allmenu a {
            display: inline-block;
            height: 39px;
            vertical-align: top;
            padding: 0 15px;
            text-decoration: none;
            color: #fff;
            float: left;
        }
        .header-menu a{
            color:#656565;
        }
        .header-menu .menu-catagory{
            position: absolute;
            background-color: #fff;
            border-left:1px solid #fff;
            height: 316px;
            width: 230px;
             z-index: 4;
             float: left;
        }
        .header-menu .menu-catagory .catagory {
            border-left:4px solid #fff;
            height: 104px;
            border-bottom: solid 1px #eaeaea;
        }
        .header-menu .menu-catagory .catagory:hover {
            height: 102px;
            border-left:4px solid #c9033b;
            border-bottom: solid 1px #bcbcbc;
            border-top: solid 1px #bcbcbc;
        }
        .header-menu .menu-content .item{
            margin-left:230px;
            position:absolute;
            background-color:white;
            height:314px;
            width:500px;
            z-index:4;
            float:left;
            border: solid 1px #bcbcbc;
            border-left:0;
            box-shadow: 1px 1px 5px #999;
        }
    </style>
</head>
<body>
    <div class="pg-header">

    <div class="header-nav">
        <div class="container narrow bg">
            <div class="nav-allgoods left">
                <a id="all_menu_catagory" href="#" class="menuEvent">
                    <b class="catName">全部商品分类</b>>
                    <span class="arrow" style="display: inline-block;vertical-align: top;"></span>
                </a>
            </div>
        </div>
    </div>
    <div class="header-menu">
        <div class="container narrow hide">
            <div id="nav_all_menu" class="menu-catagory">
                <div class="catagory" float-content="one">
                    <div class="title">家电</div>
                    <div class="body">
                        <a href="#">空调</a>
                    </div>
                </div>
                <div class="catagory" float-content="two">
                    <div class="title">床上用品</div>
                    <div class="body">
                        <a href="http://www.baidu.com">床单</a>
                    </div>
                </div>
                <div class="catagory" float-content="three">
                    <div class="title">水果</div>
                    <div class="body">
                        <a href="#">橘子</a>
                    </div>
                </div>
            </div>

            <div id="nav_all_content" class="menu-content">
                <div class="item hide" float-id="one">

                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="勺子">勺子</a> </span>
                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="菜刀">菜刀</a> </span>

                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="#">菜板</a> </span>
                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="碗">碗</a> </span>

                        </dd>
                    </dl>

                </div>
                <div class="item hide" float-id="two">
                    <dl>
                        <dt><a href="#" class="red">床上用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="">枕头</a> </span>

                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">床上用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="角阀">夏凉被</a> </span>

                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">床上用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="角阀">嘿嘿嘿</a> </span>

                        </dd>
                    </dl>
                </div>
                <div class="item hide" float-id="three">
                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="#" target="_blank" title="角阀">微波炉</a> </span>

                        </dd>
                    </dl>
                    <dl>
                        <dt><a href="#" class="red">厨房用品</a></dt>
                        <dd>
                            <span>| <a href="http://www.meilele.com/category-jiaofa" target="_blank" title="角阀">金菜刀</a> </span>

                        </dd>
                    </dl>
                </div>
            </div>
        </div>
    </div>
</div>

<script src="../../jquery-1.12.4.js"></script>
<script>
    $(function () {
        Change("#all_menu_catagory","#nav_all_menu","#nav_all_content")
    });

    function Change(menuF,menuS,menuT) {
        $(menuF).bind({
            "mouseover":function () {
            $(menuS).parent().removeClass("hide");
        },"mouseout":function () {
            $(menuS).parent().addClass("hide");
        }
        });

        $(menuS).children().bind({
            "mouseover":function () {
                $(menuS).parent().removeClass("hide");
                var $item = $(menuT).find('[float-id="' +　$(this).attr("float-content") + '"]');
                $item.removeClass("hide").siblings().addClass("hide");
            },
            "mouseout":function () {
                $(menuS).parent().addClass("hide");
                $(menuT).parent().addClass("hide");
            }
        });
        
        $(menuT).children().bind({
            "mouseover":function () {
                $(menuS).parent().removeClass("hide");
                $(this).removeClass("hide");
            },
            "mouseout":function () {
                $(menuS).parent().addClass("hide");
                $(this).addClass("hide");
            }
        })
    }
</script>
</body>
</html>
```

### 11.拖动面板
``` html 

<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
    <div style="border: 1px solid #ddd;width: 600px;position: absolute;">
        <div id="title" style="background-color: black;height: 40px;color: white;">
            <strong>标题</strong>
        </div>
        <div style="height: 300px;">
            内容
        </div>
    </div>
<script type="text/javascript" src="../../jquery-1.12.4.js"></script>
<script>
    $(function () {
        $('#title').mouseover(function () {
            $(this).css('cursor','move');
        }).mousedown(function (e) {
            var _event = e || widows.event;
            var ord_x = _event.clientX;
            var ord_y = _event.clientY;

            var parent_left = $(this).parent().offset().left;
            var parent_top = $(this).parent().offset().top;

            $(this).bind('mousemove',function (e) {
                var _new_event = e || window.event;
                var new_x = _new_event.clientX;
                var new_y = _new_event.clientY;

                var x = parent_left + (new_x - ord_x);
                var y = parent_top + (new_y - ord_y);

                $(this).parent().css('left',x+'px');
                $(this).parent().css('top',y+'px');
            })
        }).mouseup(function () {
            $(this).unbind('mousemove');
        });
    })
</script>
</body>
</html>
```

### 12.模态对话框
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .shade{
            position: fixed;
            left: 0;
            top: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,.6) ;
            z-index: 20;
        }
        .modal{
            position: fixed;
            left: 50%;
            top: 50%;
            height: 300px;
            width: 400px;
            margin-top: -150px;
            margin-left: -200px;
            z-index: 30;
            border: 1px solid #ddd;
            background-color: white;
        }
        .hide{
            display: none;
        }
        .modal form {
            position: fixed;
            left: 50%;
            top: 50%;
            height: 200px;
            width: 229px;
            border: 1px;
            margin-left: -115px;
            margin-top: -100px;
        }
        .modal form p {
            float: right;
            margin-top: 12px;
        }
        .modal form span {
            float: right;
            display: inline-block;
            height: 18px;
            width: 170px;
            background-color: #FFEBEB;
            text-align: center;
            border: 1px solid #ffbdbe;
            color: #e4393c;
            font-size: 14px;
            visibility: hidden;
        }
        .modal form [type="button"] {
            position: absolute;
            bottom: -30px;
            left: 115px;
        }
        .modal form [value="提交"]{
            left: 50px;
        }
    </style>
</head>
<body>
    <div style="width: 300px; margin: 0 auto">
        <input type="button" value="添加主机" onclick="return Add();" />
        <table style="border: 2px solid #F5F5F5; width: 300px;">
            <thead>
                <tr>
                    <th >主机名</th>
                    <th >IP</th>
                    <th >端口</th>
                    <th>操作</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td target="host">c1.com</td>
                    <td target="ip">1.1.1.1</td>
                    <td target="port">8888</td>
                    <td onclick="Edit(this);">Edit</td>
                </tr>
               <tr>
                    <td target="host">c2.com</td>
                    <td target="ip">1.1.1.1</td>
                    <td target="port">8888</td>
                    <td onclick="Edit(this);">Edit</td>
                </tr>
                <tr>
                    <td target="host">c3.com</td>
                    <td target="ip">1.1.1.1</td>
                    <td target="port">8888</td>
                    <td onclick="Edit(this);">Edit</td>
                </tr>
                <tr>
                    <td target="host">.com</td>
                    <td target="ip">1.1.1.1</td>
                    <td target="port">8888</td>
                    <td onclick="Edit(this);">Edit</td>
                </tr>
            </tbody>
        </table>
    </div>
    <div class="shade hide"></div>
    <div  class="modal hide">
        <form action="" method="get">
            <p>主机名:<input type="text" id="host" name="host"><br><span></span></p>
            <p>IP地址:<input type="text" id='ip' name="ip"><br><span></span></p>
            <p>端口号:<input type="text" id='port' name="port"><br><span></span><br></p>
            <input type="button" value="提交" onclick="return SubmitForm();">
            <input type="button" value="取消" onclick="HideModal();">
        </form>
    </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>
        $(function () {
           $("tr:even").css("background-color","#f5f5f5");
        });
        function Edit(ths) {
            $(".shade,.modal").removeClass("hide");
            prevList = $(ths).prevAll();
            prevList.each(function () {
                var text = $(this).text();
                var target = $(this).attr("target");
                $("#"+target).val(text);
            });
        }
        function HideModal() {
            $(".shade,.modal").addClass("hide");
            $(".modal").find("input[type='text']").val("");
            Addd = false;
        }
        function SubmitForm() {
            var flag = Detection();

            try {
                    if (Addd && flag){
                    $("tbody").append($("tr").last().clone());
                    $(".modal").find("input[type='text']").each(function () {
                        var value = $(this).val();
                        var name = $(this).attr("name");
                        ($("tr").last().children()).each(function () {
                            if ($(this).attr("target") == name){
                                $(this).text(value);
                                return
                            }
                                }
                        )});
                    Addd = false;
                    HideModal();
                    return false;
                }
            }catch (e){}


            if (flag){
                $(".modal").find("input[type='text']").each(function () {
                    var value = $(this).val();
                    var name = $(this).attr("name");
                    $(prevList).each(function () {
                        if ($(this).attr("target") == name){
                            $(this).text(value);
                            return
                        }
                            }
                    )});
                    $(".modal,.shade").addClass("hide");
                    HideModal();
                }
            return flag;
            }

        
        function Detection() {
            var flag = true;
            $(".modal").find("input[type='text']").each(function () {
                var value = $(this).val();
                if (value.length == 0){
                    $(this).next().next().css("visibility","visible").text("亲，不能为空");
                    flag = false;
                    return false;
                }else {
                    $(this).next().next().css("visibility","hidden").text("");
                }

                if ($(this).attr('name') == "host"){
                    var r = /(\.com)$/;
                    if (r.test(value) == false){
                        $(this).next().next().css("visibility","visible").text("主机名必须以.com结尾");
                        flag = false;
                        return false;
                }
                }else if ($(this).attr('name') == "ip"){
                    var r2 = /^(([0-2]?[0-9][0-9]?)\.){3}([0-2]?[0-9][0-9]?)$/;
                    if (r2.test(value) == false){
                        $(this).next().next().css("visibility","visible").text("ip 地址格式有误");
                        flag = false;
                        return false;
                    }
                }else if ($(this).attr('name') == "port"){
                    var r3 = /^([0-9]{1,5})$/;
                    if ((r3.test(value) == false) || (value > 65535)){
                        $(this).next().next().css("visibility","visible").text("端口必须为0-65535");
                        flag = false;
                        return false;
                    }
                }else {
                    $(this).next().next().css("visibility","hidden").text("");
                }
        });
        return flag;
        }

        function Add() {
            Addd = true;
            $(".shade,.modal").removeClass("hide");
        }
    </script>
</body>
</html>
```

### 13.轮播图
``` html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        ul{
            list-style: none;
        }
        .out{
            width: 730px;
            height: 454px;
            margin: 50px auto;
            position: relative;
        }
        .out .img li{
            position: absolute;
            left: 0;
            top: 0;
        }
        .out .num{
            position: absolute;
            left:0;
            bottom: 20px;
            text-align: center;
            font-size: 0;
            width: 100%;
        }
        .out .btn{
            position: absolute;
            top:50%;
            margin-top: -30px;
            width: 30px;
            height: 60px;
            background-color: aliceblue;
            color: black;
            text-align: center;
            line-height: 60px;
            font-size: 40px;
            display: none;
        }
        .out .num li{
            width: 20px;
            height: 20px;
            background-color: black;
            color: #fff;
            text-align: center;
            line-height: 20px;
            border-radius: 60%;
            display: inline;
            font-size: 18px;
            margin: 0 10px;
            cursor: pointer;
        }
        .out .num li.active{
            background-color: red;
        }
        .out .left{
            left: 0;
        }
        .out .right{
            right: 0;
        }
        .out:hover .btn{
            display: block;
            color: white;
            font-weight: 900;
            background-color: black;
            opacity: 0.8;
            cursor: pointer;
        }
        .out img {
            height: 100%;
            width: 100%;
        }
    </style>
</head>
<body>
     <div class="out">
         <ul class="img">
             <li><a href="#"><img src="images/1.jpg" alt=""></a></li>
             <li><a href="#"><img src="images/2.jpg" alt=""></a></li>
             <li><a href="#"><img src="images/3.jpg" alt=""></a></li>
             <li><a href="#"><img src="images/4.jpg" alt=""></a></li>
             <li><a href="#"><img src="images/5.jpg" alt=""></a></li>
         </ul>

         <ul class="num">
             <!--<li class="active">1</li>-->
             <!--<li>2</li>-->
             <!--<li>3</li>-->
             <!--<li>4</li>-->
             <!--<li>5</li>-->
         </ul>

         <div class="left btn"><</div>
         <div class="right btn">></div>

     </div>

    <script src="../../jquery-1.12.4.js"></script>
    <script>

        $(function(){
            var size=$(".img li").size();
            for (var i= 1;i<=size;i++){
                var li="<li>"+i+"</li>";
                $(".num").append(li);
            }
            $(".num li").eq(0).addClass("active");


            $(".num li").mouseover(function(){
               $(this).addClass("active").siblings().removeClass("active");
               var index=$(this).index();
               i=index;
               $(".img li").eq(index).fadeIn(1000).siblings().fadeOut(1000);
            });


        i=0;
        var t=setInterval(move,1500);

        function move(){
            i++;
            if(i==size){
                i=0;
            }
            $(".num li").eq(i).addClass("active").siblings().removeClass("active");
            $(".img li").eq(i).stop().fadeIn(1000).siblings().stop().fadeOut(1000);
        }

        function moveL(){
            i--;
            if(i==-1){
                i=size-1;
            }
            $(".num li").eq(i).addClass("active").siblings().removeClass("active");
            $(".img li").eq(i).stop().fadeIn(1000).siblings().stop().fadeOut(1000);
        }

        $(".out").hover(function(){
            clearInterval(t);
        },function(){
            t=setInterval(move,1500);
        });

        $(".out .right").click(function(){
            move()
        });
        $(".out .left").click(function(){
           moveL()
        })

        });
    </script>

</body>
</html>
```

### 14.编辑框
``` html 

<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        .edit-mode{
            background-color: #b3b3b3;
            padding: 8px;
            text-decoration: none;
            color: white;
        }
        .editing{
            background-color: #f0ad4e;
        }
    </style>
</head>
<body>

    <div style="padding: 20px">
        <input type="button" onclick="CheckAll('#edit_mode', '#tb1');" value="全选" />
        <input type="button" onclick="CheckReverse('#edit_mode', '#tb1');" value="反选" />
        <input type="button" onclick="CheckCancel('#edit_mode', '#tb1');" value="取消" />

        <a id="edit_mode" class="edit-mode" href="javascript:void(0);"  onclick="EditMode(this, '#tb1');">进入编辑模式</a>

    </div>
    <table border="1">
        <thead>
        <tr>
            <th>选择</th>
            <th>主机名</th>
            <th>端口</th>
            <th>状态</th>
        </tr>
        </thead>
        <tbody id="tb1">
            <tr>
                <td><input type="checkbox" /></td>
                <td edit="true">v1</td>
                <td>v11</td>
                <td edit="true" edit-type="select" sel-val="1" global-key="STATUS">在线</td>
            </tr>
            <tr>
                <td><input type="checkbox" /></td>
                <td edit="true">v1</td>
                <td>v11</td>
                <td edit="true" edit-type="select" sel-val="2" global-key="STATUS">下线</td>
            </tr>
            <tr>
                <td><input type="checkbox" /></td>
                <td edit="true">v1</td>
                <td>v11</td>
                <td edit="true" edit-type="select" sel-val="1" global-key="STATUS">在线</td>
            </tr>
        </tbody>
    </table>

    <script type="text/javascript" src="../../jquery-1.12.4.js"></script>
    <script>
        /*
         监听是否已经按下control键
         */
        window.globalCtrlKeyPress = false;

        window.onkeydown = function(event){
            if(event && event.keyCode == 17){
                window.globalCtrlKeyPress = true;
            }
        };
        window.onkeyup = function(event){
            if(event && event.keyCode == 17){
                window.globalCtrlKeyPress = false;
            }
        };

        /*
         按下Control，联动表格中正在编辑的select
         */
        function MultiSelect(ths){
            if(window.globalCtrlKeyPress){
                var index = $(ths).parent().index();
                var value = $(ths).val();
                $(ths).parent().parent().nextAll().find("td input[type='checkbox']:checked").each(function(){
                    $(this).parent().parent().children().eq(index).children().val(value);
                });
            }
        }
    </script>
    <script type="text/javascript">

$(function(){
    BindSingleCheck('#edit_mode', '#tb1');
});

function BindSingleCheck(mode, tb){

    $(tb).find(':checkbox').bind('click', function(){
        var $tr = $(this).parent().parent();
        if($(mode).hasClass('editing')){
            if($(this).prop('checked')){
                RowIntoEdit($tr);
            }else{
                RowOutEdit($tr);
            }
        }
    });
}

function CreateSelect(attrs,csses,option_dict,item_key,item_value,current_val){
    var sel= document.createElement('select');
    $.each(attrs,function(k,v){
        $(sel).attr(k,v);
    });
    $.each(csses,function(k,v){
        $(sel).css(k,v);
    });
    $.each(option_dict,function(k,v){
        var opt1=document.createElement('option');
        var sel_text = v[item_value];
        var sel_value = v[item_key];

        if(sel_value==current_val){
            $(opt1).text(sel_text).attr('value', sel_value).attr('text', sel_text).attr('selected',true).appendTo($(sel));
        }else{
            $(opt1).text(sel_text).attr('value', sel_value).attr('text', sel_text).appendTo($(sel));
        }
    });
    return sel;
}

STATUS = [
    {'id': 1, 'value': "在线"},
    {'id': 2, 'value': "下线"}
];

BUSINESS = [
    {'id': 1, 'value': "车上会"},
    {'id': 2, 'value': "二手车"}
];

function RowIntoEdit($tr){
    $tr.children().each(function(){
        if($(this).attr('edit') == "true"){
            if($(this).attr('edit-type') == "select"){
                var select_val = $(this).attr('sel-val');
                var global_key = $(this).attr('global-key');
                var selelct_tag = CreateSelect({"onchange": "MultiSelect(this);"}, {}, window[global_key], 'id', 'value', select_val);
                $(this).html(selelct_tag);
            }else{
                var orgin_value = $(this).text();
                var temp = "<input value='"+ orgin_value+"' />";
                $(this).html(temp);
            }

        }
    });
}

function RowOutEdit($tr){
    $tr.children().each(function(){
        if($(this).attr('edit') == "true"){
            if($(this).attr('edit-type') == "select"){
                var new_val = $(this).children(':first').val();
                var new_text = $(this).children(':first').find("option[value='"+new_val+"']").text();
                $(this).attr('sel-val', new_val);
                $(this).text(new_text);
            }else{
                var orgin_value = $(this).children().first().val();
                $(this).text(orgin_value);
            }

        }
    });
}

function CheckAll(mode, tb){
    if($(mode).hasClass('editing')){

        $(tb).children().each(function(){

            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){

            }else{
                check_box.prop('checked',true);

                RowIntoEdit(tr);
            }
        });

    }else{

        $(tb).find(':checkbox').prop('checked', true);
    }
}

function CheckReverse(mode, tb){

    if($(mode).hasClass('editing')){

        $(tb).children().each(function(){
            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){
                check_box.prop('checked',false);
                RowOutEdit(tr);
            }else{
                check_box.prop('checked',true);
                RowIntoEdit(tr);
            }
        });


    }else{
        
        $(tb).children().each(function(){
            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){
                check_box.prop('checked',false);
            }else{
                check_box.prop('checked',true);
            }
        });
    }
}

function CheckCancel(mode, tb){
    if($(mode).hasClass('editing')){
        $(tb).children().each(function(){
            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){
                check_box.prop('checked',false);
                RowOutEdit(tr);

            }else{

            }
        });

    }else{
        $(tb).find(':checkbox').prop('checked', false);
    }
}

function EditMode(ths, tb){
    if($(ths).hasClass('editing')){
        $(ths).removeClass('editing');
        $(tb).children().each(function(){
            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){
                RowOutEdit(tr);
            }else{

            }
        });

    }else{

        $(ths).addClass('editing');
        $(tb).children().each(function(){
            var tr = $(this);
            var check_box = tr.children().first().find(':checkbox');
            if(check_box.prop('checked')){
                RowIntoEdit(tr);
            }else{

            }
        });

    }
}


    </script>

</body>
</html>
```