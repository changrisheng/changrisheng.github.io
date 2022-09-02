---
title: PHP
date: 2021-10-13 15:00:00
tags:
  - 复习
  - PHP
categories:
  - 复习
keywords:
description: 复习PHP知识点
top_img:
cover: https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/php.png
---


{% note blue 'fas fa-bullhorn' modern %}PHP最新稳定版本：8.1.0{% endnote %}


# PHP基础知识

## PHP简介
{% folding cyan, 点击查看 %}

1. PHP（“PHP: Hypertext Preprocessor”，超文本预处理器的字母缩写）是一种被广泛应用的开放源代码的多用途脚本语言，它可嵌入到 HTML中，尤其适合 web 开发。

{% endfolding %}

## false的七种情况
{% folding cyan, 点击查看 %}
> 字符串和数字用等于模糊判断时，字符串会被先转换成数字再进行对比
{% tabs %}
<!-- tab 定义 -->
```text
  整型0
  浮点0.0
  布尔false
  空字符串'',""
  字符串'0'
  空数组[]
  NULL
```
<!-- endtab -->
<!-- tab 示例代码 -->
```PHP
    $arr = [
        "'0e123' == ''" => '0e123' == '',
        "'0e123' == '0'" => '0e123' == '0',
        "'0e123' == 0" => '0e123' == 0,
        "'0e123' == 'e'" => '0e123' == 'e',
        "'0e123' == '000'" => '0e123' == '000',
        "'1e123' == '1'" => '1a000e123' == '1',
        "'1e123' == 1" => '1a000e123' == 1,
        "'000e123' == '0'" => '000e123' == '0',
        "'e123' == 0" => 'a123' == 0,
        "'e123' == '0'" => 'a123' == '0',
        "null == 0" => null == 0,
        "null == '0'" => null == '0',
        "null == false" => null == false,
        "[] == 0" => [] == 0,
        "[] == '0'" => [] == '0',
        "[] == false" => [] == false,
        "false == 0" => false == 0,
        "false == '0'" => false == '0',
    ];
    foreach ($arr as $key => $value) {
        echo '( ' . $key . ' ) => ' . ($value === true ? 'true' : 'false') . PHP_EOL;
    }

```
<!-- endtab -->
<!-- tab 输出结果 -->
```PHP
    ( '0e123' == '' ) => false
    ( '0e123' == '0' ) => true
    ( '0e123' == 0 ) => true
    ( '0e123' == 'e' ) => false
    ( '0e123' == '000' ) => true
    ( '1e123' == '1' ) => false
    ( '1e123' == 1 ) => true
    ( '000e123' == '0' ) => true
    ( 'e123' == 0 ) => true
    ( 'e123' == '0' ) => false
    ( null == 0 ) => true
    ( null == '0' ) => false
    ( null == false ) => true
    ( [] == 0 ) => false
    ( [] == '0' ) => false
    ( [] == false ) => true
    ( false == 0 ) => true
    ( false == '0' ) => true
```
<!-- endtab -->
{% endtabs%}
{% endfolding %}

## NULL的三种情况
{% folding cyan, 点击查看 %}
1. 直接赋值NULL
2. 未定义变量
3. unset销毁后的变量
{% endfolding %}

## 常量
{% folding cyan, 点击查看 %}
{% note danger simple %}一经定义，不可删除和修改{% endnote %}

> 预定义常量

```text
    1. FILE 文件所在路径+文件名
    2. LINE 所在代码行
    3. DIR 所在文件夹路径
    4. FUNCTION 方法名
    5. CLASS 类名
    6. TRAIT TRAIT的名称
    7. METHOD 类名+方法名
    8. NAMESPACE 命名空间名
```
{% endfolding %}

## 引用变量
{% folding cyan, 点击查看 %}
{% note info simple %}用不同名字访问同一个变量内容，用『&』符号表示{% endnote %}
{% endfolding %}

## 超全局数组
{% folding cyan, 点击查看 %}
{% tabs %}
<!-- tab 全局数组 -->
```text
    $GLOBALS，包含下面8个超全局数组的值
    $_GET
    $_POST
    $_REQUERT，包含$_GET,$_POST,$_COOKIE
    $_SEESION
    $_COOKIE
    $_SERVER
```
<!-- endtab -->
<!-- tab 使用 -->
```PHP
    $_SERVER['SERVER_ADDR'] //服务器地址
    $_SERVER['SERVER_NAME'] //服务名称
    $_SERVER['REQUEST_TIME'] //请求时间
    $_SERVER['QUERY_STRING'] //请求地址中问号后的内容
    $_SERVER['HTTP_REFERER'] //上次请求地址
    $_SERVER['HTTP_USER_AGENT'] //浏览器信息
    $_SERVER['REMOTE_ARRR'] //客户端请求ip
    $_SERVER['REQUEST_URI'] // 请求中脚本名称
    $_SERVER['PATH_INFO'] // 请求中路径
```
<!-- endtab -->
{% endtabs%}
{% endfolding %}

## 抽象类和接口
{% folding cyan, 点击查看 %}
{% tabs %}
<!-- tab 抽象类（abstract） -->
1. 定义为抽象的类不能被实例化.
2. 任何一个类，如果它里面至少有一个方法是被声明为抽象的，那么这个类就必须被声明为抽象的。
3. 被定义为抽象的方法只是声明了其调用方式（参数），不能定义其具体的功能实现。
4. 继承一个抽象类的时候，子类必须定义父类中的所有抽象方法；另外，这些方法的访问控制必须和父类中一样（或者更为宽松）。
5. 例如某个抽象方法被声明为受保护的，那么子类中实现的方法就应该声明为受保护的或者公有的，而不能定义为私有的。此外方法的调用方式必须匹配，即类型和所需参数数量必须一致。例如，子类定义了一个可选参数，而父类抽象方法的声明里没有，则两者的声明并无冲突。
6. 这也适用于 PHP 5.4 起的构造函数。在 PHP 5.4 之前的构造函数声明可以不一样的.
<!-- endtab -->
<!-- tab 示例代码 -->
```PHP
abstract class Animal {
    protected $name = 'animal';

    abstract public function call();

    abstract public function run();

    public function getName() {
        return $this->name;
    }
}

class Cat extends Animal {
    protected $name = 'cat';

    public function call() {
        echo $this->getName() . ': 喵喵叫～' . PHP_EOL;
    }

    public function run() {
        echo $this->getName() . '在跑～' . PHP_EOL;
    }
}

class Dog extends Animal {
    protected $name = 'dog';

    public function call() {
        echo $this->getName() . ': 汪汪叫～' . PHP_EOL;
    }

    public function run() {
        echo $this->getName() . '在跑～' . PHP_EOL;
    }
}

$cat = new Cat;
$cat->call();
$cat->run();

$dog = new Dog;
$dog->call();
$dog->run();
```
<!-- endtab -->
<!-- tab 输出结果 -->
```PHP
    cat: 喵喵叫～
    cat在跑～
    dog: 汪汪叫～
    dog在跑～
```
<!-- endtab -->
{% endtabs%}

{% tabs %}
<!-- tab 接口（interface）-->
1. 使用接口（interface），可以指定某个类必须实现哪些方法，但不需要定义这些方法的具体内容。
2. 接口是通过 interface 关键字来定义的，就像定义一个标准的类一样，但其中定义所有的方法都是空的。
3. 接口中定义的所有方法都必须是公有，这是接口的特性。
4. 要实现一个接口，使用 implements 操作符。类中必须实现接口中定义的所有方法，否则会报一个致命错误。类可以实现多个接口，用逗号来分隔多个接口的名称。
5. 实现多个接口时，接口中的方法不能有重名。
6. 接口也可以继承，通过使用extends操作符.
7. 类要实现接口，必须使用和接口中所定义的方法完全一致的方式。否则会导致致命错误.
<!-- endtab -->
<!-- tab 示例代码 -->
```PHP
    interface Animal {
        public function call();
        public function run();
    }

    class HasName {
        protected $name = 'name';

        public function getName() {
            return $this->name;
        }
    }

    class Cat extends HasName implements Animal {
        protected $name = 'cat';

        public function call() {
            echo $this->getName() . ': 喵喵叫～' . PHP_EOL;
        }

        public function run() {
            echo $this->getName() . '在跑～' . PHP_EOL;
        }
    }

    class Dog  extends HasName implements Animal {
        protected $name = 'dog';

        public function call() {
            echo $this->getName() . ': 汪汪叫～' . PHP_EOL;
        }

        public function run() {
            echo $this->getName() . '在跑～' . PHP_EOL;
        }
    }
```
<!-- endtab -->
<!-- tab 输出结果 -->
```PHP
    cat: 喵喵叫～
    cat在跑～
    dog: 汪汪叫～
    dog在跑～
```
<!-- endtab -->
{% endtabs%}
区别
{% note simple %}
  1. 对接口的继承使用implements,抽象类使用extends
  2. 接口中不可以声明变量,但可以声明类常量.抽象类中可以声明各种变量
  3. 接口没有构造函数,抽象类可以有
  4. 接口中的方法默认为public,抽象类中的方法可以用public,protected,private修饰
  5. 一个类可以继承多个接口,但只能继承一个抽象类
  6. 接口的定义用interface,抽象类定义用abstract
{% endnote %}
{% endfolding %}

## 运算符优先级
{% folding cyan, 点击查看 %}
![](https://cdn.jsdelivr.net/gh/changrisheng/cdn@master/img/article/review/operator_priority.png)
{% endfolding %}

## 浮点数值得精度丢失问题
{% folding cyan, 点击查看 %}
{% p red, 原因：因为计算机存储是二进制，准换进制时会有精度丢失 %}
{% p green, 解决方案：先将浮点字符串化，再进行整数获取，输出可通过print %}
```PHP
    $f = 0.57;
    $f = $f * 100;
    // 输入可通过print
    printf('%d', $f);

    // 用于存储或二次计算，先将浮点字符串化，再进行整数获取
    $f = strval($f);
    var_dump($f);
    echo floor($f);
    echo intval($f);
    echo (int)($f);
```
{% endfolding %}

## Switch 问题
{% folding cyan, 点击查看 %}
> switch 只能判断整型、浮点、字符
{% endfolding %}

## 变量类型
{% folding cyan, 点击查看 %}
{% note info simple %}
  1. 普通变量
  2. 全局变量，通过global定义，可以在局部域调用全局变量，可通过$GLOBAL['XXX']读取变量的值
  3. 静态变量，通过static定义，仅在局部域中存在，执行函数离开作用域，其值也不会消失
{% endnote %}
{% endfolding %}

## 打印处理
{% folding cyan, 点击查看 %}
{% note info simple %}
  1. print() 仅输出单个变量
  2. printf() 按格式输出
  3. print_r() 格式化输出
  4. echo 输出多个变量
  5. sprintf() 按格式返回
  6. var_dump() 格式化输出，并输出变量类型
  7. var_export() 将格式化输出，加true可返回，返回内容可直接做变量使用
{% endnote %}
{% endfolding %}



{% note blue 'fas fa-bullhorn' modern %}待更新{% endnote %}
