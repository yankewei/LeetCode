Given a linked list, rotate the list to the right by k places, where k is non-negative.

Example 1:
```
Input: 1->2->3->4->5->NULL, k = 2
Output: 4->5->1->2->3->NULL
Explanation:
rotate 1 steps to the right: 5->1->2->3->4->NULL
rotate 2 steps to the right: 4->5->1->2->3->NULL
```

Example 2:
```
Input: 0->1->2->NULL, k = 4
Output: 2->0->1->NULL
Explanation:
rotate 1 steps to the right: 2->0->1->NULL
rotate 2 steps to the right: 1->2->0->NULL
rotate 3 steps to the right: 0->1->2->NULL
rotate 4 steps to the right: 2->0->1->NULL
```

Notes:
1. 首先这个为可以用双指针来解。刚开始想着把本身的链表追加到自己的尾部，后来发现这就成为一个环了，不能解决这个问题，所有使用双指针来解。
2. 判断`k`和`head`是否为空，然后求出`head`长度，之后用`k%long`来求出一个值，判断是否为0，然后让一个指针走`long - k % long - 1`的长度，Next指向一个临时变量存储后边的list，再将Next指向nil。再遍历临时变量，Next指向最初的双指针的另一个指针就可以了

Solution:
```
func rotateRight(head *ListNode, k int) *ListNode {
    if k == 0 || head == nil {
        return head
    }
    rListNode := head
    tmpNode := head
    long := 0
    for head != nil {
        head = head.Next
        long++
    }
    k = k % long
    if k == 0 {
        return rListNode
    }
    l := long - k
    if l == 0 {
        return rListNode
    }
    for i := 0; i < l - 1; i++ {
        rListNode = rListNode.Next
    }
    response := rListNode.Next
    rListNode.Next = nil
    tmp := response
    for tmp.Next != nil {
        tmp = tmp.Next
    }
    tmp.Next = tmpNode
    return response
}
```
