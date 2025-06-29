### 876. Middle of the Linked List
## Q: 
https://leetcode.com/problems/middle-of-the-linked-list/description/

## Solution: 
https://takeuforward.org/data-structure/find-middle-element-in-a-linked-list/

## Code:

class Solution 
{

    public ListNode middleNode(ListNode head) {
        ListNode slow=head, fast=head;
        while(fast!=null && fast.next!=null)
        {
            slow=slow.next;
            fast=fast.next.next;
        }
        return slow;
        
    }
}

![image](https://github.com/user-attachments/assets/cc432bc7-fa21-4ed0-9b2a-7d5d3ff5d186)
