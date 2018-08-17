#堆排序算法
##算法原理

##伪代码实现
* PARENT
```
PARENT(i)
	return floor(i/2)
```
-----------
* LEFT
```
LEFT(i)
	return 2i
```
----------
* RIGHT
```
RIGHT(i)
	return 2i+1
```
------------
* MAX_HEAPIFY
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
* BUILD\_MAX_HEAP
```
BUILD_MAX_HEAP(A)
	A.heap_size=A.length
	for i=floor(A.length/2) downto 1
		MAX_HEAPIFY(A,i)
```
-----------------
* HEAPSORT
```
HEAPSORT(A)
	BUILD_MAX_HEAP(A)
	for i=A.length downto 2
		exchange A[1] with A[i]
		A.heap_size=A.heap_size-1
		MAX_HEAPIFY(A,1)
```
------------------
###利用最大堆实现最大优先队列
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



