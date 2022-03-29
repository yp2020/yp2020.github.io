bitmaps 实际上是字符串，

在 `Redis` 中，字符串都是以二进制的方式来存储的。也就是一位一位的，`bitmaps`可以对字符串的位进行操作。

例如 set k1 a 

a 对应的 ASCII 码是 97，

97 转为 二进制是 01100001，

BIT 相关的命令就是对二进制进行操作的。

## BIT 命令

1. 设置值 

> setbit key offset  value 

设置 key 对应的 value 在 offset 处的 bit 值 offset 从 0 开始

2. 获取值

>  getbit key offset

得到 key 对应的 value 在 offset 处的 bit 值。

如果 offset 不存在，那么返回结果为 0 

3. 获取指定范围 2进制数据的 1 的个数

> bitcount k1 [start] [end]

[start] [end] 代表起始和结束字节数。一个字节 8 位。

4. Bitmaps 间的运算

> bitop op destkey key[key....]

bitop 是一个复合操作，可以做多个 Bitmaps 的 and ,or，not, xor 操作的结果保存在 destkey 中。



## Bitmaps 分析

如果网站每天的活跃用户很多，可以 bitmaps 来存储活跃的用户。 用户编号为 0123456，对应的就是 1和 0

这个可以用来统计一些数据，比如签到记录

如果用string 来存签到记录 ，太浪费。一年就是 365个 key-value 

直接用 bit 来存储，就是 1 到， 0未到，统计 1 的个数即可。





官方文档在这里 

[http://www.redis.cn/commands/bitfield.html](http://www.redis.cn/commands/bitfield.html)

