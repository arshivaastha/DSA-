# Merge two sorted linked list
### Q: 
https://leetcode.com/problems/merge-two-sorted-lists/description/
### Solution: 
https://takeuforward.org/data-structure/merge-two-sorted-linked-lists/

>### Brute force:
>Extract all the elements from both the lists into an additional array then sorting the array and creating a new combined linked list.
````
import java.util.*;
                                                                        
class Node {                                           // Node class represents a node in a linked list
                                            // Data stored in the node // Pointer to the next node in the list
    int data;
    Node next;
    Node(int data1, Node next1) {                  // Constructor with both data and next node as parameters
        data = data1;
        next = next1;
    }
    Node(int data1) {                             // Constructor with only data as a parameter, sets next to null
        data = data1;
        next = null;
    }
}

public class Main {
    static Node convertArrToLinkedList(ArrayList<Integer> arr) {        // Function to convert an array to a linked list
        Node dummyNode = new Node(-1);                                  // Create a dummy node to serve as the head of the linked list
        Node temp = dummyNode;
        
        for (int i = 0; i < arr.size(); i++) {                          // Iterate through the array and create nodes with array elements
            temp.next = new Node(arr.get(i));                           // Create a new node with the array element
            temp = temp.next;                                           // Move the temporary pointer to the newly created node
        }
        return dummyNode.next;                                          // Return the linked list starting from the next of the dummy node
    }

    // Function to merge two sorted linked lists
    static Node sortTwoLinkedLists(Node list1, Node list2) {
        ArrayList<Integer> arr = new ArrayList<>();
        Node temp1 = list1;
        Node temp2 = list2;               // Storing elements of both lists into an array

        while (temp1 != null) {                  // Add elements from list1 to the array
            arr.add(temp1.data);  
            temp1 = temp1.next;                 // Move to the next node in list1
        }
        while (temp2 != null) {                 // Add elements from list2 to the array
            arr.add(temp2.data);
            temp2 = temp2.next;
        }
                                                  // Sorting the array in ascending order
        Collections.sort(arr);
        Node head = convertArrToLinkedList(arr);     // Converting the sorted array back to a linked list
        return head;                                 // Return the head of the merged sorted linked list
    }

    // Function to print the linked list
    static void printLinkedList(Node head) {
        Node temp = head;
        while (temp != null) {
            // Print the data of the current node
            System.out.print(temp.data + " ");
            // Move to the next node
            temp = temp.next;
        }
        System.out.println();
    }
````

> ### Optimal
>  We employ a pointer based merging strategy where nodes from both linked lists are rearranged to form a single sorted linked list.
Initializing pointers at the head of the two lists, compare the values of the nodes and the smaller value node becomes the next
node in the merged list. The pointers are updated until one list is entirely merged, then attach the remaining nodes of the
other list directly to the merged list as they are already sorted.
### Intuition
When I saw the problem, I immediately thought of the merge step in merge sort, where two sorted lists are combined into a single sorted list. Since linked lists are involved, pointer manipulation is key. A dummy node helps manage the new list cleanly without needing special handling for the head.

### Approach
- Create a dummy node to act as the starting point of the merged list.
- Use a current pointer to build the merged list as you iterate.
- Compare the values at the heads of l1 and l2, attach the smaller one to current.next, and move the respective pointer forward.
- Continue this process until either list is exhausted.
- Attach any remaining nodes (since the lists are sorted, no more comparisons are needed).
- Return dummy.next as the head of the merged list.
### Complexity
Time complexity:
O(n+m) — where ( n ) and ( m ) are the lengths of l1 and l2.

Space complexity:
O(1) — No extra space is used beyond pointers.
![image](https://github.com/user-attachments/assets/bf566ffc-1661-4f97-a75b-4ab63ff074d4)

> ### Code
````
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1); // 🎯 Dummy node for simpler head management
        ListNode current = dummy; // 📍 Pointer to track the current end of merged list

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                current.next = list1; // ⬅️ Append smaller value from list1
                list1 = list1.next;
            } else {
                current.next = list2; // ➡️ Append smaller value from list2
                list2 = list2.next;
            }
            current = current.next; // 🏃 Move to next in merged list
        }

        // 🔗 Attach any remaining nodes from either list
        if (list1 != null) current.next = list1;
        if (list2 != null) current.next = list2;

        return dummy.next; // 🚀 Return head of merged list (after dummy)
    }
}


````
> ### Recursion
> 
````

class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

        if(list1!=null && list2!=null){
        if(list1.val<list2.val){
            list1.next=mergeTwoLists(list1.next,list2);
            return list1;
            }
            else{
                list2.next=mergeTwoLists(list1,list2.next);
                return list2;
        }
        }
        if(list1==null)
            return list2;
        return list1;
    }
}
````

