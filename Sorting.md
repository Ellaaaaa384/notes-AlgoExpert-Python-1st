##### 题目：Bubble sort

##### 思路：反复遍历array，如果`array[i] > array[i+1]`，swap array[i] & array[i+1]，直到遍历的时候不会出现上述情况（`isSorted is True`）

$avg\ \&\ worst:T=O(N^2)/S=O(1)$

##### 要点：

bubble sort是原地swap（不是O(N)space的解释👇）

![image-20220128161159313](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220128161159313.png)

遍历cnt次意味着倒数cnt个数都是sorted的了（`for i in range(len(array)-cnt-1):`）

##### 题目：Insertion sort

##### 思路：大循环：遍历array一次，对`array[i]`进行`array[0:i-1]`的第二次倒序遍历，如果`array[j] < array[j-1]`，swap array[j] & array[j-1]（相当于把`array[i]`插入前面subarray的合适位置）

$avg\ \&\ worst:T=O(N^2)/S=O(1)$

##### 要点：

Insertion sort也是原地swap

二次倒序遍历的跳出条件是`while j > 0 and array[j] < array[j-1]:`

##### 题目：Selection sort

##### 思路：大循环：遍历array一次，将`array[currentIdx+1:-1]`中的最小值与`array[currentIdx]`swap

$avg\ \&\ worst:T=O(N^2)/S=O(1)$

##### 要点：

```python
array=[1,3,2,1]
array.index(min(array[1:])) # output是0([1,3,2,1])
array[1:].index(min(array[1:])) # output是2([3,2,1])
```

#### Three number sort

##### 题目：order有xyz三个值，array只由xyz三个值组成，output是array按照order中的排序

![image-20220128193614255](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220128193614255.png)

##### 思路：（$T=O(N)/S=O(1)$）

1⃣️ 直接count每个value有几个，对array重新赋值

2⃣️ 对中间值左右插值，注意追踪三个值的插入位