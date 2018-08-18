#快速排序算法
##算法原理
* 快速排序算法的期望时间复杂度O(nlgn)[在元素互异的情况下]，最坏情况时间复杂度O(n^2)
* 快速排序是原址排序
* 快速排序是利用分治思想的一种排序方法，他将原数组划分成三个部分，主元和都比主元小的一组数，以及都比主元大
的一组数，然后对子数组递归使用快速排序，因为子数组是原址排序的，因此不需要合并，原数组已经有序了。

##伪代码实现
* QUICKSORT
```
QUICKSORT(A,p,r)
	if p<r
		q=PARTITION(A,p,r)
		QUICKSORT(A,p,q-1)
		QUICKSORT(A,q+1,r)
```
--------------
* PARTITION(A,p,r)
```
PARTITION(A,p,r)
	x=A[r]
	i=p-1
	for j=p to r-1
		if A[j]<x
			i=i+1
			exchange A[i] with A[j]
	exchange A[i+1] with A[x]
	return i+1
```
--------------
##随机快速排序算法
* QUICKSORT
```
QUICKSORT(A,p,r)
	if p<r
		q=RANDOMIZED_PARTITION(A,p,r)
		QUICKSORT(A,p,q-1)
		QUICKSORT(A,q+1,r)
```
* RANDOMIZED_PARTITION
```
RANDOMIZED_PARTITION(A,p,r)
	i=RANDOM(p,r)
	exchange A[i] with A[r]
	return PARTITION(A,p,r)
```

