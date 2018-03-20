问题描述：
Remove all elements from a linked list of integers that have value val.

例子：
```
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5
```

解决方法：
#Go
```go
func removeElements(head *ListNode, val int) *ListNode {
    result := ListNode{0,head}
    tmp := &result

    for tmp.Next != nil {
        if tmp.Next.Val == val {
            tmp.Next = tmp.Next.Next
        } else {
            tmp = tmp.Next
        }
    }
    return result.Next
}
```
