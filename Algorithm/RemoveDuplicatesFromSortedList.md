问题描述：
Given a sorted linked list, delete all duplicates such that each element appear only once.

例子：
```
For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
```
解法：

# Go
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func deleteDuplicates(head *ListNode) *ListNode {
    var current = head

    for current != nil && current.Next != nil {
        if current.Val != current.Next.Val {
            current = current.Next
        } else {
            current.Next = current.Next.Next
        }
    }
    return head

}
```
