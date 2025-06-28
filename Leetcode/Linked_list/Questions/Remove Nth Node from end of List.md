> Intuition

The idea is simple:
We want to remove the n-th node from the end of the linked list. Since it's a singly linked list, we can't go backwards — so we first calculate the total length of the list and then remove the appropriate node from the beginning (length - n-th node from the start).


> Approach

1.First Pass: Traverse the list once to find its length (len).

2.Edge Case: If n == len, it means we need to remove the head node. So return head.next.

3.Second Pass: Traverse again to reach the node just before the one we want to remove (len - n - 1 steps).

4.Change the pointer of this node to skip the target node (temp.next = temp.next.next).

5.This approach ensures correctness with clean and simple code, using constant space.

> Complexity
- Time Complexity: 𝑂(𝐿)
Two passes through the list where L is the number of nodes.

- Space Complexity: 𝑂(1)
No extra space used — just pointer manipulation.

> Code

 Definition for singly-linked list:
 
  public class ListNode {
  
      int val;
      ListNode next;
      ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
  }
 
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        
        if(head.next==null)
        return null;                           //only one node
    
        int len =0;
        ListNode temp = head;
        
        while(temp!=null){
            len++;                             //size
            temp=temp.next;
        }

         if (len == n) {
            return head.next;                  //deleting head
        }
        temp=head;
       for(int i=0;i<len-n-1;i++){
        temp=temp.next;
       }
    
    temp.next=temp.next.next;
            //5-2+1=4 that means 4th index..
         


 return head;
    }
}
