# 堆排序算法
## 算法原理
* 堆排序的时间复杂度O(nlgn)
* 堆排序是原址排序，只需要常数个额外的元素空间存储临时数据
* 堆是一个数组，数组的排列是二叉树的形式，可以看成一个近似的完成二叉树，除了最底层外，其它层都是满的，而且从左
向右填充。树上的每一个结点对应数组中的一个元素或者对象。二叉堆一般分成两个形式：最大堆和最小堆，最大堆的根节点比
子节点大，最小堆的根节点比子节点小。维护这样一个二叉堆就能利用最大堆或者最小堆的性质来快速排序。

## 伪代码实现
* PARENT //求取父节点下标
```
PARENT(i)
	return floor(i/2)
```
-----------
* LEFT //求取左子树下标
```
LEFT(i)
	return 2i
```
----------
* RIGHT //求取右子树下标
```
RIGHT(i)
	return 2i+1
```
------------
* MAX_HEAPIFY //时间复杂度O(lgn)，是维护最大堆性质的关键
```
MAX_HEAPIFY(A,i)
	l=LEFT(i)
	r=RIGHT(i)
	if i<=A.heap_size and A[i]<A[l]
		largest=l
	else
		largest=i
	if i<=A.heap_size and A[largest]<A[r]
		largest=r
	if largest!=i
		exchange A[i] with A[largest]
		MAX_HEAPIFY(A,largest)
```
---------------
* BUILD\_MAX_HEAP //具有线性时间复杂度，功能是从无序的数组构造一个最大堆
```
BUILD_MAX_HEAP(A)
	A.heap_size=A.length
	for i=floor(A.length/2) downto 1
		MAX_HEAPIFY(A,i)
```
-----------------
* HEAPSORT //时间复杂度O(nlgn)，功能是对一个数组进行原址排序
```
HEAPSORT(A)
	BUILD_MAX_HEAP(A)
	for i=A.length downto 2
		exchange A[1] with A[i]
		A.heap_size=A.heap_size-1
		MAX_HEAPIFY(A,1)
```
------------------
### 利用最大堆实现最大优先队列
#### 优先队列的应用场景：
* 共享计算机系统的作业调度，最大优先队列记录将要执行的各个作业以及它们之间的
相对优先级。当一个作业完成或者被中断后，调度器调用HEAP_EXTRACT_MAX从所有的等待作业中选出具有最高优先级的作业来执行。在任何时候
调度器都可以调用HEAP_INSERT把一个新作业加入到队列中来。
* 最小优先队列可以被用于基于事件驱动的模拟器。队列中保存要模拟的事件，每个事件都有一个发生时间作为其关键字。事件必须按照发生的
时间顺序进行模拟，因为某一事件的模拟结果可能会触发对其他事件的模拟。在每一步，模拟程序调用EXTRACT_MIN来选择下一个要模拟的事件，
当一个新事件产生时，模拟器通过调用INSERT将其插入最小优先级队列中。
* MAXIMUM
```
HEAP_MAXIMUM(A)
	return A[1]
```
-------------------
* EXTRACT_MAX
```
HEAP_EXTRACT_MAX(A)
	if A.heap_size<1
		error "heap underflow"
	max=A[1]
	A[1]=A[A.heap_size]
	A.heap_size=A.heap_size-1
	MAX_HEAPIFY(A,1)
	return max
```
--------------------
* INCREASE_KEY
```
HEAP_INCREASE_KEY(A,i,key)
	if key<A[i]
		error "new key is smaller than current key"
	A[i]=key
	while i>1 and A[PARENT(i)]<A[i]
		exchange A[i] with A[PARENT(i)]
		i=PARENT(i)
```
--------------------
* INSERT
```
HEAP_INSERT(A,key)
	A.heap_size=A.heap_size+1
	A[A.heap_size]=-inf
	HEAP_INCREASE_KEY(A,A.heap_size,key)

```



