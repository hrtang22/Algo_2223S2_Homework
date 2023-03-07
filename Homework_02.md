## Algo_Homework_02

唐浩然

2201111746

#### Leetcode 07 
![Leetcode_07](./pic/Leetcode_07.png)

**code:**
```python
class Solution:
     def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        str_x = str(x)
        if str_x[0] == '-':
            str_rev_x = '-' + str_x[1:][::-1]
            if len(str(2**31)) > len(str_rev_x[1:]):
                return int(str_rev_x)
            elif len(str(2**31)) == len(str_rev_x[1:]):
                if str(2**31) < str_rev_x[1:]:
                    return 0
                else:
                    return int(str_rev_x)
            else:
                return 0
        else:
            str_rev_x = str_x[::-1]
            if len(str(2**31-1)) > len(str_rev_x):
                return int(str_rev_x)
            elif len(str(2**31-1)) == len(str_rev_x):
                if str(2**31) < str_rev_x:
                    return 0
                else:
                    return int(str_rev_x)
            else:
                return 0          

```
**算法思路：**
由于不能使用64bit的long进行数字的存储，考虑需要对于反转后数字是否溢出进行计算，因此首先将数字转换为字符串并进行反转；
在此之后，对负数、正数两种情况分别讨论，通过比较字符串与溢出临界值转化而来的字符串之间长度的关系：
1. 若长度大于临界值，则溢出返回零；
2. 若长度相等，则利用字符串比较判断大小；
3. 若长度小于临界值，则直接反转；


#### Leetcode 13 
![Leetcode_13](./pic/Leetcode_13.png)

**code：**
```python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        Roman_values = dict(I=1,V=5,X=10,L=50,C=100,D=500,M=1000)
        last_value = 0
        re = 0
        for ch in s:
            value = Roman_values[ch] 
            re += value
            if value > last_value:
                re -= 2*last_value
            last_value = value
        return re
```
**算法思路：**
首先构建罗马字符到数字的对应关系dict（Roman_values），接下来只需要顺序对于字符读取并累加；
由于字符的组成会出现如：IV表示5 - 1 = 4 这类的结构，只需要判断字符序列是否按照数值递减即可；
即对于上一次读取的字符进行存储，如果当前字符大于上一个字符，则需要减去上一个字符的2倍数值；
#### Leetcode 66
![Leetcode_66](./pic/Leetcode_66.png)

**code:**
```python
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        flag = False
        digits.reverse()
        for i, d in enumerate(digits):
            num = int(d)
            if flag or i == 0:
                num += 1
            if num < 10:
                digits[i] = num
                flag = False
            else:
                digits[i] = 0
                flag = True
        if flag:
            digits.append(1)
        digits.reverse()
        return digits
```
**算法思路：**
对于输入的digits，欲得到其+1之后的结果，首先对于该数组进行反转；
之后对其进行遍历，利用flag作为是否需要进位标识，即可完成+1计算；
