Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.
> 给定一个二叉树和一个值（sum），从根节点到叶子节点，把节点的值相加，如果这个值等于给定的值（sum），那么函数返回true，否则返回false

**Note:** 叶子节点的意思是没有任何的子节点

**Example:**
Given the below binary tree and sum = 22,
> 给定下面的二叉树和值（sum）22，
```go
      5
     / \
    4   8
   /   / \
  11  13  4
 /  \      \
7    2      1
```
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.
> 返回true，从根节点到叶子节点有一个`5>4>11>2`相加等于22.

**solution:**
##### 考察的其实就是一个深度优先遍历(depth first search),可以使用递归的思想来解决。
##### Go version 1
```go 
func hasPathSum(root *TreeNode, sum int) bool {
    if root == nil {
        return false
    }
    if root.Left != nil && root.Right != nil {
        return hasPathSum(root.Left, sum - root.Val) || hasPathSum(root.Right, sum - root.Val)
    } else if root.Left != nil || root.Right != nil {
        if root.Left != nil {
            return hasPathSum(root.Left, sum - root.Val)
        } else {
            return hasPathSum(root.Right, sum - root.Val)
        }
    } else {
        if root.Val == sum {
            return true 
        } else {
            return false
        }
    }
}
```
##### Go version 2
```go
func hasPathSum(root *TreeNode, sum int) bool {
    if root == nil  {
		return false
	}
	if root.Val == sum && root.Left == nil && root.Right == nil {
		return true
	}
	return hasPathSum(root.Left,sum-root.Val) || hasPathSum(root.Right,sum-root.Val)
}
```
##### 其实 1 和 2 的思想是一样的。只是 1 对左右节点分别做了处理。导致效率有些慢。1 耗时16ms, 2 耗时8ms
