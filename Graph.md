#### Depth-first search

##### 题目：类似二叉树的preOrderTraverse

![image-20220115114915087](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220115114915087.png)

##### 思路：node.append->child.depthFirstSearch()

#### Single cycle check

##### 题目：从array[$a_0$]开始，向右array[$a_0$]个数到array[$a_1$]再向右array[$a_1$]个值到array[$a_2$]，以此类推。single cycle：从任意array[$a_0$​​​]开始，every index is visited once before returning to the starting point (array[$a_0$])

##### 思路：

1⃣️ 用一个和array等长的全0 array2 记录idx，每到一个值就把这个位置的array2值改成0，若array2某个值大于1或`numVisited == len(array)`时仍有array2某个值等于0就`return False`（$T=O(N)/S=O(N)$）

2⃣️ numVisited和currentIdx两个变量，判断条件：`numVisited < len(array)`时回到出发点（`return False`），`numVisited = len(array)`时回不到出发点（`return currentIdx == STARTING_IDX`）

##### 要点：

实现loop（`idx == len(array)`的下一个是`idx==0`）的关键：`currentIdx = (currentIdx + plusIdx) % len(array)`（-4%5=1）（仅对python有效，否则要加一句`return currentIdx if currentIdx >= 0 else currentIdx+len(array)`）

#### Breadth first search

##### 题目：level by level

![image-20220119204810926](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220119204810926.png)

##### 思路：用queue的FIFO思路

![IMG_AA85F8A21ABA-1](/Users/shiyuan/STUDY/大四/一个程序媛的诞生/编程笔记/IMG_AA85F8A21ABA-1.jpeg)

##### 要点：

`list.pop(1)`删除列表里第2个数

#### River Size

##### 题目：01构成矩阵，0代表陆地，1代表河流（上下左右相邻的1代表同一条河），返回所有河流大小构成的数组

![image-20220120134850944](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220120134850944.png)

##### 思路：创建等大矩阵记录是否访问过这个位置，对每个“值为1且未访问”的node的unvisited neighbors加到queue后面，对每个node采用类似Breadth first search的方法（$T=O(wh)/S=O(wh)$​）

##### 要点：

主函数：遍历矩阵的每个点，如果unvisited，调用traverseNode函数

traverseNode函数：用于记录每个unvisited且值为1的node的unvisited neighbors（getUnvisitedNeighbors函数）有几个可用（breadth first search）

getUnvisitedNeighbors函数：上下左右unvisited的空+边界的例外

#### Youngest common ancestor

##### 题目：AncestralTree class有一个ancestor property找两个node最近的共同ancestor

##### 思路：两个node如果是不同层：先让深层node往上找ancestor到与浅层node同层，再一起往上找到common ancestor（$T=O(d)/S=O(1)$​）

#### Remove islands

##### 题目：01构成矩阵，返回“把所有1换成0（border上的1及其相邻的1除外）”的矩阵

![image-20220120200737685](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220120200737685.png)

##### 思路：（$T=O(wh)/S=O(wh)$）

主函数：遍历矩阵的border，如果是1，调用findBorderOnes函数；把matrix矩阵中对应位置是borderOnes矩阵的False的改为0

findBorderOnes函数：用等大的borderOnes矩阵，把border 1相邻（getNeighbors函数）的所有1对应位置改为True

getNeighbors函数：上下左右边界的例外

##### 要点：

矩阵的边界判断：

```python
rowIsBorder = row == 0 or row == len(matrix)-1
colIsBorder = col == 0 or col == len(matrix[row])-1
isBorder = rowIsBorder or colIsBorder
```

==stack和queue的区别？这个题不能用queue吗？==

#### Cycle in graph

##### 题目：判断图里有无cycle

![IMG_3BC7E34B2548-1](/Users/shiyuan/STUDY/大四/一个程序媛的诞生/编程笔记/IMG_3BC7E34B2548-1.jpeg)

##### 思路：$T=O(v+e)/S=O(v)$​, v is vertices number, e is edge number

主函数：用inStack记录正在处理的这条线上的所有visited node，遍历（用visited记录）每个node，对unvisited node有cycle就返回true

isNodeInCycle函数（recursive）：对该node指向的node进行遍历，if unvisited：再次调用isNodeInCycle函数；elif inStack：return True。把该node的inStack状态设置为False

##### 要点：

vertex: 相当于node

edge: 相当于箭头

adjacency list：用于存directed graph

![IMG_0CD12022ED9F-1](/Users/shiyuan/STUDY/大四/一个程序媛的诞生/编程笔记/IMG_0CD12022ED9F-1.jpeg)

