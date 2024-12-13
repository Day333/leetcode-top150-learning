# First

$$O(2*n)$$

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        res = set(nums)
        nums[:] = sorted(res)
        return len(res)
```
这个我的思路是先去重，然后排序，会慢一些。

# Later

$$O(n)$$

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        k = 1
        for i in range(1, len(nums)):
            if nums[i] != nums[i-1]:
                nums[k] = nums[i]
                k += 1
        return k
```
这样子只需要遍历一次数组就可以。