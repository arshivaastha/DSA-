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
![image](https://github.com/user-attachments/assets/bf566ffc-1661-4f97-a75b-4ab63ff074d4)

````

````


