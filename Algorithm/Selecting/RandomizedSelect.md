# 选择算法
## 问题描述
在一个由n个元素组成的集合中，第i个顺序统计量是该集合中第i小的元素。该选择算法就是选出这个元素。
## 算法原理
* 快速随机选择算法的期望时间复杂度O(n)[在元素互异的情况下]，最坏情况时间复杂度O(n^2)
* 快速随机选择算法是利用分治思想的一种选择方法，其在随机快速排序的基础之上构建出来的。他将原数组划分成三个部分，主元和都比主元小的一组数，以及都比主元大的一组数，然后判断顺序统计量在哪一个区域，并对该区域的子数组递归使用选择算法。因为随机选择算法只要处理含有顺序统计量的那个半边，因此他的时间复杂度比快速排序要快，期望时间复杂度能够达到线性。

## 伪代码实现
* RANDOMIZED_SELECT
```
RANDOMIZED_SELECT(A,p,r,i)
	if p==r
		return A[p]
	q=RANDOMIZED_PARTITION(A,p,r)
	k=q-p+1
	if i==k
		return A[q]
	else if i<k
		return RANDOMIZED_SELECT(A,p,q-1,i)
	else
		return RANDOMIZED_SELECT(A,q+1,r,i-k)
	
```
--------------
* RANDOMIZED_PARTITION(A,p,r)
```
RANDOMIZED_PARTITION(A,p,r)
	i=RANDOM(p,r)
	exchange A[r] with A[i]
	x=A[r]
	i=p-1
	for j=p to r-1
		if A[j]<x
			i=i+1
			exchange A[i] with A[j]
	exchange A[i+1] with A[x]
	return i+1
```

