# First


$$O(n)$$
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        res = [i for i in nums if i != val]
        nums[:] = res
        return len(nums)
```



# Later

```python
k = 0
for i in range(len(nums)):
    if nums[i] != val:
        nums[k] = nums[i]
        k += 1
return k
```

这个代码的空间复杂度减小了，只用了一个数组就完成了这个任务。