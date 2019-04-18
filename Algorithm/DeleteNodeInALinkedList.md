##### 描述
###### 编写一个方法，从链表中把给定的节点删除掉。（节点不会是最后一个）
##### 解法
###### 不想多说，明白链表是什么的都会做
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func deleteNode(node *ListNode) {
    node.Val = node.Next.Val
    node.Next = node.Next.Next
}
```