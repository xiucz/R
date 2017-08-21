
```r
library(ggplot2)
packageVersion("ggplot2")
head(mpg)
```
```r
p <- ggplot(data = mpg, aes(x = class, y = cty, fill = factor(year)))
## 
p1 <- p + geom_bar(stat = "identity", position = "fill")
## x轴字体大小，角度，
p2 <- theme(axis.text.x=element_text(angle=90, size=8, vjust = 0.5))
## 
p3 <- p2 + theme(legend.key.size=unit(.4,'cm')) +
    theme(legend.key = element_rect(colour = 'white',
          fill = 'pink', size = 1, linetype = 1))
##
```