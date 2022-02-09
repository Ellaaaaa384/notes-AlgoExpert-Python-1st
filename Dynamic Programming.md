#### Max subset no adjacent sum

##### 题目：取数组中不相邻的几个数使和最大

##### 思路：

1⃣️ `maxSum[i] = max(maxSum[i-1], (maxSum[i-2]+array[i]))`（理解：第i个maxSum要不等于上一个值（不使用array[i]）如果要用array[i]，那array[i-1]就不能用，所以最多基于maxSum[i-2]）（$T=O(N),S=O(N)$）

2⃣️ 优化space complexity：只存maxSum[i], maxSum[i-1], maxSum[i-2]三个值（$T=O(N),S=O(1)$​）

##### 要点：

`	maxSum = array[:]`创造与array等长的数组

#### Num of ways to make change

##### 题目：给定几个面值的钱和期待的总额，返回“实现总额的方法数”

##### 思路：迭代。对从0开始的sum值，way[sum] += way[sum-val]

#### Min num of coins for change

##### 题目：给定几个面值的coin和期待的总额，返回使用最少数量的coin凑到总额的数

##### 思路：

`num[amount] = min(num[amount], (num[amount-denom]+1))`，如果无法凑整会让`num[n] == float("inf")`（就是没有重新赋值）

##### 要点：

`for a in range(5)` -> a从0到4遍历

#### Levenshtein Distance

##### 题目：两个字符串str1和str2，返回使str1变成str2的最少操作次数（替换/插入/删除）

##### 思路：列表+动态

Eg. str1 = abc, str2 = abdy

| str1\str2 | " "   | a    | b    | d    | y    |
| --------- | ----- | ---- | ---- | ---- | ---- |
| " "       | 0 (m) | 1    | 2    | 3    | 4    |
| a         | 1     | x    | y    |      |      |
| b         | 2     | z    |      |      |      |
| c         | 3     |      |      |      |      |

z空的意思：用\_ab得到\_a

两个字符串最后一位相同，用左上相邻的值：eg. x = m

两个字符串最后一位不相同，用min(左，左上，上)的值：eg. y = min(x,1,2)

如果用完整的列表存，$T=O(MN),S=O(MN)$​​，只存列表的最后两行，$T=O(MN),S=O(min(M,N))$​​

##### 要点：

初始化矩阵（list）`tab = [[0 for _ in range(4)] for _ in range(3)]`生成3x4的全0矩阵

调用矩阵中的数：`tab[a][b]`

#### Num of ways to traverse graph

##### 题目：从左上角格子走到右下角格子有几种方法？

![image-20220114171241768](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220114171241768.png)

##### 思路：

1⃣️ 迭代: 到左邻方块的方法+到上邻方块的方法=到该方块的方法`return numOfWays(width-1,height)+numOfWays(width,height-1)`，$T=O(2^{m+n}),S=O(m+n)$​​​​

<img src="/Users/shiyuan/Library/Application Support/typora-user-images/image-20220114173450423.png" alt="image-20220114173450423" style="zoom:50%;" />

2⃣️ 动态算法：类似Levenshtein Distance的算法

##### 要点：数学方法虽然可以狂省内存，但不是考官想要的

