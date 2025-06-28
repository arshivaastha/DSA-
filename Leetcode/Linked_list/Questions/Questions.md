### 1) "237. Delete Node in a Linked List"
   
Solution:
https://leetcode.com/problems/delete-node-in-a-linked-list/solutions/6511385/beats-100-smart-solution-notes-java-c-python-o-1

### 2) " 24. Swap Nodes in Pairs https://leetcode.com/problems/swap-nodes-in-pairs/description/"

Solution: https://leetcode.com/problems/swap-nodes-in-pairs/solutions/6527722/beats-100-easy-smart-solution-notes-java-c-python
> Approach
There are two critical edge cases for the head:
First, if the list contains only two nodes, we simply swap them and return the new head.
Second, if there are more than two nodes, we perform the first pair's swap and reset the head before moving on to the rest of the list.
Once the head is set, we only have to worry about two main scenarios: lists with an even number of nodes and lists with an odd number of nodes. In the even-length case, every pair can be swapped without issue. In the odd-length case, the last node will remain as-is because there's no partner to swap it with.
Another important consideration is linking the pairs together properly as we proceed. After we swap each pair, we need to connect the last node of the previous swapped pair to the new head of the current pair. Then we point the second node of the swapped pair to the next node in the list so that we can advance the pointer and continue. Getting these connections right is what keeps the list intact as we move along.
Here’s a quick illustration:
Before swap:
A -> B -> C -> D -> E
Swap A and B:
B -> A -> C -> D -> E
Swap C and D:
B -> A -> D -> C -> E
E stays as it is because it has no partner.
