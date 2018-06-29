Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Note: A leaf is a node with no children.

Example:

Given binary tree [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```
return its depth = 3.

#### solution:
```go
func maxDepth(root *TreeNode) int {
    var left, right int
	if root != nil {
		left = 1 + maxDepth(root.Left)
		right = 1 + maxDepth(root.Right)
	}

	if left > right {
		return left 
	}
	return right
}
```
