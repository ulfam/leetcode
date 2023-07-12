+ [Squares of a Sorted Array](#squares-of-a-sorted-array)
+ [Summary Ranges](#summary-ranges)
+ [Move Zeroes](#move-zeroes)
+ [Subarray Sum Equals K](#subarray-sum-equals-k)

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
### Time complexity is O(n). space O(1)
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
                
       # попробовать через идею, что старт с момента, когда slow стоит на первом нуле. В итоге 2 цикла. Между slow и fast всегда нули. Так мы минимизируем свопы
```



## Subarray Sum Equals K

https://leetcode.com/problems/subarray-sum-equals-k/

Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.
A subarray is a contiguous non-empty sequence of elements within an array.

### tried to solve without hints 
### Time complexity is O(n), space = O(n)
### 

Approach 4: Using Hashmap
Algorithm

The idea behind this approach is as follows: If the cumulative sum(represented by sum[i]sum[i]sum[i] for sum up to ithi^{th}i 
th
  index) up to two indices is the same, the sum of the elements lying in between those indices is zero. Extending the same thought further, if the cumulative sum up to two indices, say iii and jjj is at a difference of kkk i.e. if sum[i]−sum[j]=ksum[i] - sum[j] = ksum[i]−sum[j]=k, the sum of elements lying between indices iii and jjj is kkk.

Based on these thoughts, we make use of a hashmap mapmapmap which is used to store the cumulative sum up to all the indices possible along with the number of times the same sum occurs. We store the data in the form: (sumi,no.ofoccurrencesofsumi)(sum_i, no. of occurrences of sum_i)(sum 
i
​
 ,no.ofoccurrencesofsum 
i
​
 ). We traverse over the array numsnumsnums and keep on finding the cumulative sum. Every time we encounter a new sum, we make a new entry in the hashmap corresponding to that sum. If the same sum occurs again, we increment the count corresponding to that sum in the hashmap. Further, for every sum encountered, we also determine the number of times the sum sum−ksum-ksum−k has occurred already, since it will determine the number of times a subarray with sum kkk has occurred up to the current index. We increment the countcountcount by the same amount.

After the complete array has been traversed, the countcountcount gives the required result.

<details><summary>Test Cases</summary><blockquote>
        

</blockquote></details>


```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        s =[]
        acc_sum = 0
        for i in range(0,len(nums)):
            acc_sum+=nums[i]
            s.append(acc_sum)
        cnt=0
        dic={}
        for i in s:
            if i-k in dic:
                cnt+=dic[i-k]
            if i==k:
                cnt+=1
            if i in dic:
                dic[i]+=1
            else:
                dic[i]=1
        return cnt
```
