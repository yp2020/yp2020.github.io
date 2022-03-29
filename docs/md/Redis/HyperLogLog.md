HyperLogLog 并不是一种数据结构，实际类型为字符串类型。而是一种基数算法。

## 命令

1. 添加元素，添加成功就返回 1

   > pfadd key element [element...]

2. 计算独立用户数

   > pfcount key [key...]

3. 合并

> pfmerge destkey sourcekey [sourcekey..]

HyperLogLog 的优势在于 内存占用量极小，但是缺点在于会有一定的误差率。



![image](https://wayne6.oss-cn-hangzhou.aliyuncs.com/img/202203291656610.png)





![image_1](https://wayne6.oss-cn-hangzhou.aliyuncs.com/img/202203291656088.png)
