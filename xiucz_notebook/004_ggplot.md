```
> library("ggplot2");packageVersion("ggplot2")
[1] ‘2.2.1’
```
# theme


参数|设置内容|继承自
-|-|-
line|所有线属性 	 
rect|所有矩形区域属性 	 
text|所有文本相关属性 	 
title|所有标题属性 	 
axis.title|坐标轴标题|text
axis.title.x|x轴属性|axis.title
axis.title.y|y轴属性|axis.title
axis.text|坐标轴刻度标签属性|text
axis.text.x|属性和继承和前面类似，不再重复 	 
axis.text.y|	  	 
axis.ticks|坐标轴刻度线|line
axis.ticks.x| 	  	 
axis.ticks.y|	  	 
axis.ticks.length|刻度线长度 	 
axis.ticks.margin|刻度线和刻度标签之间的间距 	 
axis.line|坐标轴线|line
axis.line.x| 
axis.line.y|	  	 
legend.background|图例背景|rect
legend.margin|图例边界 	 
legend.key|图例符号 	 
legend.key.size|图例符号大小 	 
legend.key.height|图例符号高度 	 
legend.key.width|图例符号宽度 	 
legend.text|图例文字标签 	 
legend.text.align|图例文字标签对齐方式 	0为左齐，1为右齐
legend.title|图例标题|text
legend.title.align|图例标题对齐方式 	 
legend.position|图例位置|left, right, bottom, top, 两数字向量
legend.direction|图例排列方向|"horizontal" or "vertical"
legend.justification|居中方式|center或两数字向量
legend.box|多图例的排列方式|"horizontal" or "vertical"
legend.box.just|多图例居中方式 	 
panel.background|绘图区背景|rect
panel.border|绘图区边框|rect
panel.margin|分面绘图区之间的边距 	 
panel.grid|绘图区网格线|line
panel.grid.major|主网格线 	 
panel.grid.minor|次网格线 	 
panel.grid.major.x| 	  	 
panel.grid.major.y|	  	 
panel.grid.minor.x|	  	 
panel.grid.minor.y|	  	 
plot.background|整个图形的背景 	 
plot.title|图形标题 	 
plot.margin|图形边距|top, right, bottom, left
strip.background|分面标签背景|rect
strip.text|分面标签文本|text
strip.text.x| 	  	 
strip.text.y|



```r
theme_micro <- function(..., base_size = 12, bg = 'white') {
    require(grid)
    theme_classic(...) +
        theme(rect=element_rect(fill=bg),
              plot.margin=unit(rep(0.5,4), 'lines'),
              panel.background=element_rect(fill='transparent', color='transparent'),
              panel.border=element_rect(fill='transparent', color='transparent'),
              panel.grid=element_blank(),
              axis.title = element_text(color='black', vjust=0.1),
              axis.ticks.length = unit(-0.3,'lines'),
              axis.ticks = element_line(colour = 'black'),
              axis.ticks.margin = unit(0.8,"lines"),
              legend.title=element_blank(),
              legend.key=element_rect(fill='transparent', color='transparent'))
}

```
----
# 
```r
library(ggplot2)
packageVersion("ggplot2")
head(mpg)
```

# barplot

```r
mtcars$cyl <- factor(mtcars$cyl)
p <- ggplot(data = mpg, aes(x = wt, y = mpg, fill = factor(year)))
## 
p1 <- p + geom_bar(stat = "identity", position = "fill", width = 0.5)
## x轴字体角度, x轴字体大小, 距x轴偏离距离
p2 <- theme(axis.text.x=element_text(angle=90, size=8, vjust = 0.5, color="black", face = "bold"))
## 
p3 <- p2 + theme(legend.key.size=unit(.4,'cm')) +
    theme(legend.key = element_rect(colour = 'white',
          fill = 'pink', size = 1, linetype = 1))
          
## guides(fill = guide_legend(reverse = TRUE))
#        scale_y_continuous(breaks = c(0.00, 0.25, 0.50, 0.75, 1.00), labels = c("0", "25", "50", "75", "100")) 

# geom_bar(stat = "identity", width = 0.5) +   ## 修改柱条的宽度

# 如何自定义ggplot2中各组数据输出的次序
但是我想要的次序是UPS2only, UPS2yeast, UPS2mouse，因此需要重新定义exp的因子水平
这里只需调整melt之后的因子水平即可：

ups.melt$exp=factor(ups.melt$exp, levels=c("UPS2only","UPS2yeast","UPS2mouse")); #修改exp的因子水平顺序，从而确定X轴输出的顺序

#scale_y_continuous(expand=c(0,0))
#scale_y_continuous(limits=c(0,max(toPlot$value)))
# scale_x_continuous(expand = c(0, 0), limits = c(0,5))

#theme(axis.line = element_line(size=1, colour = "black"))


> ggplot(data = mtcars, aes(x = cyl, y = mpg, fill=factor(gear))) + geom_bar(position = "fill", stat="identity")
```

#　geom_point()
```r
ggplot(data=mtcars, aes(x=wt, y=mpg)) + geom_point()
```
```
# shape参数修改图形的形状
ggplot(data=mtcars, aes(x=wt, y=mpg)) +geom_point(shape=17)

# size参数修改点的大小
ggplot(data = mtcars, aes(x=wt, y=mpg))+geom_point(size=5)

# color参数修改点的颜色
ggplot(data=mtcars, aes(x=wt, y=mpg))+geom_point(color="red")

ggplot(data=mtcars, aes(x=wt, y=mpg, color=cyl, shape= cyl))+ geom_point(size=3) +    
  scale_color_brewer(palette = "Accent")+ scale_shape_manual(values = c(2, 9, 16))
```



```
# legend
```
p <- qplot(Sepal.Length,Petal.Length,data=iris,geom="point",colour = Species)
```

## 去掉图例
```
p + theme(legend.position="none"
```
## 图例位置
```
b <- qplot(Species,Sepal.Width,data=iris,geom="boxplot",fill = Species)+scale_fill_brewer(palette = "Pastel2")
b+theme(legend.position="top")
b+theme(legend.position=c(.92,.9))
```
## 移除图例标题
```
b + guides(fill = guide_legend(title = NULL))
```

## 去掉背景
```r
legend.background = element_blank()
```

## 去掉KEY的背景
```
legend.key = element_blank()
```
