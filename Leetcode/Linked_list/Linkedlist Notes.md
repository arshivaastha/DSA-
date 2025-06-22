# Linked List Data Structure

A linked list is a fundamental data structure in computer science. It mainly allows efficient insertion and deletion operations compared to arrays. Like arrays, it is also used to implement other data structures like stack, queue and deque. Here’s the comparison of Linked List vs Arrays

Linked List:
Data Structure: Non-contiguous
Memory Allocation: Typically allocated one by one to individual elements
Insertion/Deletion: Efficient
Access: Sequential

Array:
Data Structure: Contiguous
Memory Allocation: Typically allocated to the whole array
Insertion/Deletion: Inefficient
Access: Random

Link to gfg notes:
https://www.geeksforgeeks.org/dsa/linked-list-data-structure/

## Reverse a linkedlist
Reverse a Linked List without using extra space. 

### Iterative Method
Time complexity - O(n)
Space complexity - O(1)

public void reverseList() 
{
       if(head == null || head.next == null) {
           return;
       }
       
       Node prevNode = head;
       Node currNode = head.next;
       while(currNode != null) {
           Node nextNode = currNode.next;
           currNode.next = prevNode;
           prevNode = currNode;
           currNode = nextNode;
       }
       head.next = null;
       head = prevNode;
   }

### Recursive Method
Time complexity - O(n)
Space complexity - O(1)  

public Node reverseListRecursive(Node head) {
       // empty node || last node or only one node
       if(head == null || head.next == null) {
           return head;
       }

       Node newHead = reverseListRecursive(head.next);
       head.next.next = head;
       head.next = null;
       return newHead;
   }

### Collections Method
Time complexity - O(n)
Space complexity - O(1)  

LinkedList<Integer> list2 = new LinkedList<>();

       list2.add(1);
       list2.add(2);
       Collections.reverse(list2);


