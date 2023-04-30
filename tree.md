+ [Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)

## Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

### tried to solve without hints 
### Time complexity is 
### 

<details><summary>Test Cases</summary><blockquote>
        

</blockquote></details>


```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is not None:
            max_depths = 1
            if (not root.left) and (not root.right):
                return max_depths
            else:
                max_depths+= max (self.maxDepth(root.left), self.maxDepth(root.right))
            return max_depths
        else:
            return 0

```
