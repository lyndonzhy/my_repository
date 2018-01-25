# my_repository
readme_edits

#学习网址
https://www.cnblogs.com/ywliao/articles/6522971.html

sum  求和
sd   求标准差
mean 求平均值
cor  求相关系数
var  求方差函数，要求数值
cov  求协方差函数，要求数值
plot 画散点图函数
pie  画饼图函数
hist 分布柱状函数，要求数值
plot(density()) 密度函数
plot(database), pairs(database)  绘出矩阵各列的散布图 
table() 创建一个连续表,在3个聚类中分别统计各种花出现的次数
paste()函数，Concatenate vectors after converting to character.（把向量转换成字符并连接）
colnames()函数， Retrieve or set the row or column names of a matrix-like object.（设置矩阵类数据，的行或者列的名称）
sample()函数，sample takes a sample of the specified size from the elements of x using either with or without replacement.（命令是从x中随机抽取size大小的样本）

常用对象转化函数 >as.character() #转换为字符型 
-> as.numeric() #转换为数值型 
-> as.logical() #转换为逻辑型 
-> as.complex() #转化为复数型 
-> as.factor() #转化为因子型 
-> methods(as) #methods包中的全部转换函数 
-> methods(is) #methods包中全部对象类型判别函数

时间格式
将日期转换成时间戳
1、as.numeric(as.POSIXct("2017-12-05 12:20:00", format="%Y-%m-%d %H:%M:%S"))
2、as.numeric(as.POSIXct("2017-12-05", format="%Y-%m-%d"))
3、as.numeric(Sys.time())

将时间戳转换为日期格式
as.POSIXct(datetime, origin="1970-01-01 00:00:00")
datetime = 1512447600

安装函数包
导航栏（Tools） -> 第一个选项(Install Packages)

进swirl教学  library("swirl")  swirl()  
读取本地csv文件，table <- read.csv('C:/Users/zhangheying/Desktop/data.csv',header = TRUE,sep = ",")

#数据聚合
在数据库操作中，往往需要进行聚合函数的应用，这里同样可以很方面使用summarize()函数实现数据集聚合操作，语法如下：
可以用来聚合的函数有：
min()：       返回最小值
max()：       返回最大值
mean()：      返回均值
sum()：       返回总和
sd()：        返回标准差
median()：    返回中位数
IQR()：       返回四分位极差
n()：         返回观测个数
n_distinct()：返回不同的观测个数
first()：     返回第一个观测
last()：      返回最后一个观测
nth()：       返回n个观测

例子：
summarize(df2tbl, max(y))
summarize(df2tbl, n())
而且该函数还可以结合group_by()函数实现分组聚合，group_by()函数语法：
group_by(.data, ..., add = FALSE)
例子：
summarize(group_by(df2tbl,x), sum(y))


#观测筛选
如果需要将数据集中的某些观测进行筛选的话，可以使用filter()函数，语法如下：
filter(.data, ...)
.data为tbl对象
...为观测筛选条件，类似于subset()函数中的用法，但不同的是filter()函数不能筛选某些变量。
例子：
df <- data.frame(x = c('a','b','c','a','b','e','d','f'), y = c(1,2,3,4,5,6,7,8))
df2tbl <- tbl_df(df)
filter(df2tbl,x %in% c('a','b'))

#变量选取
filter()函数只能将指定条件的观测筛选出来，并不能筛选出只关心的变量，为了弥补这个缺陷，可以使用select()函数筛选指定的变量，而且比subset()函数更灵活，而且选择变量的同时也可以重新命名变量。如果剔除某些变量的话，只需在变量前加上负号“-”。之所以说他比subset()函数灵活，是因为可以在select()函数传递如下参数：
starts_with(x, ignor.case = TRUE)#选择以字符x开头的变量
ends_with(x, ignor.case = TRUE)#选择以字符x结尾的变量
contains(x, ignor.case = TRUE)#选择所有包含x的变量
matches(x, ignor.case = TRUE)#选择匹配正则表达式的变量
num_range('x', 1:5, width = 2)#选择x01到x05的变量
one_of('x','y','z')#选择包含在声明变量中的
everything()#选择所有变量，一般调整数据集中变量顺序时使用
例子：
#将df2tbl数据集中的y变量放到x变量前
select(df2tbl,y,everything())

#数据关连
我们知道，数据库中经常需要将多个表进行连接操作，如左连接、右连接、内连接等，这里dplyr包也提供了数据集的连接操作，具体如下：
inner_join#内连
left_join#左连
right_join#右连
full_join#全连
semi_join#返回能够与y表匹配的x表所有记录
anti_join#返回无法与y表匹配的x表的所记录
例子：
df2 <- data.frame(x = c('a','b','c'), z = c('A','B','C'))
df2tbl2 <- tbl_df(df2)
inner_join(x = df2tbl, y = df2tbl2, by = 'x')
semi_join(x = df2tbl, y = df2tbl2, by = 'x')
anti_join(x = df2tbl, y = df2tbl2, by = 'x')

#数据合并
在R基础包里有cbind()函数和rbind()函数实现按列的方向进行数据合并和按行的方向进行数据合并，而在dplyr包中也添加了类似功能的函数，它们是bind_cols()函数和bind_rows()函数。
例子：
mydf1 <- data.frame(x = c(1,2,3,4), y = c(10,20,30,40))
mydf2 <- data.frame(x = c(5,6), y = c(50,60))
mydf3 <- data.frame(z = c(100,200,300,400))
bind_rows(mydf1, mydf2)
bind_cols(mydf1, mydf3)
需要说明的是，bind_rows()函数需要两个数据框或tbl对象有相同的列数，而bind_cols()函数则需要两个数据框或tbl对象有相同的行数。

#管道函数
这里介绍一种dplyr包中特有的管道函数，即通过%>%将上一个函数的输出作为下一个函数的输入。
例子：根据数据集df2tbl和df2tbl2，取出z变量对应的最大y值
inner_join(x = df2tbl, y = df2tbl2, by = 'x') %>% group_by(., z) %>% summarize(., max(y))
inner_join(x = df2tbl, y = df2tbl2, by = 'x') %>% group_by(z) %>% summarize(max(y)) #也可运行

#连接数据库数据
如果需要获取MySQL数据库中的数据时，可以直接使用dplyr包中的src_mysql()函数，其功能类似于RMySQL包。src_mysql()函数语法如下：
src_mysql(dbname, host = NULL, port = 0L, user = "root", password = "", ...)
通过以上方式连接MySQL数据库后，使用tbl()函数获取数据集，tbl()函数语法如下：
tbl(src,from = '')
src为src_mysql()函数对象
from为SQL语句
例子：
src <- src_mysql('test', host = 'localhost', user = 'root', password = 'snake')
src
#获取指定表中的数据
tbl(src, from = 'diff')


