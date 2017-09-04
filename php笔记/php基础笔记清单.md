title: php基础笔记清单
tags:
  - PHP
categories:
  - PHP
date: 2017-08-31 11:22:00
---

## 一.变量

### 1.变量命名及规范：
一个变量包括两方面：变量名和变量值。

* 变量名的第一个字符必须是$。
* $后的第一字符必须是 字母 或 下划线。
* php命名区分大小写，最好统一小写。

### 2.创建变量：
> 在php中创建变量就是变量的声明
```php
$a = 'hello world!';
```

## 二.数据类型

### 1.基本数据类型(标量数据类型)
* Integer	整数
* Float		浮点数
* String 	字符串
* Boolean 	布尔型

### 2.组合数据类型
* Array 	数组
* Object 	对象

### 3.特殊数据类型
* Resourse 	资源类型
* Null		Null类型

### 4.松散类型
> php属于松散类型的语言，可以自动转换变量的数据类型

### 5.测试变量的类型 gettype();
```php
$a;
echo gettype($a); //NULL
$a = 'hello';
echo gettype($a); //string
...
```
> 
is_int(val),is_float(val),is_string(val);
is_bool(val),is_array(val),is_object(val);
is_resource(val),is_null(val); //返回true或false

### 6.改变变量的数据类型
```php
$a = 8.23;
settype($a,string); 	//"8.23"
settype($a,integer) 	//8
settype($a,boolean)		//1
```

### 7.强制类型转换
> 变量本身的类型	并没有发生变化

```php
$a = 23.22;
```
>  
(string) $a;(int) $a;(float) $a;(boolean) $a;
函数转换：intval(val),floatval(val),strval(val);
intval()还有第二个参数为转换的基数。


## 三.运算符与表达式

### 1.运算符类型
> 
1. 算数运算符 		+,-,*,/,%
2. 赋值运算符		=,+=,-=,*=,/=
3. 位运算			&,|,^,~,<<,>>
4. 比较运算符		>,<,>=,<=,==,===,!=,!==
5. 错误控制
6. 增量、减量运算符	++,-- 
7. 逻辑运算符		&&(and),||(or),xor,!
8. 字符串运算符 	.,.=

### 2.运算符的优先级
> 
1. 算数运算符: '*', '/', '%', '+', '-'
2. 比较运算符: '<', '<=', '>', '>=', '<>', '==', '!=', '===', '!=='
3. 赋值运算符: '=', '+=', '-=', '*=', '/=', '.=', '%='

### 3.常量 define();
> 
php中常量不同于变量，常量名不需要以 $ 开头，最好以大写命名
define(MY_COUNT,22);


## 四.选择与循环

### 1.选择语句
> 
* if语句
* if...else语句
* if...elseif...语句
* switch...case语句
* 三目运算符 (exp) ? exp1 : exp2;

### 2.循环语句
> 
* while循环
* do...while循环 //先执行循环体再判断
* for...循环
* foreach()循环

### 3.break语句退出循环
### 4.continue语句跳过本次循环
### 5.goto语句


## 五.函数

`function name(arg1,arg2){...};`

> 
1. 形参和实参
2. 按值传递  ：传递的是值得副本
3. 按引用传递 & ： 传递的是值的引用
4. 函数返回 return： 返回变量、常量、表达式或引用
5. 全局变量和局部变量 global和GLOBALS['']; 函数内部变量为局部变量
6. 静态变量 static ： 也是局部变量，但会把值一直保存在内存中

## 六.对象
> 栈空间段， 堆空间段，代码段， 初使化静态段，

### 1.面向对象设计的优点：代码与需求易融合、可重用性、模块特性
### 2.面向对象设计的基础

#### 2.1 类 ： 对一类事物的统称
#### 2.2 对象  ： 对象是类的实例
#### 2.3 属性  ： 类的对象的特性
#### 2.4 方法  ： 类的行为 (类的方法和属性统称为类的 成员)

### 3.PHP中创建类和对象
> 
对象总是按引用的方式赋值的
class Car{};//创建Car类
$car1 = new Car();//创建一个Car类的实例 把一个对象的引用赋值给 $car1

### 4.创建和使用属性
#### 4.1 属性的可见性 公有:public(var)、保护:protected、私有:private
> 
public公有属性 可被任何代码访问
protected保护属性 可被本类和子类访问，不被本类和类的子类外部访问
private私有属性 不被类的子类和类的外部访问，只能本类访问

#### 4.2 申明属性并访问属性
```php
class Myclass {
  public $attr1 = 1;
  private $attr2;
  protected $attr3;
}
$c1 = new Myclass();
echo $c1->attr1;
```
#### 4.3 静态属性 static 可以看成类的全局变量
```php
class Myclass {
	static public $attr1 = 1;
}
$c1 = new Myclass();
//不能使用对象来访问只能类
echo Myclass::$attr1;
```

#### 4.4 类常量 const
```php
class Myclass {
	const ATTR = 1;
}
$c1 = new Myclass();
//同静态变量一样
echo Myclass::ATTR;
```
#### 4.5 反射 对象 ReflectionMethod(对象,方法) invokeArgs(对象，数组参数)
```php
class Myclass {
  public function say(){
  return '我叫小明';
}
public function run($name){
	return '我叫'.$name.'我跑了20000公里';
}
}
$xiaoming = new Myclass();
$str = new ReflectionMethod($xiaoming,"say");
echo $str-> invoke($xiaoming); //我叫小明
$str2 = new ReflectionMethod($xiaoming,'run');
echo $str2-> invokeArgs($xiaoming,Array('小明'));//我叫小明我跑了20000公里
```
#### 5.方法
> 
方法的可见性(public,private,protected)、方法的创建、方法的调用、方法的参数和返回值

#### 5.1 方法中访问对象和属性(自包含性)
> 在对象的方法中访问同一个对象的属性，使用$this
$this分别代表对象$p1、$p2、$p3
$this->attr;

#### 5.2 静态方法 static
> 
在静态方法中只能访问静态变量，不能访问普通变量
static的成员是属于类的，是不属于任何对象实例
类里面的静态方法只能访问类的静态的属性 self::
非静态方法里可以访问静态成员不能使用$this,使用self::
```php

			class Car {
				public static $name = 'nice';
				const AGE = 22;
				public static function run(){
					echo self::$name; //访问$name
					echo self:AGE;	//访问age
				}
			}
			Car::run() //调用静态方法
```
#### 5.3 类型提示检测方法的参数
```php

			class Car {
				public $color;
			}
			class Gar {
				public function paint(Car $car,$color){
					$car->color=$color;
				}
			}
			$car = new Car();
			$gar = new Gar();
			$car->color = 'red';
			$gar->paint($car,'blue');
			echo $car->color; //blue
```
            
#### 5.4 封装实现独立性 private

#### 5.5 构造函数和析构函数__construct(),__destruct()
> 调用基类的构造函数 parent::__construct();

#### 5.5 __get(),__set()和__call()重载对象
> 
__get()和__set();
使对象能够对不可见的属性的访问和修改
```php

				class Car {
					private $color = 'red';
					//__get()方法
					public function __get(){
						if(isset($this->color)){
							return $this->color;
						}else {
							return null;
						}
						
					}
					//__set()方法
					public function __set($val){
						$this->color = $val
					}
				}
```
> 方法重载：
子类写和父类方法一样的名字覆盖父类方法的形式
```php

                class One {
                    public function say(){
                        echo 'One';
                    }
                }
                class Two extends One {
                    public function say(){
                        parent::say();
                        echo 'Two';
                    }
                }
 ```
 
#### 5.6 final关键字 类和方法阻止 继承 和 重载
```php

final class Demo{
}
```
            

#### 5.7 clone 克隆 __clone();//克隆时执行的方法
> $p2 = clone $p1;

#### 5.8 抽象方法和抽象类 abstract
> 抽象类不能产生实例对象
```php

            abstract class Demo {
                abstract function fun1();
                abstract function fun2();
            }
            class Text extends Demo{
                function fun1(){}
                function fun2(){}
            }
```
> 
子类必须把父类中的抽象方法全部都实现，否则子类中还存在抽象方法，
那么子类还是抽象类，还是不能实例化类

#### 5.9 接口 interface
> 
接口的思想是指定了一个实现了该接口的类必须实现的一系列方法
接口是一种特殊的抽象类，抽象类又是一种特殊的类，所以接口也是一种特殊的类，
接口里面所有的方法必须 都是声明为抽象方法,另外接口里面不能声明变量(但可声明常量constant)
而且接口里面所有的成员都是public权限的
```php

            interface One {
                const constant = 'constant value';
                public function fun1();
                public function fun2();
            }
            interface Two extends One {
                function fun3();
                function fun4();
            }
            继承使用 implements 关键字
            class Three implements One {
                function fun1(){}
                function fun2(){}
            }
            // 实现了全部方法，我们去可以使用子类去实例化对象了
            $three = new Three();
            // 使用implements实现多个接口
            class Four implemtns 接口一, 接口二, ... {
                // 必须把所有接口中的方法都要实现才可以实例化对象。
            }
```
> 
PHP中不仅一个类可以实现多个接口，也可以在继承一个类的同时实现多个接口, 
一定要先继承类再去实现接口；
```php

            // 使用extends继承一个类，使用implements实现多个接口
            class Four extends 类名一 implemtns 接口一, 接口二, ... {
                // 所有接口中的方法都要实现才可以实例化对象
                ...
            }
```
### 6. 多态
> 
多态就是把子类对象赋值给父类引用，然后调用父类的方法，去执行子类覆盖父类的那个方法，
但在PHP里是弱类型的，对象引用都是一样的不分父类引用，还是子类引用。

### 7.串行化serialize()方法，__sleep(),__wakeup()

> 
serialize()前调用__sleep()方法限制串行化的内容，
unserialize()后调用__wakeup()方法反序列化后的结果

### 8.自动加载类 __autoload();
### 9.魔术方法 __get(),__set(),__clone,__sleep(),__wakeup()...
### 10.命名空间 namespace

*<span style="color:red">参考</span>*

* http://www.cnblogs.com/xiaochaohuashengmi/archive/2010/09/10/1823042.html
* << php入门经典 >>


	
