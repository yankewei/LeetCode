Given a non-empty, singly linked list with head node `head`, return a middle node of linked list.
> 给定一个非空，单向的链表，头结点`head`,返回链表的中间节点。

If there are two middle nodes, return the second middle node.
> 如果有两个中间节点，返回第二个。

##### Example 1:
```
Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
```

##### Example 2:
```
Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
```
##### Note:
- 给定节点的数量 1 到 100。

##### solution
###### 可以用双指针的方式来解决，因为我们不需要知道链表的长度，所以使用一个慢指针，一个快指针，快指针一次走两步，慢指针一次走一步，这样的话当快指针走到最后，慢指针就是结果了。
```go
//这里需要注意的就是 for 循环里的两个都是 fast 指针，因为 fast 可能会为nil，
func middleNode(head *ListNode) *ListNode {
    slow, fast := head, head
    for fast != nil && fast.Next != nil {
        slow = slow.Next
        fast = fast.Next.Next
    }
    return slow
}
```
