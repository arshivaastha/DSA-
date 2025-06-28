Q:
92. Reverse Linked List II
https://leetcode.com/problems/reverse-linked-list-ii/description/

Solution: https://www.youtube.com/watch?v=vE__gU1MUnw&t=3s
![image](https://github.com/user-attachments/assets/c67c0177-7d57-41c3-9802-ba1f882f15c4)

> Code:
  Definition for singly-linked list:

  public class ListNode {
  
      int val;
      ListNode next;
      ListNode() {}
      ListNode(int val) { this.val = val; }
      ListNode(int val, ListNode next) { this.val = val; this.next = next; }
  }
 
class Solution {

    public ListNode reverseBetween(ListNode head, int left, int right) {
   
        ListNode dummy = new ListNode(0); // created dummy node
        dummy.next = head;
        ListNode prev = dummy; // intialising prev pointer on dummy node
        
        for(int i = 0; i < left - 1; i++)
            prev = prev.next; // adjusting the prev pointer on it's actual index
        
        ListNode curr = prev.next; // curr pointer will be just after prev
        // reversing
        for(int i = 0; i < right - left; i++){
            ListNode temp = curr.next; // temp pointer will be after curr
            curr.next = temp.next;
            temp.next = prev.next;
            prev.next = temp;
        }
        return dummy.next;
    }
}
