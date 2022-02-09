#### Product sum

##### 题目：计算array的product sum

![image-20220124182901689](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220124182901689.png)

##### 思路：从外往里check element type（`if type(element) is list:`）

$T=O(N)/S=O(d)$​​​​

##### 要点：

```python
# input:
array = [5, 2, [7, -1], 3, [6, [-13, 8], 4]]
for element in array:
# output:
5
2
[7, -1]
7
-1
3
[6, [-13, 8], 4]
6
[-13, 8]
-13
8
4
```

Permutations

题目：

思路：

1⃣️ $T=O(N!\times N)/S=O(N!\times N)$

```python
def Helper(array, perm, perms):
	if array is empty:
		perms.append(perm)
	else:
		for num in array:
			newArray = removeNumFrom(array)
			newPerm = perm + num
			Helper(newArray, newPerm, perms)
```

![image-20220124195815925](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220124195815925.png)

$N!\times N$​​ times call of `Helper()`，创造newArray和newPerm还需要N time

2⃣️ $T=O(N!\times N^2)/S=O(N!\times N)$​​​​​

巨离谱的思路（[视频讲解](https://www.algoexpert.io/questions/Permutations)25:00处）

```python
def getPermutations(array):
    perms = []
	permHelper(0, array, perms)
	return perms

def permHelper(i,array,perms):
	if i == len(array)-1:
		perms.append(array[:])
	else:
		for j in range(i,len(array)):
			swap(array,i,j)
			permHelper(i+1,array,perms)
			swap(array,i,j)
			
def swap(array,i,j):
	array[i],array[j] = array[j],array[i]
```

##### 要点：

实现从array中删除第i个数：`newArray = array[:i] + array[i+1:]`

实现两个值交换`a,b = b,a`

#### Powerset

##### 题目：

##### 思路：

![截屏2022-01-27 上午10.15.10](/Users/shiyuan/STUDY/大四/一个程序媛的诞生/编程笔记/截屏2022-01-27 上午10.15.10.png)
