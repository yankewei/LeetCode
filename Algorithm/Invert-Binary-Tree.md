翻转一棵二叉树。
示例：
输入：
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
输出：
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

#### 题解
> 使用递归的思想即可
```go
func invertTree(root *TreeNode) *TreeNode {
    if root != nil {
        tmp := root.Left
        root.Left = root.Right
        root.Right = tmp
        invertTree(root.Left)
        invertTree(root.Right)
    }
    return root
}
```
