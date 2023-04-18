## AIgo_Homework_07

唐浩然 

2201111746



#### LeetCode 85

![LeetCode_85](.\pic\Leetcode_85.png)

**code：**

```python
class Solution(object):
    def maximalhistogram(self, histo):
        res = 0
        stack = []
        histo.append(0)
        for i in range(len(histo)):
            if len(stack) == 0:
                stack.append(i)
            else:
                while(len(stack) > 0 and histo[i] < histo[stack[-1]]):
                    if len(stack) == 1:
                        res = max(res, i * histo[stack[-1]])
                    else:
                        res = max(res, (i - stack[-2] - 1) * histo[stack[-1]])
                    stack.pop()
                stack.append(i)
        return res
    def maximalRectangle(self, matrix):
        """
        :type matrix: List[List[str]]
        :rtype: int
        """
        res = 0
        l = len(matrix)
        w = len(matrix[0])
        histo = [0] * w
        for i in range(l):
            for j in range(w):
                if matrix[i][j] == '1':
                    histo[j] += 1
                else:
                    histo[j] = 0
            res = max(res, self.maximalhistogram(histo))
        return res
```

**算法思路：**

直接暴力搜索复杂度是O(n^4)会TLE, 因此对于矩阵每一行进行累加成直方图，对直方图中求解最大矩形面积，相当于进行了n次直方图计算，对于直方图计算，只需要使用单调栈即可；此时复杂度降低为O(n^2)

#### LeetCode 152

![LeetCode_152](.\pic\Leetcode_152.png)

**code:**

```python
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        result = -0x7fffffff;
        max_p = min_p = 1
        numbers = len(nums)
        for i in range(numbers):
            if nums[i] < 0:
              max_p, min_p = min_p, max_p
            max_p = max(max_p * nums[i], nums[i])
            min_p = min(min_p * nums[i], nums[i])
            result = max(max_p, result)
        return result
```

**算法思路：**

尝试过暴力打表的方式发现会TLE, 因此采用动态规划的方法，由于正数与负数之间只有符号差别，因此此时同时维护最大值与最小值，在遇到负数时将最大值最小值互换即可；此时时间复杂度为O(n)
