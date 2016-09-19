[TOC]
# 边框 #
<!-- ## 目录 ##
* [1、边框](#1) *
* [2、用border画图](#2) *
    * [2.1、三角形](#2) *
* [3、圆角效果](#3) * -->
## 1、边框 ##
```css
div{
    /*border: border-width border-style border-color; 这三个属性都可以分为4个方向分别设置，按顺序为上、右、下、左，都允许1-4个值*/
    border: 1px solid #ccc;
    /*设置上边框为实线，右边框为点状，下边框为虚线，左边框为双线*/
    border-style: solid dotted dashed double;
}
```

## 2、圆角效果 ##
`border-radius`，IE8及以下不支持。
```css
div{
    /*分别设置，左上、右上、右下、左下*/
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
    border-bottom-left-radius: 5px;
    /*缩写，按顺序左上、右上、右下、左下*/
    border-radius: 5px 5px 5px 5px;
    /*缩写，第一个值为左上；第二个值为右上，左下；第三个值为右下*/
    border-radius: 5px 6px 5px;
    /*缩写，第一个值为左上，右下；第二个值为右上，左下*/
    border-radius: 5px 6px;
    /*缩写，一个值设置四个角*/
    border-radius: 5px;
}
```

## 3、用css画图 ##
### 3.1、三角形 ###
原理：利用相邻两个边框的接壤处分配原则  
![原理](https://github.com/yuzhantian/css-library/raw/master/library-imgs/border-base.png)
```css
div{
    border-top:30px solid blue;
    border-right:30px solid black;
    border-bottom:30px solid red;
    border-left:30px solid green;
    width:0px; height:0px;
}
```
![三角形](https://github.com/yuzhantian/css-library/raw/master/library-imgs/border-triangle.png)
```css
.triangle-up {border-bottom: 50px solid #00545b; width: 0; height: 0; border-left: 30px solid transparent; border-right: 30px solid transparent;}
.triangle-right {border-left: 50px solid #00545b; width: 0; height: 0; border-top: 30px solid transparent; border-bottom: 30px solid transparent;}
.triangle-down { border-top: 50px solid #00545b; width: 0; height: 0; border-left: 30px solid transparent; border-right: 30px solid transparent; }
.triangle-left {border-right: 50px solid #00545b; width: 0; height: 0; border-top: 30px solid transparent; border-bottom: 30px solid transparent;}

.triangle-left-top{border-left: 30px solid #00545b;border-top: 30px solid #00545b; border-right: 30px solid transparent; border-bottom: 30px solid transparent; width: 0; height: 0;}
.triangle-right-top{border-right: 30px solid #00545b;border-top: 30px solid #00545b; border-left: 30px solid transparent; border-bottom: 30px solid transparent; width: 0; height: 0;}
.triangle-right-bottom{border-right: 30px solid #00545b;border-bottom: 30px solid #00545b; border-left: 30px solid transparent; border-top: 30px solid transparent; width: 0; height: 0;}
.triangle-left-bottom{border-left: 30px solid #00545b;border-bottom: 30px solid #00545b; border-right: 30px solid transparent; border-top: 30px solid transparent; width: 0; height: 0;}
```
```html
<!-- 六芒星 -->
<div>
    <div style="width: 0; height: 0; border-left: 30px solid transparent; border-right: 30px solid transparent; border-bottom: 50px solid #00545b;"></div>
    <div style="width: 0; height: 0; border-left: 30px solid transparent; border-right: 30px solid transparent; border-top: 50px solid #00545b;transform: translateY(-35px);"></div>
</div>
```
### 3.2、圆形 ###
效果如下，代码详见[demo.css](https://github.com/yuzhantian/css-library/blob/master/border/demo.css)
![圆形](https://github.com/yuzhantian/css-library/raw/master/library-imgs/border-circle.png)

## 4、页面左上角卷角效果 ##
效果如下，代码详见[left-triangle.html](https://github.com/yuzhantian/css-library/blob/master/border/left-triangle.html)
![左上角卷角效果](https://github.com/yuzhantian/css-library/raw/master/library-imgs/border-left-triangle.png)