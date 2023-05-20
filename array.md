+ [Squares of a Sorted Array](#squares-of-a-sorted-array)
+ [Summary Ranges](#summary-ranges)
+ [Move Zeroes](#move-zeroes)

## Squares of a Sorted Array

https://leetcode.com/problems/squares-of-a-sorted-array/

### tried to solve without hints - success after 17 min
### main idea - two pointers from opposite sides
### Time complexity is O(2*len(nums)) because of list reversing reversing. Additional memory O(len(nums))

<details><summary>Test Cases</summary><blockquote>
    [-11, -3,-1,0,1,2,5,6] -> [121,36,25,9,4,1,1,0] -> [0,1,1,4,9,25,36,121]
    [-9] -> [81] -> [81]
</blockquote></details>


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
        # ПЕРЕПИСАТЬ БЕЗ РАЗВОРОТА С enumerate
        
```


## Summary Ranges

https://leetcode.com/problems/summary-ranges/

### tried to solve without hints - success after 15 min
###
### Time complexity is O(n). space O(n)
### 

```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        if len(nums) == 0:
            return []
        else:
            start = nums[0]
            end = nums[0]
            ranges = []
            for i in range(1,len(nums)):
                if nums[i] == (nums[i-1]+1):
                    end = nums[i]
                else:
                    if start != end:
                        s = str(start)+"->"+str(end)
                    else:
                        s = str(start)
                    ranges.append(s)
                    start = end = nums[i]
            if start != end:
                lasts = str(start)+"->"+str(end)
            else:
                lasts = str(start)
            ranges.append(lasts)
            return ranges
            # ПОПРОБОВАТЬ ЧЕРЕЗ ДВА ВЛОЖЕННЫХ ЦИКЛА while ЧЕРЕЗ ДВА УКАЗАТЕЛЯ 
```

## Move Zeroes

https://leetcode.com/problems/move-zeroes/

### tried to solve without hints - success after 15 min
###
### Time complexity is O(n**2). space O(n)
### 

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        slow = 0
        fast = 1
        while slow < len(nums) and fast < len(nums):
            if nums[slow] == 0:
                nums[slow] = nums[fast]
                nums[fast] = 0
            fast+=1
            if (nums[slow])!=0:
                slow+=1
```
