# LinkedList
### 1. Reverse LinkedList
<a href = "https://leetcode.com/problems/reverse-linked-list-ii/submissions/">LeetCode 92. Reverse Linked List II </a>
- Iterative
```java
public ListNode reverseList(ListNode head) {
	if (head == null){
		return null;
	}
	ListNode curr = head;
	ListNode dummy = null;
	ListNode prev = dummy;
	while (curr != null) {
		ListNode nextCheck = curr.next;
		curr.next = prev;
		prev = curr;
		curr = nextCheck;
	}
	return prev;
}
```
- recursive
``` java
public ListNode reverseList(ListNode head) {
	if (head == null || head.next == null){
		return head;
	}
	ListNode last = reverseList(head.next);
	head.next.next = head;
	head.next = null;
	return last;
}
```
- <a style = "color : red">**N recursion**</a>
```java
ListNode successor = null;
public ListNode reverseN(ListNode head, int n) {
	if (n == 1) {
		successor = head.next;
		return head;
	}
	ListNode last = reverseN(head.next, n - 1);
	head.next.next = head;
	head.next = successor;
	return last;
}
```