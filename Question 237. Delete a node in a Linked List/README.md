# Leetcode Question 237<br> Delete a node in a Linked List
Link to the problem <a>https://leetcode.com/problems/delete-node-in-a-linked-list</a>
<hr>

## Problem Understanding
You are given:
- A reference to a node (node) inside a singly linked list
- You do NOT have access to the head

You must:
- Delete this node from the list
- Maintain order of remaining elements

Key Constraint (Most Important Insight)
- The given node is NOT the last node.

#### Hidden Implication or Standard Approach for Node deletion
In a singly linked list:
- You normally need previous node to delete current node
- But here, you don’t have access to the previous node
  
⭐ So standard deletion is impossible
<hr>

## Brute Force Approach
Approach:
- Traverse from the head to find the just previous node of the given node
- Update `previousNode.next = previousNode.next.next` to delete the given node

Problem
- We don't have access to the head

So, this approach is invalid.
<hr>

## Optimal Approach (Only approach)
Intuition: Since we cannot delete the current node directly but using this node we can delete the next node. We can replace the data of the given node from the next node data and simply delete that node.

<br>Simply
- We replace its value with the next node’s value
- Then delete the next node instead

<hr>

## Edge Cases & Failure Scenarios
#### 1. Node is last node
- Would cause node.next to be null → crash
- Already guaranteed in problem constraints

#### 2. Duplicate values concern
- Not applicable (values are unique)

#### 3. Memory leak concern
In Java:
- Garbage Collector handles removed node
  
In C++:
- Would need manual delete (important interview point)
