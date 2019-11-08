####Sass和Less
Sass和Less都属于CSS预处理器，CSS 预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言，为 CSS 增加了一些编程的特性，如：变量、语句、函数、继承等概念。将 CSS 作为目标生成文件，然后开发者就只要使用这种语言进行CSS的编码工作。

官网地址： http://lesscss.org/

VSCode插件：Easy LESS

官网地址： https://sass-lang.com/

VSCode插件：Easy Sass

语法：
	注释 
   变量，插值，作用域
	选择器嵌套，伪类嵌套，属性嵌套(Sass)
	运算，单位，转义，颜色
	函数
	混入，命名空间(Less)，继承
	合并，媒体查询
	条件，循环
	导入
	…
	
#####less
文件命名：xxx.less
```html

.box{ width:100px;}

// 单行注释，不会被编译出来
/*
    多行注释，就是CSS的注释方式，会被编译出来
*/

//定义变量像素
@number : 123px;
//定义关键字
@key : margin;
//定义常量
@i : 2;

//代替关键字@{}
.box@{i}{
//代替常量/数字@
    width : @number;
    height : @number;
    @{key} : auto;
}

.box3{
    height : @number;
    //定义常量作用到当前大括号作用域，不受书写前后限制
    @number : 456px;
    width : @number;
}

// ul li{}
// ul li div{}
// ul li p{}

ul{
    list-style:none;
    li{
        float:left;
        div{ margin:10px;}
        p{ margin:20px;}
    }
    &:hover{
        color : red;
        // less是没有这种属性嵌套的写法
        // font : {
        //     size : 10px;
        //     weight : bold;
        //     family : 宋体;
        // }
    }
}

@num : 100px;

.box4{
//可以进行运算，类型按左边的第一个来运算
    width : @num * 3;
    height : @num + 10em;
    margin : 10em + @num;
    font : 20px / 1.5;
    //强制不进行运算~""
    padding : ~"20px / 1.5";
    color : #010203 * 2;
}

//使用函数
.box5{
//四舍五入
    width : round(3.4px);
    //百分比
    height : percentage(0.2);
    //随机数
    margin : random();
    //开方
    padding : sqrt(25%);
}

//混入会生成css代码
.show{
    display : block;
}
//混入带参数不会生成css代码
.hide(@color){
    display : none;
    color : @color;
}
.box6{
    width : 100px;
    //混入使用不带参数
    .show;
    //混入使用带参数
    .hide(blue);
}

//命名空间
#nm(){
    .show{ display: inline-block; }
}

.box7{
    //调用命名空间
    #nm.show;
}
.box8{
//调用命名空间
    #nm.show;
}

//继承使用&:extend(）
.line{
    display : inline;
}
.box7{
    &:extend(.line);
}
.box8{
    &:extend(.line);
}

.box9{
//多参数逗号合并
    background+ : url(a.png);
    background+ : url(b.png);
    //多参数空格合并
    transform+_ : scale(2);
    transform+_ : rotate(30deg);
}

//响应式书写
.box10{
    width : 100px;
    @media all and ( min-width : 768px ){
        width : 600px;
    }
    @media all and ( min-width : 1440px ){
        width : 900px;
    }
}

//条件判断 when ( 条 件 )
@count : 3;
.get(@cn) when ( @cn > 4 ){
    width : 100px + @cn;
}
.get(@cn) when ( @cn < 4 ){
    width : 10px + @cn;
}
.box11{
    .get(@count);
}

//循环的使用，通过递归实现
@count2 : 0;
.get2(@cn) when (@cn < 3){
    .get2((@cn+1));
    .box-@{cn}{
        width: 100px + @cn;
    }
}

.get2(@count2);
//合并文件
@import './reset.less';

```
转换css后
```css
.box {
  width: 100px;
}
/*
    多行注释，就是CSS的注释方式，会被编译出来
*/
.box2 {
  width: 123px;
  height: 123px;
  margin: auto;
}
.box3 {
  height: 456px;
  width: 456px;
}
ul {
  list-style: none;
}
ul li {
  float: left;
}
ul li div {
  margin: 10px;
}
ul li p {
  margin: 20px;
}
ul:hover {
  color: red;
}
.box4 {
  width: 300px;
  height: 110px;
  margin: 110em;
  font: 20px / 1.5;
  padding: 20px / 1.5;
  color: #020406;
}
.box5 {
  width: 3px;
  height: 20%;
  margin: random();
  padding: 5%;
}
.show {
  display: block;
}
.box6 {
  width: 100px;
  display: block;
  display: none;
  color: blue;
}
.box7 {
  display: inline-block;
}
.box8 {
  display: inline-block;
}
.line,
.box7,
.box8 {
  display: inline;
}
.box9 {
  background: url(a.png), url(b.png);
  transform: scale(2) rotate(30deg);
}
.box10 {
  width: 100px;
}
@media all and (min-width: 768px) {
  .box10 {
    width: 600px;
  }
}
@media all and (min-width: 1440px) {
  .box10 {
    width: 900px;
  }
}
.box11 {
  width: 13px;
}
.box-2 {
  width: 102px;
}
.box-1 {
  width: 101px;
}
.box-0 {
  width: 100px;
}
* {
  margin: 0;
  padding: 0;
}

```
#####less
命名：xxx.scss

```html
.box{ width:200px;}

// 单行注释，不会被编译出来

/*
    多行注释，就是CSS的注释方式，会被编译出来
*/

//常量px $
$number : 123px;
//关键字 $
$key : margin;
//数字 $
$i : 2;

//关键字产量使用：#{$}
.box#{$i}{
//变量使用显示：$
    width : $number;
    height : $number;
    #{$key} : auto;
}

// Sass的作用于是有顺序的
.box3{
    $number : 456px;
    height: $number;
    width : $number;
}

ul{
    list-style:none;
    li{
        float:left;
        div{ margin:10px;}
        p{ margin:20px;}
    }
    //ul添加伪指令不要后面的空格使用：&连接
    &:hover{
        color : red;
        font : {
            size : 10px;
            weight : bold;
            family : 宋体;
        }
    }
}

$num : 100px;

.box4{
    width : $num * 3;
    //Sass中如果单位不同的话，是不能运算
    //height : $num + 20em;
    font : 20px / 1.5;
    // 默认 / 是分割的操作，加个小括号就可以运算了
    padding : (20px / 1.5);
    color : #010203 * 2;
}

//自定义函数
@function sum($n,$m){
    @return $n + $m;
}

.box5{
//四舍五入
    width : round(3.4px);
    //百分号格式
    height : percentage(0.2);
    //随机数
    margin : random();
    //开方
    padding : sqrt(25%);
    //调用自定义函数
    font-size : sum(4px , 5px);
}

//混入
@mixin show {
    display : block;
}
//混入带参数
@mixin hide($color) {
    display : none;
    color : $color;
}

.box6{
    width : 100px;
    //使用混入
    @include show;
    //混入使用带参数
    @include hide(red);
}

//继承
%line{
    display : inline;
}

.box7{
//继承使用
    @extend %line;
}
.box8{
    @extend %line;
}

$background : (
    a : url(a.png),
    b : url(b.png)
);
$tranform : (
    a : scale(2),
    b : rotate(30deg)
);
//参数合并
.box9{
//逗号合并
    background : map-values($background);
    //空格合并
    transform : zip(map-values($tranform)...);
}
//响应式
.box10{
    width : 100px;
    @media all and ( min-width : 768px ){
        width : 600px;
    }
    @media all and ( min-width : 1440px ){
        width : 900px;
    }
}

//条件判断：@if、@else
$count : 3;

.box11{
    @if($count > 4){
        width : 100px + $count;
    }
    @else{
        width : 10px + $count;
    }
}

//循环for
@for $i from 0 through 2{
    .box-#{$i}{
        width : 100px + $i;
    }
}

//导入代码
@import './reset.scss';
```
转换css后
```css
@charset "UTF-8";
.box {
  width: 200px;
}

/*
    多行注释，就是CSS的注释方式，会被编译出来
*/
.box2 {
  width: 123px;
  height: 123px;
  margin: auto;
}

.box3 {
  height: 456px;
  width: 456px;
}

ul {
  list-style: none;
}

ul li {
  float: left;
}

ul li div {
  margin: 10px;
}

ul li p {
  margin: 20px;
}

ul:hover {
  color: red;
  font-size: 10px;
  font-weight: bold;
  font-family: 宋体;
}

.box4 {
  width: 300px;
  font: 20px / 1.5;
  padding: 13.33333px;
  color: #020406;
}

.box5 {
  width: 3px;
  height: 20%;
  margin: 0.37028;
  padding: sqrt(25%);
  font-size: 9px;
}

.box6 {
  width: 100px;
  display: block;
  display: none;
  color: red;
}

.box7, .box8 {
  display: inline;
}

.box9 {
  background: url(a.png), url(b.png);
  transform: scale(2) rotate(30deg);
}

.box10 {
  width: 100px;
}

@media all and (min-width: 768px) {
  .box10 {
    width: 600px;
  }
}

@media all and (min-width: 1440px) {
  .box10 {
    width: 900px;
  }
}

.box11 {
  width: 13px;
}

.box-0 {
  width: 100px;
}

.box-1 {
  width: 101px;
}

.box-2 {
  width: 102px;
}

* {
  margin: 0;
  padding: 0;
}

img {
  display: block;
}

```
	
	