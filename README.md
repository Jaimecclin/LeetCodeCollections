# 98. Validate Binary Search Tree
## Level - Medium 
## Question
https://leetcode.com/problems/validate-binary-search-tree/

### Thought 1 - Recursive
Defination of Binary Tree:
 - The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

We set lower and upper bound to validate each node value. For left node, the upper bound is root's value. Value of left node can't be larger than root value. On the contrary, the lower bound of right node is root value. 
```python=
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        def isValid(root, lower=float('-inf'), upper=float('inf')):
            if not root:
                return True
            if root.val <= lower or root.val >= upper:
                return False
            if root.left:
                if not isValid(root.left, lower, root.val):
                    return False
            if root.right:
                if not isValid(root.right, root.val, upper):
                    return False
            return True
        return isValid(root)
```