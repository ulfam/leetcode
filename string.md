+ [String Compression](#string-compression)
+ [Long Pressed Name](#long-pressed-name)
+ [Group Anagrams](#group-anagrams)

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
# ПЕРЕПИСАТЬ С ДВУМЯ УКАЗАТЕЛЯМИ, и двумя циклами while - ОДИН УБЕГАЕТ ВПЕРЕД, ДРУГОЙ СЗАДИ

```

## Long Pressed Name

https://leetcode.com/problems/long-pressed-name/

### NOT SOLVED
### Time complexity 
### 

<details><summary>Test Cases</summary><blockquote>

</blockquote></details>


```python

class Solution:
    def compress(self, chars: List[str]) -> string:
        s = ""
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
        # for i in range(l):
        #     chars[i]=s[i]
        return s

    def isLongPressedName(self, name: str, typed: str) -> bool:
        nameCompressed = self.compress(name)
        typedCompressed = self.compress(typed)
        pn = pt = 0
        countn = countt = ""
        while pn<len(nameCompressed):
            if (nameCompressed[pn] in string.ascii_lowercase) and (typedCompressed[pt] in string.ascii_lowercase):
                if countn!="":
                    if countt=="":
                        return False
                    else: 
                        if int(countt)<int(countn):
                            return False
                if nameCompressed[pn] != typedCompressed[pt]:
                    return False
                pn+=1
                pt+=1
                countn=""
                countt=""
            elif (nameCompressed[pn] not in string.ascii_lowercase) and (typedCompressed[pt] not in string.ascii_lowercase):
                countn+=nameCompressed[pn]
                countt+=typedCompressed[pt]
                pn+=1
                pt+=1
            elif (nameCompressed[pn] not in string.ascii_lowercase) and (typedCompressed[pt] in string.ascii_lowercase):
                return False
            else:
                pt+=1
                countt+=typedCompressed[pt]
        if countn!="":
            if countt=="":
                return False
            else:
                return (int(countn)<int(countt))
        for j in range(pt+1, len(typedCompressed)):
            if (typedCompressed[j] in string.ascii_lowercase):
                return False
        return True


        "alex"
        "aaleexa"
        "alex"



```


## Group Anagrams


### solved ~ 15 min
### Time complexity O(n), space O(n)
### 

https://leetcode.com/problems/group-anagrams/

<details><summary>Test Cases</summary><blockquote>

</blockquote></details>


```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        sorted_str = []
        d = {}
        for iw in range(len(strs)):
            sorted_w = "".join(sorted(strs[iw]))
            if d.get(sorted_w)!=None:
                d[sorted_w].append(strs[iw])
            else:
                d[sorted_w]=[strs[iw]]
        answ = []
        for key, value in d.items():
            answ.append(value)
        return answ
```


