#### Binary search

##### 题目：sorted array中找出target value的index，如果没有，返回-1

##### 思路：二分查找，设置left和right两个pointer（$T=O(logN),S=O(1)$）

##### 要点：

`def helper()`来传入pointer参数

#### Find three largest number

##### 题目：找到array中最大的三个数（input不排序，output排序）

##### 思路：（$T=O(N),S=O(1)$​）

`findThreeLargestNumbers()`：遍历array中的每个值`num`

`updateLargest()`：`num`大于`threeLargest[i]`就把这个值换到`threeLargest[i]`，threeLargest的更小值依次挪位（调用`shiftAndUpdate()`实现）

#### Search in sorted matrix

##### 题目：sorted matrix满足每一行、每一列都是sorted，返回target的坐标（没有就返回`[-1,-1]`）

##### 思路：row正序遍历，col倒序遍历（$T=O(M+N),S=O(1)$​）

