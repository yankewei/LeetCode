Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

### Example 1:
```
Input: 1->2->3->3->4->4->5
Output: 1->2->5
```

### Example 2:
```
Input: 1->1->1->2->3
Output: 2->3
```

### one
第一次遍历时使用`map`来存储每个Val值出现的次数。第二次遍历去掉出现两次的Val值。

```go
func deleteDuplicates(head *ListNode) *ListNode {
    if head == nil {
        return head
    }
    dict := make(map[int]int)
    tmp := head
    for tmp != nil {
        _, exists := dict[tmp.Val]
        if exists {
            dict[tmp.Val]++
        } else {
            dict[tmp.Val] = 1
        }
        tmp = tmp.Next
	}
    response := &ListNode{}
    response.Next = head
	res := response
	for response.Next != nil {
		if dict[response.Next.Val] > 1 {
			response.Next = response.Next.Next
		} else {
			response = response.Next
		}
	}
    return res.Next
}
```
