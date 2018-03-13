问题描述：You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

例子：
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

解决方法：
# PHP
```PHP
class ListNode
{
    public $val;
    public $next;
    public function __construct($val)
    {
        $this->val = $val;
        $this->next = null;
    }
}
class Solution
{
    function addTwoNumbers(ListNode $l1, ListNode $l2) {
        $res = new ListNode(0);
        $cur = $res;
        $add = 0;

        while ($l1->val && $l2->val) {
            $val = $l1->val + $l2->val + $add;
            $add = $val / 10;
            $res->next = new ListNode($val%10);
            $res = $res->next;
            $l1 = $l1->next;
            $l2 = $l2->next;
            if (!$l1 || !$l2) {
                break;
            }
        }
        return $cur->next;
    }
}
```
