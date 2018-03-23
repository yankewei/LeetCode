问题描述：
Given a singly linked list, determine if it is a palindrome.

Follow up:
Could you do it in O(n) time and O(1) space?

解决方法：

* 思路

  利用快慢指针法，当fast指针到链表末尾时，把链表后边的一半反转，和前边一半比较

# Go
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func isPalindrome(head *ListNode) bool {

    if head == nil ||  head.Next == nil{
        return true
	}
	var slow = head
	var fast = head

	for fast != nil && slow != nil {
		slow = slow.Next
		if (fast.Next == nil) {
			fast = fast.Next
		} else {
			fast = fast.Next.Next
		}
	}
	var prev *ListNode
    for slow != nil {
        tmp := slow.Next
        slow.Next = prev
        prev = slow
        slow = tmp
	}
	slow = prev
	fast = head
    for slow != nil {
        if slow.Val != fast.Val {
			return false
		}
        slow = slow.Next
        fast = fast.Next
    }
    return true
}
```
