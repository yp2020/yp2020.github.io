## 概念

`Redis`  客户端执行一条指令，分为如下 4 步：

1. 发送命令
2. 命令排队
3. 命令执行
4. 返回结果

其中 1 和  4 的时间消耗在一起就是 Round Trip Time 往返时间  `RTT` 

虽然 `Redis`  提供了批量操作命令，可以有效的减少 `RTT` ,  但是大部分命令不支持批量操作，执行 n 次命令还是会在网络 IO 上浪费时间。

`Redis` 命令真正执行的时间通常在 微妙级别，所以才有 `Redis` 性能瓶颈是网络的说法。

![image-20220321170841873](https://wayne6.oss-cn-hangzhou.aliyuncs.com/img/image-20220321170841873.png)

Pipeline 流水线，能够将一组命令进行组装，一次性发送给服务端，也就是只经过了 1 个 `RTT` ,然后再将这一组的 `Redis ` 命令的执行结果按照顺序返回给客户端。



## 特点

1. Pipeline 执行速度一般比逐条执行要快
2. 客户端和服务端的网络延时越大，Pipeline 的效果越明显，因为 延时越大，`RTT` 越大

![image-20220321170806346](https://wayne6.oss-cn-hangzhou.aliyuncs.com/img/image-20220321170806346.png)

## 与原生批量命令的对比

| Pipeline                                                     | 原生批量操作命令              |
| ------------------------------------------------------------ | ----------------------------- |
| 不是原子性的                                                 | 是原子性的                    |
| 支持多个命令                                                 | 一个命令，对应多个 key 的操作 |
| 需要客户端和服务端的共同实现，而且在 Pipeline 可以在高级语言客户端中使用，而且更加受欢迎。 | 服务端支持实现                |

## 最佳实践

为避免阻塞，可以将一次包含大量命令的 Pipeline 拆分成为多个较小的 Pipeline 来完成。