# my_repository
readme_edits

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


时间格式
将日期转换成时间戳
1、as.numeric(as.POSIXct("2017-12-05 12:20:00", format="%Y-%m-%d %H:%M:%S"))
2、as.numeric(as.POSIXct("2017-12-05", format="%Y-%m-%d"))
3、as.numeric(Sys.time())

将时间戳转换为日期格式
as.POSIXct(datetime, origin="1970-01-01 00:00:00")
datetime = 1512447600
