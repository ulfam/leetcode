+ [String Compression](#string-compression)
+ [Long Pressed Name](#long-pressed-name)

## String Compression

https://leetcode.com/problems/string-compression/

### tried to solve without hints - much time, solutions not optimal
### Time complexity is O(2n), space O(2n) 
### 

<details><summary>Test Cases</summary><blockquote>
        
        # ["a","2","b","2","c","c","c"] -> ["a","2","b","2","c","3"]
        # range 6-4
        # n=6
        # p=4
        # c=3
        
        # old code
        # n = len(chars)
        # pointer = 0
        # count = 1
        # for c in range(1,len(chars)):
        #     if chars[c] == chars[c-1]:
        #         count += 1
        #     else:
        #         chars[pointer]=chars[c-1]
        #         if count > 1:
        #             pointer+=1
        #             chars[pointer]=str(count)
        #         pointer+=1
        #         count = 1
        # chars[pointer]=chars[n-1]
        # if count > 1:
        #     pointer+=1
        #     chars[pointer]=str(count)
        # for i in range(n-pointer-1):
        #     chars.pop()
        # return len(chars)
</blockquote></details>


```python
def compress(self, chars: List[str]) -> int:
        s = ''
        n = len(chars)
        count = 1
        for c in range(1,len(chars)):
            if chars[c] == chars[c-1]:
                count += 1
            else:
                s+=chars[c-1]
                if count > 1:
                    s+=str(count)
                count = 1
        s +=chars[n-1]
        if count > 1:
            s+=str(count)
        l = len(s)
        for i in range(n-l):
            chars.pop()
        for i in range(l):
            chars[i]=s[i]
        return l

```

## Long Pressed Name

https://leetcode.com/problems/long-pressed-name/

### tried to solve without hints - much time, solutions not optimal
### Time complexity is O(2n), space O(2n) 
### 

<details><summary>Test Cases</summary><blockquote>

</blockquote></details>


```python


```
