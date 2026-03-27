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

<hr>

## Approach 1: Brute Force
Intuition
- Traverse the list to calculate its length
- Identify the target node from the beginning:
`target index = length - n`
- Traverse again to reach that node

#### Implementation
```
public ListNode nthFromEnd(ListNode head, int n) {
    if (head == null) return null;

    int length = 0;
    ListNode temp = head;

    // Step 1: Calculate length
    while (temp != null) {
        length++;
        temp = temp.next;
    }

    // Step 2: Validate input
    if (n > length) return null;

    // Step 3: Find target node
    int target = length - n;
    temp = head;

    for (int i = 0; i < target; i++) {
        temp = temp.next;
    }

    return temp;
}
```
#### Complexity Analysis
| Metric | Value |
| :--- | :--- |
| **Time Complexity** | $O(N) + O(N) = O(N)$ |
| **Space Complexity** | $O(1)$ |

#### Drawbacks
- Requires two traversals
- Less efficient compared to optimal approach

<hr>

## Approach 2: Optimal (Two Pointer Technique)
Intuition
Use two pointers:
- fast pointer moves n steps ahead
- slow pointer starts from head

Maintain a gap of n nodes between them.

When fast reaches the end:
- slow will be at the nth node from the end

#### Implementation
```
public ListNode nthFromEnd(ListNode head, int n) {
    if (head == null) return null;

    ListNode fast = head;
    ListNode slow = head;

    // Step 1: Move fast n steps ahead
    for (int i = 0; i < n; i++) {
        if (fast == null) return null; // n > length
        fast = fast.next;
    }

    // Step 2: Move both pointers
    while (fast != null) {
        fast = fast.next;
        slow = slow.next;
    }

    return slow;
}
```
#### Complexity Analysis
| Metric | Value |
| :--- | :--- |
| **Time Complexity** | $O(N)$ |
| **Space Complexity** | $O(1)$ |

Why This Works

By maintaining a gap of n nodes:
- When fast reaches the end (null)
- slow is exactly n nodes behind → desired node

#### Edge Cases
- n > length → return null
- n == length → return head
- Single node list
- Empty list
