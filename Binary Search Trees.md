#### Find closest value in BST

##### 题目：找到BST的node中和targetValue最近的

##### 思路

经典迭代（recursively，average：$T=O(logN)/S=O(logN)$​​​​，worst：$T=O(N)/S=O(N)$​）！在算法函数的`return`语句调用该函数，传入新数据

##### 要点

迭代算法+BST的complexity：average：$T=O(logN)/S=O(logN)$，worst：$T=O(N)/S=O(N)$

BST：对$\forall node$，满足$node>leftNodes$，$node\leq rightNodes$​

#### BST construction（主要是拿来学语法的）

##### 题目：实现insert，search，remove

##### 思路：

insert：一路比大小，实现把数字加在最末端即可

search：一路比大小，找到返回True

remove：无穷多的分类讨论，1⃣️ 找值，重建`parentNode = currentNode` 2⃣️ 重建currentNode.left和currentNode.right（1.3.1是用currentNode的right subtree的最小值替换`currentNode.value`）

![BST_construction](/Users/shiyuan/STUDY/大四/一个程序媛的诞生/编程笔记/BST_construction.jpeg)

##### 要点

method开头`currentNode = self`

不返回特定值的时候`return self`

Avg: $T = O(log(N))$, Worst: $T = O(N)$

Recursive algorithm: Avg: S = O(log(N)), Worst: S = O(N). (effectively using up frames on the call stack, 大概是说每次处理的node值存在stack里)

Iterative algorithm: $S = O(1)$

#### Validate BST

##### 题目：验证BST是否符合要求

##### 思路：

$leftParent \leq currentNode.value < rightParent$​​​ ( rightParent: 往上数向右拐的node )

经典迭代（$T=O(N), S=O(d)$, d is depth of BST）

##### 要点：

`float("-inf")`代表$-\infin$​​

代码的思路很诡异，思路是从上往下，但代码运行从下往上

![image-20220110215756208](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220110215756208.png)

#### BST Traversal

##### 题目：实现inOrderTraverse，preOrderTraverse和postOrderTraverse

##### 思路：

inOrderTraverse：最左边开始，leftNode->currentNode->rightNode然后往上一级

![image-20220111161215301](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220111161215301.png)

三个函数的区别就是append的位置不同

![image-20220111160200227](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220111160200227.png)

#### Min Height BST

##### 题目：把sorted array写成BST，并使其depth=min

##### 思路：

sorted->中间的数作为root，左右半边分别看作新array构建bst

$T = O(N)$, $S = O(N)$

##### 要点：

`insert()`那里没注意到的（如果bst有值可调用`insert()`方法，如果是`None`可直接赋值）

```python
	if bst is None:
		bst = BST(valueToAdd)
	else:
		bst.insert(valueToAdd)
```

这几个题简直把迭代玩明白了

class里面def的一个是方法（method），一个是属性（attribute）

#### Find Kth Largest Value in BST

##### 问题：找到BST中第k大的node值

##### 思路：

1⃣️ 基于`inOrderTraverse()`的思路，从小到大遍历，得到sorted array并取第`len(array)-k`个数

2⃣️ 基于reverse `inOrderTraverse()`的思路，从大到小遍历，另设class: TreeInfo.numVisited, TreeInfo.latestVisited，当`numVisited = k`，返回`lastVisited`

##### 要点：

`inOrderTraverse()`的思路: inOrderTraverse(tree.left) -> 记录tree.value -> inOrderTraverse(tree.right)

reverse `inOrderTraverse()`的思路: inOrderTraverse(tree.right) -> 记录tree.value(这个题里还包括更新TreeInfo) -> inOrderTraverse(tree.left)

#### Reconstruct preOrderTraverse BST……==这个题实在是离大谱==

##### 题目：通过pre order的array恢复BST

##### 思路：

1⃣️ 

2⃣️

##### 要点：
