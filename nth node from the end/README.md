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
