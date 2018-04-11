问题描述：Given a linked list, remove the n<sup>th</sup> node from the end of list and return its head.

例子：
```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

提示：
Given n will always be valid.
Try to do this in one pass.

解法：
###Go(一)
```Go
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    long := 0
    tmp := &ListNode{0, nil}
    tmp.Next = head
    first := head
    for first != nil {
        long++
        first = first.Next
    }
    long -= n
    first = tmp
    for long > 0 {
        first = first.Next
        long--
    }
    if first.Next != nil {
        first.Next = first.Next.Next
    } else {
        first.Next = nil
    }
    return tmp.Next
}
```
###Go(二)
```Go
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    tmp := &ListNode{0, nil}
    tmp.Next = head

    first := tmp
    second := tmp

    for i := 1; i <= n + 1; i++ {
        first = first.Next
    }

    for first != nil {
        first = first.Next
        second = second.Next
    }
    second.Next = second.Next.Next
    return tmp.Next
}
```
