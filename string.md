+ [String Compression](#string-compression)

## String Compression

https://leetcode.com/problems/string-compression/

### tried to solve without hints - much time, solutions not optimal
### Some test-cases:
###  -> 
### 
### 
###
### Time complexity is O(2n), space O(2n) 
### 


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
