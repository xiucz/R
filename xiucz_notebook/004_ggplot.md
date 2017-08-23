# 主题


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
    require(grid) +
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
```r
p <- ggplot(data = mpg, aes(x = class, y = cty, fill = factor(year)))
## 
p1 <- p + geom_bar(stat = "identity", position = "fill")
## x轴字体角度, x轴字体大小, 距x轴偏离距离
p2 <- theme(axis.text.x=element_text(angle=90, size=8, vjust = 0.5))
## 
p3 <- p2 + theme(legend.key.size=unit(.4,'cm')) +
    theme(legend.key = element_rect(colour = 'white',
          fill = 'pink', size = 1, linetype = 1))
          
## guides(fill = guide_legend(reverse = TRUE))
```
