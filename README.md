# gggap
Easy to define segments in y-axis for 'ggplot2'.

[![CRAN RStudio mirror
downloads](http://cranlogs.r-pkg.org/badges/ggap)](http://www.r-pkg.org/pkg/ggap)

## 安装

You can install `ggap` from CRAN:

``` r
install.packages("ggap")
```

Or get the development version from Github:

``` r
# install.packages("devtools")
devtools::install_github("cmoralesmx/ggap")
```

## 使用

``` r
data(mtcars)
library(ggplot2)
p<-ggplot(data = mtcars, aes(x = gear, fill = gear)) +
    geom_bar() +
    ggtitle("Number of Cars by Gear") +
    xlab("Gears")

#single segments and missing tick_width
ggap(plot=p,
       segments=c(5,10),
       ylim=c(0,50))
#tick_width can be one or more numbers
ggap(plot=p,
       segments=c(5,10),
       tick_width = c(1,10),
       ylim=c(0,50))
#segments list cantains more than one number vectors
ggap(plot=p,
       segments=list(c(2.5,4),c(5,10)),
       tick_width = c(1,0.5,10),
       ylim=c(0,50))
#rel_heights can set the relative height for segments and segmented y-axis
ggap(plot=p,
       segments=list(c(2.5,4),c(5,10)),
       tick_width = c(1,0.5,10),
       rel_heights=c(0.2,0,0.2,0,1),
       ylim=c(0,50))
#reversed y-axis
p<-ggplot(data = mtcars, aes(x = gear, fill = gear)) +
    geom_bar() +
    ggtitle("Number of Cars by Gear") +
    xlab("Gears")+
    scale_y_continuous(trans = 'reverse')
#single segments and missing tick_width
ggap(plot=p,
       segments=c(10,5),
       ylim=c(15,0))
#for facet()
library(ggplot2)
p<-ggplot(mtcars,aes(mpg,hp))+geom_point()
p1<-p+facet_wrap(~cyl,scales="free")
ggap(plot = p1,ylim = c(60,200),segments = c(100,120))
```

