# 01-2 spoc answer

### 在v9-cpu中如何实现时钟中断的

使用一个递增的timer，当达到timeout值后清零，若中断使能为1，则产生时钟中断，触发中断程序

### v9-cpu指令，关键变量描述有误或不全的情况

+ ssp：系统堆栈指针
+ usp：用户堆栈指针
+ cycle：CPU周期计数器
+ xcycle：cycle的四倍
+ timer：计时器
+ timeout：时钟中断的周期
+ delta：时钟步长

### 在v9-cpu中的跳转相关操作是如何实现的

比如最简单的JMP（跳到第一个操作数），首先更新xcycle，然后检查xpc是否换页，再继续执行。其他跳转操作都是类似的

### 在v9-cpu中如何设计相应指令，可有效实现函数调用与返回

将参数放在栈中，在调用时根据偏移量（8 per paramater）访问参数，将PC（返回地址）存在内存中

### emhello/os0/os1等程序被加载到内存的哪个位置,其堆栈是如何设置的

程序在内存头部，堆栈从高地址向低地址增长

### 在v9-cpu中如何完成一次内存地址的读写的

先检查虚页号，再（需要的话）进行虚实地址转换，若paging开则还需进行页表的寻找和内存地址变换

### 在v9-cpu中如何实现分页机制

内存地址为32位，前10位对应页表，中间10位对应页表中的entry，后12位为offset，即每页大小为4096

### 请编写一个小程序，在v9-cpu下，能够接收你输入的字符并输出你输入的字符

[v9_1.c](https://github.com/xunkai55/os-spoc-answer/blob/master/01-2-answer/v9_1.c)

### 请编写一个小程序，在v9-cpu下，能够产生各种异常/中断
　
[v9_2.c](https://github.com/xunkai55/os-spoc-answer/blob/master/01-2-answer/v9_2.c)
　
### 请编写一个小程序，在v9-cpu下，能够统计并显示内存大小

[v9_3.c](https://github.com/xunkai55/os-spoc-answer/blob/master/01-2-answer/v9_3.c)



