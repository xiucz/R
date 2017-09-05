```r
library(data.table)
mtcars_dt <- data.table(mtcars)
```
## 数据筛选
### 行筛选
```r
mtcars_dt[cyl==8]
```
### 列筛选
```r
mtcars_dt[,.(mpg,cyl,hp)]
```

## 选取子集
```r
## subset是行满足条件
## select是列满足条件
subset(mtcars_dt,cyl==8,select =c('mpg','cyl','disp'))
```

## 增删变量
```r
## 单变量添加
> DT[i, LHS:=RHS, by=...]
# LHS为新建的变量，RHS为该变量的计算方式

## 双变量添加
> DT[i, c("LHS1","LHS2") := list(RHS1, RHS2), by=...]

## 多变量添加，注意`:=`
> DT[i, `:=`(LHS1=RHS1,LHS2=RHS2,...), by=...]

mtcars_dt[,`:=`(mpg_reciprocal=1/mpg,new=cyl+gear)]
```

## 删除变量
```r
mtcars_dt[,mpg_reciprocal:=NULL]
```

## 分组汇总
```r
mtcars_dt[,.(mean_mpg = mean(mpg), sum_disp = sum(disp)),by=list(cyl)]
```

## Reference_info
http://youngspring1.github.io/post/2016/2016-03-13-datatable1/

http://www.cnblogs.com/nxld/p/6059570.html
