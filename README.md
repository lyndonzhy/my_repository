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

进swirl教学  library("swirl")  swirl()  
读取本地csv文件，table <- read.csv('C:/Users/zhangheying/Desktop/data.csv',header = TRUE,sep = ",")
