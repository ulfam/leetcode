+ [Squares of a Sorted Array](#squares-of-a-sorted-array)

## Squares of a Sorted Array

https://leetcode.com/problems/squares-of-a-sorted-array/

### tried to solve without hints - success after 17 min
### Some test-cases:
### [-11, -3,-1,0,1,2,5,6] -> [121,36,25,9,4,1,1,0] -> [0,1,1,4,9,25,36,121]
### [-9] -> [81] -> [81]
### main idea - two pointers from opposite sides
### 
###
### Time complexity is O(2*len(nums)) because of list reversing reversing. Additional memory O(len(nums))
### 

# 
# 
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        # I don't make None check because we have condition that 1 <= nums.length <= 104
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
