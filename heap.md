Top K Frequent Elements
 

+ [Top K Frequent Elements](#top-k-frequent-elements)

## Top K Frequent Elements

https://leetcode.com/problems/top-k-frequent-elements/

### tried to solve without hints - 
### Time complexity is O((u log u) + n), where u - count of unique elements in nums, space complexity is O(u+k)
### 

<details><summary>Test Cases</summary><blockquote>
        
   
</blockquote></details>


```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        d = {}
        for i in nums:
            if d.get(i):
                d[i]+=1
            else:
                d[i]=1
        freq = list(d.values())
        freq.sort()
        final_array = []
        for key,value in d.items():
            if value in freq[-k:]:
                final_array.append(key)
        return final_array
```
