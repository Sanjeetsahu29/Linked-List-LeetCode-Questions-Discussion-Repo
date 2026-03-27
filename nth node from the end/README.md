# Nth Node From End of Linked List
Given the head of a singly linked list and an integer n, return the nth node from the end of the list.

Constraints:
- The linked list contains at least one node
- 1 ≤ n ≤ size of the list

### Problem Understanding

In a singly linked list, we cannot traverse backward, so accessing elements from the end is non-trivial.

To solve this problem, we need a way to:
- Either determine the length first, or
- Maintain a relative distance between nodes
