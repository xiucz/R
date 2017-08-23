## RColorBrewer
```r
library(RColorBrewer)

## seq连续型
display.brewer.all(type = "seq")
## div离散型
display.brewer.all(type = "div") 
## qual极端型
display.brewer.all(type = "qual")

##可以使用brewer.pal(数值,"<某组渐变颜色的名称>")来获取该组颜色的全部颜色
```

## 自动产生颜色函数heat.colors
```r
> barplot(rep(1,30),col = terrain.colors(30))
> barplot(rep(1,30),col = cm.colors(30))
> barplot(rep(1,30),col = heat.colors(30))
> barplot(rep(1,30),col = topo.colors(30))
```

## 背景色
### 只设置坐标系内的背景颜色
```r
plot(rnorm(100),type="n")
#x的值就是图中大矩形的四个顶点的坐标
x<-par("usr")
#对四个顶点坐标所表示的区域进行背景颜色的设置
rect(x[1],x[3],x[2],x[4],col="lightgray")
#再在背景上标出散点
points(rnorm(1000))
```
### 设置标题、坐标轴标号等颜色
```r
#col.axis="blue"---设置坐标轴刻度颜色
#col.lab="red"---设置横纵坐标轴标题颜色
#col.main="darkblue"--设置标题颜色
plot(rnorm(100),main="Plot Title",col.axis="blue",col.lab="red",col.main="darkblue")
```

## ggsci
https://ggsci.net/  
https://cran.r-project.org/web/packages/ggsci/vignettes/ggsci.html

## ggtech
https://github.com/ricardo-bion/ggtech

## ggthemr
https://github.com/cttobin/ggthemr
## 配色网站
https://color.adobe.com/zh/create/color-wheel/?copy=true  
http://color.aurlien.net/  
http://www.0to255.com  
http://colorblender.com/

## Reference_info
