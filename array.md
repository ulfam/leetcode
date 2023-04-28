+ [Squares of a Sorted Array](#squares-of-a-sorted-array)

## Squares of a Sorted Array

https://leetcode.com/problems/squares-of-a-sorted-array/

### tried to solve without hints - success after 17 min
### Some test-cases:
### 
### 
### 
###
### Time complexity is 
### 

# [-11, -3,-1,0,1,2,5,6] - []
# two pointers from opposite sides

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        squarednums = [0]*len(nums)
        start = 0
        end = len(nums)-1
        for i in range(len(nums)):
            if (nums[start])**2 >= (nums[end])**2:
                squarednums[i] = (nums[start])**2
                start+=1
            else:
                squarednums[i] = (nums[end])**2
                end-=1
        return squarednums[::-1]
        
```
