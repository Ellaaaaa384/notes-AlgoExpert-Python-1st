#### Caesar cipher encryptor

##### 题目：给定string和key，newString每个字符是string对应位置字符的后k个值（k=2，a的后k位 = c）

##### 思路：$T=O(N)/S=O(N)$

建立字母表(type = list), 这样才能用`append()`进行修改

```python
alphabet = list("abcdefghijklmnopqrstuvwxyz")
% output
alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
```

获得该字符的后k位的值`newLetterCode = (alphabet.index(letter) + key) % 26`

##### 要点：

将数组改回字符串：`return "".join(newLetters)`

字符串追加（字母表type = str）`newLetters += newLetter`

#### First non-repeating character

##### 题目：返回字符串中第一个不重复的字符的idx

##### 思路：设置字典记录每个字符出现频次（$T=O(N)/S=O(1)$）

##### 要点：

对字典索引key对应的值进行操作，如果没有key则返回0: `charFreq[char] = charFreq.get(char,0) + 1`（意思就是如果要返回NF就用`.get(char, "NF")`，且用`charFreq[char]`会直接创建以char为key的索引）

#### Longest palindromic substring

##### 题目：返回string中的最长对称substring（evenLength："xyzzyx"；oddLength："aba"）

##### 思路：遍历每个字母，返回以该字母为对称中心（奇偶）的最大起止index（始终用数组记录起止点index）（$T=O(N^2)/S=O(N)$）

##### 要点：

```python
odd = [oddStartIdx, oddEndIdx]
even = [evenStartIdx, evenEndIdx]
longest = max(odd, even, key=lambda x: x[1]-x[0])
# 相当于longest = max((oddEndIdx - oddStartIdx), (evenEndIdx - evenStartIdx))
```

`string[0:3]`不含`string[3]`

#### Group anagrams

##### 题目：返回“由相同字母组合而成的单词”的组合

![image-20220204134044303](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220204134044303.png)

##### 思路：sort每个单词作为字典的key，把字母组成相同的原单词append为value（$T=O(W \times N \times log(N))/S=O(W \times N)$​）

##### 要点：

`sorted(word)`返回`['a', 'c', 't']`，`"".join(sorted(word))`返回`act`

```python
anagrams.values()
# output
dict_values([['yo', 'oy'], ['act', 'tac', 'cat'], ['flop', 'olfp'], ['foo']])

list(anagrams.values())
# output
[['yo', 'oy'], ['act', 'tac', 'cat'], ['flop', 'olfp'], ['foo']]
```

#### Valid IP addresses

##### 题目：给定一串数字，用三个点分隔出valid IP address，返回所有组合（valid：$0 \leq val \leq 255$，不能以0做最高位​）

##### 思路：三个指针（代表分隔点位置）三重循环（$T=O(1)/S=O(1)$）

```python
# 分隔出的ip最多3位，分隔符最多到string末尾（192 -> 192.0.0.0）
for idx1 in range(1, min(len(string), 4)):
	for idx2 in range(idx1 + 1, idx1 + min(len(string) - idx1, 4)):
		for idx3 in range(idx2 + 1, idx2 + min(len(string) - idx2,4)):
```

##### 要点：

`ipAddrFound.append(".".join(currentIP))`用"`.`"分隔每个`currentIP`

把字符串中的数字当作integer：`intString = int(string)`

判断字符串是否以"0"打头：`return len(string) == len(str(intString))`

#### Minimum characters for words

##### 题目：返回表示每个单词需要用到的最少字母组合

![image-20220205141055624](/Users/shiyuan/Library/Application Support/typora-user-images/image-20220205141055624.png)

##### 思路：（$T=O(n \times l)/S=min:O(c),max:O(n\times l)$​​，n is number of words, l is length of longest word）

经典的主函数里调用三个helper function

cntFreq()：记录每个单词需要用到的字母及数量

updateFreq()：用cntFreq()更新原字典

makeArray()：把字典里的key按value倍append
