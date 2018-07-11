Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.
> 将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

Example:
```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

Solution:
```go
/**
 * 这里有一个条件就是这两个链表已经排好序了，所有我们可以两个链表一起遍历
 * 如果有一个为空了，则直接让目标指针指向另一个链表就可以了
**/
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
	r := &ListNode{}
	reponse := r
	for l1 != nil || l2 != nil {
		if l1 == nil {
			r.Next = l2
			break
		}
		if l2 == nil {
			r.Next = l1
			break
		}
		if l1.Val <= l2.Val {
			r.Next, l1 = l1, l1.Next
		} else {
			r.Next, l2 = l2, l2.Next
		}
		r = r.Next
	}
	return reponse.Next
}
```
