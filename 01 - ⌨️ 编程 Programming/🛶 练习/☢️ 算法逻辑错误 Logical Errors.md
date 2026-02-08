
+ **二分查找 - `while`循环条件误写为`low != high`**：若查找目标不存在，两个指针在最后一步搜索会互相跨越而不触发终止，可能导致数组越界；二分查找的正确循环条件应为`low <= high`

```python
# 正确写法
def binarySearch(arr, val) -> int:
	low = 0
	high = len(arr) - 1
	
	while low <= high:
		mid = low + (high - low) / 2 # 避免溢出
		if (val < arr[mid]) high = mid - 1
		else if (val > arr[mid]) low = mid + 1
		else return mid
	return -1 

arr = [1, 2, 4, 5]
```

+ **DFS树递归 - 计算深度时误将深度作为参数**：使用DFS递归检测树的深度时不需要将当前指向的节点深度作为参数，只需在递归返回时逐层加一便可得到树的深度。

```cpp
// 正确写法
int dfs(TreeNode* p){
	if (p == nullptr) return 0;
	else return max(dfs(p->left), dfs(p->right)) + 1;
}
```

+ **链表换向 - 上一节点指针`last_cur`在当前节点指针`cur`更新后才更新**：正确的逻辑是在当前节点`cur`更新之前，更新`last_cur = cur`，否则`last_cur`总是等于`cur`，起不到缓存上一节点的作用

```python
last_cur = None
cur = head
while cur:
	nxt = cur.next
	cur.next = last_cur
	# 错误写法
	cur = nxt 
	last_cur = cur
	# 正确写法
	last_cur = cur
	cur = nxt
```

+ ****
