# PriorityQueue (Heap)
### 1. Time Complexity for PQ method
- O(log n) time for the enqueing and dequeing methods (offer, poll, remove() and add)

- O(n) for the remove(Object) and contains(Object) methods

- O(1) for the retrieval methods (peek, element, and size)
### 2. Binary Heap
- Binary Heap
	1. Child.val < parent.val
	2.  Always complete tree
	3. Index of leftChild = index of parent x 2 + 1
	4. Index of rightChild = index of parent x 2 + 2
	5.  Index of parent = (index of child – 1 ) / 2
	6. Unsorted but follow rule above

- Operation Time Complexity
	- Insert : O(log(n))
	- Update : O(log(n))
	- Get/top : O(1)
	- Pop : O(log(n))
	- Heapify : O(n)