
+ **[数组](#数组)** | >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
	
	+ [二分查找写错遍历条件](#二分查找写错遍历条件)
	
+ **[链表](#链表)** | >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
	
	+ [遍历指针更新顺序有误](#遍历指针更新顺序有误)
	+ [合并排序没有断开中位指针](#合并排序没有断开中位指针)
	+ [双向链表移动节点未更新后向指针](#双向链表移动节点未更新后向指针)
	
+ **[树图](#树图)** | >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
	
	+ [DFS递归函数误传深度](☢️%20算法逻辑错误%20Logical%20Errors.md#DFS递归函数误传深度)


---
## 数组


### 二分查找写错遍历条件

+ **二分查找 - `while`循环条件误写为`low == high`**：若查找目标不存在，两个指针在最后一步搜索会互相跨越而不触发终止，可能导致数组越界；二分查找的正确循环条件应为`low <= high`

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


---
## 链表

### 遍历指针更新顺序有误

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

### 合并排序没有断开中位指针

+ **链表合并排序 - 递归传参时没有断开左右子链表之间的节点指针**：链表递归传参一般传的是头节点指针，如果不断开左右子链表之间的节点指针，传左侧子链表指针就相当于把整段链表传入下一层递归，会导致无尽递归。

```python
def mergeSort(head: Optional[ListNode]) -> None:
	
	# 弗洛伊德算法找链表中位
	slow, slow_last, fast = head, head, head
	while fast and fast.next:
		fast = fast.next.next
		slow_last = slow
		slow = slow.next 
	
	# ！！！断开左右两段链表！！！
	slow_last.next = None
	
	left = mergeSort(head)
	right = mergeSort(slow)
	
	# 合并
	pass
```

### 双向链表移动节点未更新后向指针

+ **双向链表移动节点时忘记更新`prev`指针**：在双向链表插入节点或移动节点时，必须确保所有相邻节点的前向和后向指针都已更新，否则会造成链表结构混乱。

```python
# 普通单向链表
nxt = dummy.next
new = ListNode(next = nxt)
dummy.next = new

# 双向链表
nxt = dummy.next
new = ListNode(next = nxt, prev = dummy)
dummy.next = new
if new.next: new.next.prev = new # 容易漏写
```


---
## 树图

### DFS递归函数误传深度

+ **树DFS递归 - 计算深度时误将深度作为参数**：使用DFS递归检测树的深度时不需要将当前指向的节点深度作为参数，只需在递归返回时逐层加一便可得到树的深度。

```cpp
// 正确写法
int dfs(TreeNode* p){
	if (p == nullptr) return 0;
	else return max(dfs(p->left), dfs(p->right)) + 1;
}
```
