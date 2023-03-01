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
