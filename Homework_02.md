## Algo_Homework_02

唐浩然

2201111746

#### Leetcode 07 
![Leetcode_07](./pic/Leetcode_07.png)

**code:**
```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        str_x = str(x)
        if str_x[0] == '-':
            str_rev_x = '-' + str_x[1:][::-1]
            if 2**31 < long(str_rev_x[1:]):
                return 0
            else:
                return int(str_rev_x)
        else:
            str_rev_x = str_x[::-1]
            if 2**31-1 < long(str_rev_x):
                return 0
            else:
                return int(str_rev_x)

```
**算法思路：**

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
