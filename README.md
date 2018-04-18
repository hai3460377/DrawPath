SVG-PATH TO CANVAS
===
## 展示
[demo](https://hai3460377.github.io/DrawPath/dist/index.html)

## 功能

将svg路径命令字符串解析成canvas对应的api去一次性绘制,或渐进式的绘图动画

## 缘起

在知乎上看了 https://zhuanlan.zhihu.com/p/30087154

想到之前看zrender的源码时也见过一段很复杂的路径解析,同时zrender是一次性绘成的,想要渐进式动画则需要自己也来实现

A命令(弧线)的实现和分解为点集最复杂.这部分参考了zrender的一次性绘制.将其绘制转化为3x2变换矩阵来拆解点集...

## 使用

new window.DrawPath(canvas[,path])

参数:

>canvas主要提供绘图的画布以及长宽方便计算图形居中

>path为svg的路径字符串,可以是字符串或数组,字符串为单条路径绘制,数组则是同时多跳路径绘制,若初始化时没传入path 后续也可以.setPath来重设路径

>渐进动画需要分解命令为点集,线条平滑度取决于分解为几段,绘图速度同时取决于分段数以及每帧绘制段数.

## 已知bug

过短的线条分解段数过多会导致canvs无法绘出产生留空的现象

## 待完善

目前采用设置参数的方式来调试

>.setSplits(Number)用来设置分解段数

>参数可以是数字,则将所有命令都分解为固定段数

>也可以是对象,{A:10,L:5}的形式 针对不同命令分解为不同段数

>.config.times属性用来设置每桢绘制几次,用来平衡绘图速度,目前写定5次
