# 2. Add Two Numbers

## Description

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

## Tag

Linked List

## Enlightenment

第一个自己尝试不看答案、问题类别写的code，感觉在开始写之前，先要理解题意，抓出主干，然后想一些比较典型的test case，再下手的话可以涵盖大多数的情况

## My #1 Attempt (05/13/18)

```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode result = new ListNode(-1);
        ListNode current = new ListNode(carry);
        result.next = current;

        while (l1 != null || l2 != null) {
            int valOfL1 = l1 == null ? 0 : l1.val;
            int valOfL2 = l2 == null ? 0 : l2.val;

            carry = ((valOfL1 + valOfL2 + current.val) - (valOfL1 + valOfL2 + current.val) % 10) / 10;
            current.val = (valOfL1 + valOfL2 + current.val) % 10;

            l1 = l1 == null ? l1 : l1.next;
            l2 = l2 == null ? l2 : l2.next;
            if (carry != 0) {
                current.next = new ListNode(carry);
            } else if (l1 == null && l2 == null) {
                break;
            } else {
                current.next = new ListNode(0);
            }
            current = current.next;
        }
        return result.next;
    }
}
```
