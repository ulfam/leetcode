+ [LRU Cache](#lru-cache)

## LRU Cache

https://leetcode.com/problems/lru-cache/

### tried to solve without hints - Didn't solve
### Time complexity is
### 

<details><summary>Test Cases</summary><blockquote> 
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3} BROKE HERE
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
</blockquote></details>


```python
class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity
        self.d = {}
        self.last = None
        self.size = 0
        

    def get(self, key: int) -> int:
        if self.d.get(key)!=None:
            return self.d[key]
        else:
            return -1

    def put(self, key: int, value: int) -> None:
        if self.d.get(key)!=None:
            self.d[key] = value
        else:
            if self.size < self.capacity:
                self.d[key] = value
                self.last = key
                self.size +=1
            else:
                del self.d[self.last]
                self.d[key] = value
                self.last = key


# дописать: чтобы работало c least. Переписать if /else на self.d.get(..., -1)
# переписать, чтобы проверка была на if key in self.d:


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)

```
