# 处理机调度与死锁

## 调度层次

处理机调度算法目标
资源利用率
公平性
平衡性
策略强制执行

### 高级调度

又称作业调度
仅限批处理系统
过程：选择作业，创建进程，分配资源，插入队列

- 主要任务

	- 1.判断接纳多少作业
	- 2.判断接纳哪些作业

- 主要算法

	- 先来先服务算法(FCFS)

		- 特点

			- 有利于长作业，不利于短作业
			- 有利于CPU繁忙型作业，不利于I/O型作业
			- 作业平均等待时间长
			- 吞吐量不高

		- 性能衡量标准

			- 平均周转时间

			  周转时间=完成时间-到达时间

			- 平均带权周转时间

			  带权周转时间=周转时间/运行时间

	- 短作业(进程)优先调度算法(SJF)

		- 特点

			- 有效降低平均等待时间
			- 提高系统吞吐量
			- 对长作业不利
			- 未考虑到作业紧迫程度

	- 优先级调度算法

		- 特点

			- 基于作业紧迫程度进行调度

	- 高相应比优先调度算法

		- 特点

			- 优先权可变化
			- 有利于短作业
			- 长作业优先级越来越高

### 低级调度

又称进程调度
所有系统都具备这种调度
过程：根据算法，从就绪队列选择进程进入处理机

- 进程调度方式

	- 非抢占方式
	- 可抢占方式

- 进程调度算法

	- (时间片)轮转调度算法(分时系统)

		- 基本原理

			- 将CPU时间划成大小相同的时间片
			- 进程按先后顺序排成队列

		- 时间片大小的确定

			- 时间片过小，开销大
			- 时间片过大，退化为FCFS

	- 优先级调度算法

		- 优先权类型

			- 静态优先权
			- 动态优先权

	- 多级反馈队列调度算法

		- 基本原理

			- 设置多个就绪队列
			- 分配大小不同，逐级翻倍的时间片
			- 每一级按照FCFS算法调度
			- 一级为空，调度下一级
			- 抢占式策略

		- 特点

			- 性能好
			- 可以考虑到各个进程

	- 实时调度

		- 可调度的条件

			- 
			- m个硬实时任务
			- 每个任务处理时间为C
			- 周期时间为P

		- 调度算法

			- 最早截止时间优先算法(EDF)

				- 根据任务的开始截止时间划分优先级

			- 最低松弛度优先算法

				- 根据任务松弛度划分优先级(松弛度低优先级高)

### 中级调度

过程：暂时不用的进程，从内存调入外存

## 死锁

死锁是指两个或多个进程由于资源竞争而造成的一种僵局

### 产生死锁的原因

- 竞争资源引起进程死锁
- 进程推进顺序不当引起死锁

### 产生死锁的必要条件

- 互斥条件
- 请求保持条件
- 不可抢占条件
- 循环等待条件

### 处理死锁的基本方法

- 预防死锁

	- 破坏“请求保持”条件
	- 破坏“不可抢占”条件
	- 破坏“循环等待”条件

- 避免死锁

	- 系统状态

		- 安全状态

			- 保证安全状态则无死锁

		- 不安全状态

	- 避免死锁的算法

		- 银行家算法

			- 安全性算法

- 死锁的检测与解除

	- 死锁定理

	  死锁定理：某状态是死锁状态的充分条件是，当且仅当此状态资源分配图是不可完全简化的。

	- 死锁检测算法
	- 死锁的解除

		- 剥夺资源
		- 撤销进程
