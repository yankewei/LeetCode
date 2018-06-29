Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).
For example, this binary tree [1,2,2,3,4,4,3] is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following [1,2,2,null,3,null,3] is not:
```
    1
   / \
  2   2
   \   \
   3    3
```

#### 思路：

数结构：
```go
type TreeNode struct {
    Val int
    Left *TreeNode
    Right *TreeNode
}
```
首先树如果是一个镜像树，那么首先它的节点的Val值是相等的，然后是树的左节点应该等于右节点值。也就是
`t1.Val === t2.Val && t1.Left === t2.Right && t1.Right === t2.Left`

#### 使用recursively(递归)
```go
func isSymmetric(root *TreeNode) bool {
    return isMirror(root, root)
}
func isMirror(r1 *TreeNode, r2 *TreeNode) bool {
	if r1 == nil && r2 == nil {
		return true
	}
	if r1 == nil || r2 == nil {
		return false
	}

	return (r1.Val == r2.Val) && isMirror(r1.Left, r2.Right) && isMirror(r1.Right, r2.Left)
}
```
