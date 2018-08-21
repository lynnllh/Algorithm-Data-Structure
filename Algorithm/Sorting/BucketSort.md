# 桶排序算法
## 算法原理
* 桶排序假设输入是由一个随机过程产生，该过程将元素均匀、独立的分布在[0,1)区间上
* 桶排序的时间复杂度O(n)
* 桶排序的基本思想：桶排序将[0,1)区间划分为n个相同大小的子区间，或称为桶。然后，将n个输入数据分别放入各个桶中，由于输入数据是均匀、独立分布的，因此
一般不会在一个桶中有很多的数据。为了得到排序的结果，我们对每个桶中的数进行排序，然后遍历每个桶，按照次序把各个桶中的元素列出来即可。
* 桶排序不是原址排序 

## 伪代码实现
* BUCKETSORT
```
BUCKETSORT(A)
	n=A.length
	let B[0...n-1] be a new array
	for i=0 to n-1
		make B[i] an empty list
	for i=1 to n
		insert A[i] to B[floor(n*A[i])]
	for i=0 to n-1
		sort list B[i] with insertion sort
	concatenate the lists B[0],B[1],...,B[n-1] together in order
```