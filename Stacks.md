#### Min max stack construction

##### 题目：实现stack的peak，pop，push，getMin，getMax

##### 思路：（$T=O(1)/S=O(1)$​）

用`stack`属性记录堆中数值，用`minMaxStack`属性记录这几个数值中的min，max（`minMaxStack = [{"min": value0, "max":value0},{"min": value11, "max":value12},{"min": value21, "max":value22}···]`就是说`minMaxStack`中第i个值对应的是`stack`中前i个值中的min，max，`push()`之后append新值）

##### 要点：

Stack: last in first out

Sequence: first in first out

字典索引：有`dic = {"min": val}`，取val时：`dic[min]`

#### Balanced brackets

##### 题目：string由`"[", "]", "(", ")", "{", "}"`和其他一些字母组成，返回这些括号是否匹配

##### 思路：经典stack，有关匹配问题可以用字典实现`matchBrackets = {")": "(", "}": "{", "]": "["}`

#### Sunset Views

##### 题目：返回能看到sunset的屋子编号，“EAST”代表比右边所有高，“WEST”代表比左边所有高

![image-20220130140509034](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220130140509034.png)

![image-20220130140523803](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220130140523803.png)

##### 思路：`buildings=[]`单独讨论，用自己的思路做就是，分EAST和WEST两种情况，WEST需要加一步倒序输出

##### 要点：

倒序输出：`return canSee[::-1]`

#### Next greater element

##### 题目：把数组看作首尾相连的，返回一个新数组，`result[i]`是下一个比`array[i]`大的值的index，如果没有返回-1

##### 思路：$T=O(N)/S=O(N)$

循环两遍

```python
for idx in range(2*len(array)):
		cirIdx = idx % len(array)
```

遍历cirIdx：`if array[stack top] < array[cirIdx]`: 把`result[stack top]` 赋值为`array[cirIdx]`；cirIdx放进stack

##### 要点：

挺妙一题，🉑️反复揣摩
