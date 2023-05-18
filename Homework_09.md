## Algo_Homework_09

唐浩然

2201111746



#### Leetcode 240

![Leetcode_240](./pic/Leetcode_240.png)

**Code:**

```python
class Solution(object):
    def DFS(self, x1, y1, x2, y2, target):
        i = int((x1+x2)/2)
        j = int((y1+y2)/2)
        value = self.matrix[i][j]
        if value == target:
            return True
        if x1 >= x2 and y1 >= y2:
            return False
        if x1 > x2 or y1 > y2:
            return False
        if value > target:
            if x1 == x2 and j-1 >= y1:
                return self.DFS(x1,y1,x1,j-1,target)
            if y1 == y2 and i-1 >= y2:
                return self.DFS(x1,y1,i-1,y1,target)
            if i > x1 and j > y1 and self.DFS(x1, y1, i-1, j-1, target):
                return True
            if self.DFS(i,y1,x2,j-1,target):
                return True
            if self.DFS(x1,j,i-1,y2,target):
                return True
            return False
        if value < target:
            if x1 == x2 and j+1 <= y2:
                return self.DFS(i,j+1,x2,y2,target)
            if y1 == y2 and i+1 <= x2:
                return self.DFS(i+1,j,x2,y2,target)
            if i < x2 and j < y2 and self.DFS(i+1,j+1,x2,y2,target):
                return True
            if self.DFS(i+1,y1,x2,j,target):
                return True
            if self.DFS(x1,j+1,i,y2,target):
                return True
            return False
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        self.matrix = matrix
        m = len(matrix)
        n = len(matrix[0])
        return self.DFS(0,0,m-1,n-1,target)
```

**算法思路：**

利用数组规律，实现二维的二分查找；

#### Leetcode 347

![Leetcode_347](./pic/Leetcode_347.png)

**Code:**

```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        hash_dict = {}
        freq = [[] for i in range(len(nums) + 1)]
        for num in nums:
            if num not in hash_dict.keys():
                hash_dict[num] = 1
            else:
                hash_dict[num] += 1
        for num, f in hash_dict.items():
            freq[f].append(num)
        res=[]
        for i in range(len(freq)-1,0,-1) :
            for n in freq[i] :
                res.append(n)
                if len(res)==k :
                    return res  

```

**算法思路：** 
利用题目中对于无序性的要求，利用列表以出现次数为索引存储对应数字；

#### Leetcode 374

![Leetcode_374](./pic/Leetcode_374.png)

**Code:**

```python
class Solution(object):
    def guessnum(self,l,r):
        if l == r:
            return l
        tmp = int((l+r)/2)
        flag = guess(tmp)
        if flag == 0:
            return tmp
        if flag == -1:
            return self.guessnum(l,tmp)
        if flag == 1:
            return self.guessnum(tmp+1,r)
    def guessNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        return self.guessnum(1,n)

```

**算法思路：** 
利用Guess（）函数返回值进行二分查找；
