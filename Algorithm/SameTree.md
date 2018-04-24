问题描述：
Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

例子：
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```
```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```

解决方法：
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isSameTree(p *TreeNode, q *TreeNode) bool {
    if p == nil && q == nil {
       return true;
    }
    if p == nil || q == nil {
        return false;
    }
    if (p.Val == q.Val) {
        return isSameTree(p.Left, q.Left) && isSameTree(p.Right, q.Right);
    }
    return false;
}
```
