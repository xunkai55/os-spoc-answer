# 07-2 SPOC Answer

2012011486 张洵恺

2012013290 韩珊

学号较小者模40余6，选择第6题。

## 第六题

> 设有一个可以装A、B两种物品的仓库，其容量无限大，但要求仓库中A、B两种物品的数量满足下述不等式： -M≤A物品数量-B物品数量≤N 其中M和N为正整数。试用信号量和PV操作描述A、B两种物品的入库过程。

### Hint

> Semaphore：一共需要2个Semaphore，A、B各一个，表示A、B在差值满足要求的情况下各还可以放入多少个。同时用depot保证往仓库里面放置物品是互斥的。

> Monitor：首先用1个变量表示A与B的差值，然后判断A-B是否满足-M<=A-B<=N。在达到右临界值时就开始等待条件变量，在B往仓库里面加的时候就发送signal。

### 实现

使用Python语言和threading库实现。代码见[sem6.py](07-2-answer/sem6.py)

