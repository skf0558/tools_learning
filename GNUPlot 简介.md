# GNUPlot 简介

ZUT-孙昆峰

## 1.调用文件

绘制在D盘下的test文件

```
plot ‘D:\test'
```



```
plot  sin(x)
```





## 2.设置x,y坐标范围

set xrange[xmin:xmax]

set yrange[ymin:ymax]

自动设置范围：

set autoscale  



只设定x范围，可以简写：

```
plot [0:5] sin(x)
```

只设定y范围，可以简写

```
plot [][0:1] sin(x)
```

设定一边范围，y小于0

```
plot [][:0]  sin(x)
```



## 3.设置坐标轴

set xlabel 'xlabel' ;

set ylabel 'ylabel'

设置对数坐标

set logscale

取消对数坐标

unset logscale

## 4.设置标题

set title 'title'

多个标题

plot sin(x) title 'y=sin(x) ', x  title 'y=x'

标题位置

 set key x,y

set key 8,-0.8

plot [-10:10] [-1:1] sin(x) title 'sin'

将title放置到(8,-0.8)坐标处。

标题默认位置：

set key default

不显示标题

unset key

设置标题框

set key box

取消标题框

set key nobox



## 5.同时绘制多个

plot f1(x),f2(x),f3(x)



## 6 网格,线型

set grid; plot cos(x)

取消网格

unset grid





plot sin(x) with line linetype 3 linewidth 2

简写：

plot sin(x) w l lt 3 lw 2

表示：线类型是3，线宽2



with point pointtype 3 pointsize 2

=

w  p pt 3 ps 2

表示：用点画，点类型是3，点大小2

其中with 之后的类型可以是以下这些类型中的一种

{ lines, points, linespoints, impulses, dots, steps, fsteps, histeps, errorbars, labels, xerrorbars,
yerrorbars, xyerrorbars, errorlines, xerrorlines, yerrorlines, xyerrorlines, boxes, histograms, filledcurves, boxerrorbars, boxxyerrorbars, financebars, candlesticks, vectors, image, rgbimage , pm3d}.
一些常用基本类型：
with linespoints 画点线
linestyle 连线风格（包括linetype，linewidth等）
linetype 连线种类
linewidth 连线粗细
linecolor 连线颜色
pointtype 点的种类
pointsize 点的大小







## 7.输出图片

set terminal ’类型‘

set output '文件名'

类型为png,jpeg,gif等

例如：

```
set terminal png

set output 'sinx.png'

plt sin(x)
```

设置图片大小

set size m,n

m,n 为放大缩小倍数

set size 1.2,0.5 

表示长设置为当前1.2倍，宽为当前0.5倍。

## 8.三维splot

```
splot x*y
```



## 综合例子

```
set term post eps color "Helvetica" 24  #输出eps格式，而且带颜色，另外，字体使用helvetica, 24号。

set output "thrput.eps"

set ylabel "Throughput (pkts/second)"

set key left top

plot "thr_node8.data" u ($1/1000):2 w lp lt 1 linecolor rgb "red" pt 2 ps 2 lw 1.5 title "App1", "thr_node4.data" u ($1/1000):2 w lp lt 1 linecolor rgb "blue" pt 4 ps 2 lw 1.5 title "App2"
```



## 9一页多图

set multiplot