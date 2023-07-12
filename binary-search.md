+ [Binary Search](#binary-search)
+ [Search a 2D Matrix](#search-a-2d-matrix)
+ [Search in Rotated Sorted Array](#search-in-rotated-sorted-array)

## Binary Search

https://leetcode.com/problems/binary-search/

### tried to solve without hints - 30 min, problem with corners
### Time complexity is O(log n), space const
### 

<details><summary>Test Cases</summary><blockquote>    
        # [-1,0,3,5,9,12],9
        # n=6
        # l=0, r=5

        # m= 5 // 2 = 2
        # 3<9
        # l=2,r=5, m=3
        # 5<9
        # l=3,r=5,m=4
        # # ans=4

        # [-1,0,3,5,9,12],8
        # n=6
        # l=0, r=5, m=2
        # l=2,r=5,m=3
        # l=3,r=5, m=4
        # 9>8
        # l=3,r=3
        # l=3,
</blockquote></details>


```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        print(target)
        ans = -1
        n = len(nums)
        l=0
        r=n-1
        while l<r and (ans < 0):
            m = (l+r) // 2 # лучше l + (r-l) // 2, чтобы покрыть кейс выхода за возможные значения
            if nums[m]==target:
                ans = m
            elif nums[m]>target: # лучше else
                r = m-1
            else: # nums[m]<target
                l = m+1
        if l==r and nums[l]==target: # по идее этого не должно быть - сразу возвращение ответа
            ans = l
        return ans
```


## Search a 2D Matrix
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m = len(matrix)
        if m == 0:
            return False
        n = len(matrix[0])
        
        # binary search
        left, right = 0, m * n - 1
        while left <= right:
                pivot_idx = left + (right-left) // 2
                pivot_element = matrix[pivot_idx // n][pivot_idx % n]
                if target == pivot_element:
                    return True
                else:
                    if target < pivot_element:
                        right = pivot_idx - 1
                    else:
                        left = pivot_idx + 1
        return False
```


## Search in Rotated Sorted Array

https://leetcode.com/problems/search-in-rotated-sorted-array/

There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.

### Time complexity is 
### 

<details><summary>Test Cases</summary><blockquote>    
       
</blockquote></details>


```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        ans = -1
        n = len(nums)
        l=0
        r=n-1
        while l<=r and (ans < 0):
            m = l + (r-l) // 2
            if nums[m]==target:
                ans = m
            # Case 2: subarray on mid's left is sorted
            elif nums[m] >= nums[l]:
                if target >= nums[l] and target < nums[m]:
                    r = m - 1
                else:
                    l = m + 1
                    
            # Case 3: subarray on mid's right is sorted.
            else:
                if target <= nums[r] and target > nums[m]:
                    l = m + 1
                else:
                    r = m - 1
        return ans
```

