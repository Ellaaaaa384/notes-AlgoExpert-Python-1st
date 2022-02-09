#### Linked list construction

##### 题目：double linked list的插入、删除、移动

##### 要点：

self到底怎么用的？`node = self.head`, `self.remove(nodeToRemove)`, `if node == self.head:`

linked list的position从1开始计数

记得改动之后重建连接🔗

#### Remove $k^{th}$ node from end

##### 题目：删除倒数第k个node（如果是remove head需要重新指定head）

![image-20220123185700477](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220123185700477.png)

##### 思路：

设置first，second两个pointer，second先到k位，second和first同时右移(len-k)位，使first满足kth node from end（$T=O(N)/S=O(1)$）

#### Sum of linked lists

##### 题目：类似倒序加法

![image-20220123192521235](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220123192521235.png)

##### 思路：可以不用倒序，设一个carryBit（2+9+0=1进1，4+4+1=9，7+5+0=2进1，1+0+1=2）

##### 要点：

```python
	# 创建linked list（Linked List class predefined）
  newLinkedListHeadPnt = LinkedList(5) # 这个「5」可以是任何值
	currentNode = newLinkedListHeadPnt
  # 加新值
  newNode = LinkedList(valueAppend)
	currentNode.next = newNode
	currentNode = newNode
```

