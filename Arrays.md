#### Two Number Sum

##### 题目：array[i] + array[j] = targetSum

##### 思路

1、遍历嵌套遍历（$T=O(N^2) / S=O(1)$​）

2、hash table（$T=O(N) / S=O(N)$​）

​		只遍历一次，将array[i]存入哈希表，检测targetSum - array[i] in hashTable?

3、2 pointers 近似奥数做法（$T=O(Nlog(N)) / S=O(1)$​）

##### 要点

`for i in range(5)`得到的是`0,1,2,3,4`（每个循环会自动`i += 1`）

`array.sort()`调用sort方法

`if … elif … else …`

#### Validate subsequence

##### 题目：sequence[] is a subsequence of array[]

##### 思路

2 pointers，基于sequence的每一项去遍历array（$T=O(N),S=O(1)$）

##### 要点

traverse 遍历

遍历array的两种语法`for seqIdx in range len(sequence):`和`for value in sequence:`

subsequence：顺序不变 → 2 pointers，每次不用从头开始

两个数组都必须遍历一遍，但如果一旦array中找不到sequence[i]，就可以跳出循环

跳出循环条件：两个pointer都超出`len()`

返回值：`return indexSeq == len(sequence)`，说明跳出条件是sequence被遍历完了

#### Sorted square array

##### 题目：array[] 按升序排列（in sorted ascending order），将每个数平方并按升序排列存入newArray[]（⚠️array中可能有负数）

##### 思路

1、遍历array每一项的平方存入newArray，再`newArray.sort()`（$T=O(NlogN), S=O(N)$）

2、2 pointers分别代表array的最大值和最小值（即一左一右），并比较绝对值，把**较大**的存入newArray右边（只需要反向遍历一次array）（$T=O(N), S=O(N)$）

##### 要点

反向遍历：`for i in reversed(range(len(array))):`

给空数组指定特定内存：`newArray = [0 for _ in array]`

array in sorted → can be solved in linear time

`.sort()`占用$T=O(NlogN)$​

这几道题input是不能删除的（新array占的内存作为space O）

#### Tournament winner

##### 题目：K个队伍round-robin循环赛，每两个队伍间只比一次（N次比赛）。input有`competitions[[homeTeam,awayTeam],…,[homeTeam,awayTeam]] & results[0/1,…,0/1]`，result[i]=1代表homeTeam赢，0代表awayTeam赢。赢一局加3分，无平局，最后分最高的队伍算winner。

##### 思路

1、hash table ➕ 结构体：队名作为key，形如`"teamName":3`，依据result[idx]得到赢队，加分/添队名加分，最后把最高分揪出来

2、优化：随时记录当前最高分队名（$T=O(N),S=O(K)$​）

##### 要点

1、字典：`scores = {key:value}`

~~~python
```
# 增加内容
scores[team] = 0   # 初始化
scores[team] += 3   # 赋值

# 获取最大值的索引
# 法一
max(d, key=lambda k: d[k])
# 法二
max(d, key=d.get)
``` 
~~~

2、python里很秀的操作

```python
for idx, game in enumerate(competitions):   # 枚举，game = [homeTeam,awayTeam]
		
		homeTeam, awayTeam = game   # python中的天秀操作，用等式拆分数组
		winner = homeTeam if results[idx] == 1 else awayTeam   # 合并if…else语法
		
		update(winner, 3, scores)   # 自己定义的函数，用结构体记录{key:value}
		
		if scores[winner] > scores[bestTeam]:   # 更新bestTeam（优化）
			bestTeam = winner
```

#### Non-compatible sum

##### 题目：整数array中任意几个数字求和，求不能实现的最小整数

##### 思路

有数学归纳法的思想了。排序。求前n个数之和（`sum += array[i]`），当`array[i+1] <= sum + 1`，意味着前i个数可以凑成1,2,3,……,sum。直到`array[i+1] > sum + 1`，`sum+1`就是第一个不能被实现的整数（$T=O(NlogN),S=O(1)$）

##### 要点

==问面试官`.sort()`之和能不能删去原数组（否则$S=O(N)$​​​）==（是这个意思吗？）

前n个数能组成连续数字，如果`array[i+1] == sum + 2`，那么`sum + 1`这个值无法得到

#### Three number sum

##### 题目：array中取三个数字组成数组，和为targetSum，要求数组内、数组间按升序排列

##### 思路

`array.sort()`排序 → 第一个pointer从左往右，第二三个pointer参考two number sum（$T=O(N^2)/S=O(N)$​）

##### 要点

输出数组`newArray.append([array[i],array[j],array[k]])`

`return `之后貌似函数直接跳出了，一定要用在最最最后

如果全用hash table，会占用多余空间（重复的符合条件数组）

#### Smallest difference

##### 题目：从两个数组中各取一个数，求差的绝对值的最小值对应的数组

##### 思路

1、两次`array.sort()`，两次遍历，用`current`记录现差，`smallest`记录最小差（$T=O(N^2)/S=O(1)$）

2、两次`array.sort()`，两个指针分别从`array[0]`开始，每次移动一个指针==（$T=O(NlogN+MlogM)/S=O(1)$​​）为什么啊？？==

```python
firstNum = arrayOne[idxOne]
secondNum = arrayTwo[idxTwo]
if firstNum < secondNum: # 说明减数（firstNum）不够大
  current = secondNum - firstNum
  idxOne += 1
elif firstNum > secondNum: # 说明减数（secondNum）不够大
  current = firstNum - secondNum
  idxTwo += 1
else:
	return [firstNum, secondNum]
```

再更新`smallest`。跳出循环条件：指针超出索引范围/差为0

##### 要点

一个感觉：两个指针时，一次只移动一个指针（那是移动哪一个？很玄妙啊）

#### Move element to end

##### 题目：把array中的数字等于toMove的数字全部丢到最后去

##### 思路

1、一个pointer，遇到一个`array[i] == toMove`，就`cnt += 1`，如果不等于，就把这个数存入新数组的前面。最后加上cnt个toMove（$T=O(N)/S=O(N)$）

2、两个pointer一左一右夹逼。（$T=O(N)/S=O(1)$​）

```python
if array[left] != toMove:
	left += 1
elif array[right] == toMove:
	right -= 1
else: # 两边指针都不移动的话就交换两个数
	array[left],array[right] = array[right], array[left]
```

##### 要点

交换两个变量的值：`a,b = b,a`

每次有两个指针的时候都仿佛在做奥数题hhh

==第二个方法为什么$S=O(1)$​呢？？==

#### Monotonic array

##### 题目：if array is non-increasing or non-decreasing，return True，else return False

##### 思路

1、遍历array，从`array[i]-array[i-1]`开始，确定非增/非减，（如果`array[0]-array[1] == 0`的话`i += 1`）一旦不符合就跳出循环

2、设置` isNonIncreasing = True`和`isNonDecreasing = True`，遍历array

```python
if array[i] - array[i-1] < 0:
  isNonIncreasing = False
elif array[i] - array[i-1] > 0:
  isNonDecreasing = False
```

return的判断是`isNonIncreasing or isNonDecreasing`

##### 要点

至少遍历一次 → 至少都有$T=O(N)$

法二的return思路很秀啊

![image-20210928173325004](/Users/shiyuan/Library/Application Support/typora-user-images/image-20210928173325004.png)

遇到return语句会直接结束函数

```python
if a > b:
	return True
# 可以简化成
return a > b
```

#### Spiral traverse

##### 题目：输入二维数组后输出一维数组

![image-20211007120406589](/Users/shiyuan/Library/Application Support/typora-user-images/image-20211007120406589.png)

##### 思路

一圈作为一次循环，设置四个pointer指示这一圈的边界（同时作为跳出循环的判断）（$T=O(N)/S=O(N)$）

##### 要点

用`.append()`，四个顶点不能加重了

二维数组/矩阵列数`colNum = len(array[0])`，行数`rowNum = len(array)`

范例代码用到了迭代思想（recursive），特点是space complexity不可能是常数，至少都是$S=O(N)$​

#### Longest path

##### 题目：寻找array中的最长peak路径的元素数（从单调递增到单调递减，无相等）

##### 思路

1、笨办法：设置一个指示序列增减的数字，分现在是增/减、之前是增/减/起始六种情况讨论，两个数字相等/长度<3都要清零length（$T=O(N)/S=O(N)$）

2、拆分任务：【find peaks】+【find longest peak】，左右都比自己小的元素一定是peak，对每个peak分别看左右能延长到哪里（$T=O(N)/S=O(N)$）

##### 要点

思维直接的代价就是代码会特别复杂（会遇到稀奇古怪的bug和稀奇古怪的if else）

#### Array of products

##### 题目：输入array，输出newArray的每个元素等于array除对应位置外其他元素之积

##### 思路

1、单独看有0的情况（1个0和多个0），`newArray[i] = product / array[i]`（$T=O(N)/S=O(N)$​​​）

2、设置两个新数组，$leftArray[i]=\prod^{i-1}_0array[k]$，$$rightArray[i]=\prod^{len(array)}_{i+1}array[k]$$​，就有`newArray[i] = leftArray[i] * rightArray[i]`。（$T=O(N)/S=O(N)$）

```python
	for i in range(len(array)-1):
		leftArray[i+1] = leftArray[i] * array[i]
	
	for i in reversed(range(1,len(array))):
		rightArray[i-1] = rightArray[i] * array[i]
```

3、代码看起来就很玄学，也并没有减少space complexity（$T=O(N)/S=O(N)$）

```python
	new = [0 for _ in array]
	for i in range(len(array)):
		if new[array[i]] == 0:
			new[array[i]] = 1
		else:
			print(array[i])
			break
	
	print(-1)
```

##### 要点

暴力解法：brute force approach

一题多解的时候，从最complex的开始，挨个解释分析（最笨的那个可以不写代码）

#### First duplicate value

##### 题目：array中元素$\in [1,len(array)]$​，找到其中第一个重复出现的数字

##### 思路

1、array中元素的范围就很妙，创建同样长度的零数组new，如果没重复就把`array[i]`存入`new[array[i]]`，重复了就返回`array[i]`（$T=O(N)/S=O(N)$）

2、用`set()`创建集合seen，看`array[i]`在不在seen中，不在就`seen.add(array[i])`（$T=O(N)/S=O(N)$​）

3、`array[abs(array[i])-1] *= -1`，判断条件就是之后 i 对应的`array[abs(array[i])-1]`是不是负的（$T=O(N)/S=O(1)$​​）

##### 要点

`set()`创建无序、不重复元素集，可用[set](https://blog.csdn.net/qq_44401643/article/details/89165581?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0.no_search_link&spm=1001.2101.3001.4242)解决列表中重复元素问题，对set搜索$T=O(1)$

判断能否mutate input array的方法：输出不需要这个array，就可以把input改了（法三的思路）可能不需要占用$S=O(N)$​，这时候的判断条件一般是正负（法三简直太秀了呜呜呜）

#### Merge overlapping intervals

##### 题目：`intervals = [[a,b],[c,d],...]`，[]代表区间，如果两区间有重叠，取较大的。没有重叠就保留。[[1,2],[2,3]]算重叠，[[1,2],[3,4]]不算重叠。区间边界一定满足左$\le$​右。eg. [[1,2],[3,5],[4,7],[5,6],[7,10],[11,12]] → [[1,2],[3,10],[11,12]]

##### 思路

1、一定先按第0位排序，这样只用对比`intervals[i][1]`和`intervals[i+1][0], intervals[i+1][1]`之间的关系（$T=O(NlogN)/S=O(N)$）

##### 要点

多维数组按第i位排序`sorted(intervals, key = lambda x: x[0])`，直接用.sort()默认按第0位排序

