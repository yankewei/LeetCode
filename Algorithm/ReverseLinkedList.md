问题描述：
Reverse a singly linked list.

解决方法
# Go

```Go
/**
* 初始化一个ListNode，用来保存整个反转后的链表，prev来保存指针位置，
* 遍历链表
*   保存下一个节点指针tmp
*   当前的下一个节点指针指向prev
*   prev指针移动到当前节点的指针位置
*   把下一次执行的节点替换为tmp，否则就是prev了
*/
func reverseList(head *ListNode) *ListNode {
    if head == nil {
        return head
    }
    var prev *ListNode

    for head != nil {
        tmp := head.Next
        head.Next = prev
        prev = head
        head = tmp

    }
    return prev
}
```
