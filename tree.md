+ [Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)
+ [Invert Binary Tree](#invert-binary-tree)
+ [Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)

## Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

### tried to solve without hints 
### Time complexity is O(log n), space - const
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
            
# ПЕРЕПИСАТЬ ЗАНОВО ПРОЩЕ
# ПОЧИТАТЬ ПРО ОБХОДЫ
```

## Invert Binary Tree

https://leetcode.com/problems/invert-binary-tree/

### tried to solve without hints 
### Time complexity is O(log n), space - const
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
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root:
            if root.left and root.left:
                left = self.invertTree(root.left)
                root.left = self.invertTree(root.right)
                root.right = left
            elif root.left:
                root.right = self.invertTree(root.left)
                root.left = None
            elif root.right:
                root.left = self.invertTree(root.right)
                root.right = None
            return root
```


## Binary Tree Level Order Traversal
https://leetcode.com/problems/binary-tree-level-order-traversal/

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

```python


```
