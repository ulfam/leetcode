+ [Binary Search](#binary-search)

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
