+ [Number of Islands](#number-of-islands)

## Number of Islands

https://leetcode.com/problems/number-of-islands/

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.


### Didn't solve - looked at Solution
### Time complexity is
### 

<details><summary>Test Cases</summary><blockquote> 

</blockquote></details>


```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        visited = set()
        col, row = len(grid), len(grid[0])
        ans = 0
        dir = [[0, 1], [1, 0], [0, -1], [-1, 0]]

        def helper(c: int, r: int):
            visited.add((c, r))
            for i, j in dir:
                nc, nr = c+i, r+j
                if 0 <= nc < col and 0 <= nr < row and grid[nc][nr] == "1" and (nc, nr) not in visited:
                    helper(nc, nr)
        
        for c in range(col):
            for r in range(row):
                if (c, r) not in visited and grid[c][r] == "1":
                    helper(c, r)
                    ans += 1
        
        return ans

```
