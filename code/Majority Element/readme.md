# First

$$O(n)$$

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        ret = {key: 0 for key in set(nums)}
        for i in nums:
            ret[i] += 1
        max_key = max(ret, key=ret.get)
        return max_key
```

建立一个字典，然后字典找到出现次数最多的数字。

# Later

```python

class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        hash = {}
        res = majority = 0
        
        for n in nums:
            hash[n] = 1 + hash.get(n, 0)
            if hash[n] > majority:
                res = n
                majority = hash[n]
        
        return res
```
这个写法我觉得并不比之前的高明，他每次都存储一个变量，其实是多占据了空间。修改一下：

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        hash = {}
        for n in nums:
            hash[n] = 1 + hash.get(n, 0)
        max_key = max(hash, key=hash.get)
        return max_key
```
这样写会更快一点。