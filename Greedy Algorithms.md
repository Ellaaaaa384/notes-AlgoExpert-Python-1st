#### Minimum waiting time

##### 题目：一串人挨个办事，求所有人的最少等待时间

##### 思路：经典奥数了（`queries.sort()`）（$T=O(NlogN)/S=O(1)$）

##### 要点：

`for idx,duration in enumerate(queries):`idx=0, 1, 2, ··· , len(queries)-1，duration是queries中的每个值

#### Class photo

##### 题目：等长两个数组代表两队身高，同队站一排，能否保证站前排每个人身高低于后排对应位置的人？

##### 思路：倒序sort+每队最高的人中较矮的确定哪队在前排+挨个比较

##### 要点：

倒序sort: `array.sort(reverse=True)`

#### Task assignment

##### 题目：k个人干2k项活（每人的2项活依次进行），tasks代表每项活的时间，总时间=min{每个人干完2项活的时间}，返回分配方式

![image-20220122172811886](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220122172811886.png)

##### 思路：升序排列，按照最长时+最短时分配

##### 要点：

[sort和sorted](https://blog.csdn.net/qq_24076135/article/details/78550898)

对列表中某个元素排序`sorted()`：

```python
result = sorted(taskDurationPair, key=lambda student: student[1])

taskDurationPair: [(0, 1), (1, 3), (2, 5), (3, 3), (4, 1), (5, 4)]

result: [(0, 1), (4, 1), (1, 3), (3, 3), (5, 4), (2, 5)]
```

#### Valid starting city

##### 题目：n个城市，分别有一定量的油，汽车从某城市出发，按顺序途经城市并加油，返回出发城市（使能跑完全程）（油之和恰好能跑完全程，有且仅有一个可出发城市）

##### 思路：任意一点出发计算剩余油量，最小值对应的索引即为出发点（除法的小数会有问题，需改算能跑的里程数）（$T=O(N)/S=O(1)$）

##### 要点：

获得数组中最大值/最小值索引`array.index(min(array))`

