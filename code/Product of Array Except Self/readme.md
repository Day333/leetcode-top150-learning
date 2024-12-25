# Problem

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

# First


超时$(n^2)$

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = []
        for i in range(len(nums)):
            num1, num2 = 1, 1
            for j in range(0, i):
                num1 = num1 * nums[j] 
            for k in range(i + 1, len(nums)):
                num2 = num2 * nums[k] 
            answer.append(num1 * num2)
        return answer
```

# Later

$O(n)$
每个数都由左边的乘积和右边的乘积两部分组成。

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        output = [1] * len(nums)
        
        left = 1
        for i in range(len(nums)):
            output[i] *= left
            left *= nums[i]
        
        right = 1
        for i in range(len(nums) - 1, -1, -1):
            output[i] *= right
            right *= nums[i]
    
        return output        
```