# Q: Diameter of Binary Tree

https://leetcode.com/problems/diameter-of-binary-tree/description/

https://takeuforward.org/data-structure/calculate-the-diameter-of-a-binary-tree/

## Solution:
### Brute
<img width="769" height="629" alt="image" src="https://github.com/user-attachments/assets/edaebdd7-587b-48ce-bf44-778c048f9be3" />

```
class Solution {
  
    public int diameterOfBinaryTree(TreeNode root) { 
 if (root == null) return 0;

        // 1. Diameter passing through root
        int leftHeight = height(root.left);
        int rightHeight = height(root.right);
        int throughRoot = leftHeight + rightHeight;

        // 2. Diameter in left subtree
        int leftDiameter = diameterOfBinaryTree(root.left);

        // 3. Diameter in right subtree
        int rightDiameter = diameterOfBinaryTree(root.right);

        // 4. Return the maximum
        return Math.max(throughRoot, Math.max(leftDiameter, rightDiameter));
    }

    private int height(TreeNode node) {
        if (node == null) return 0;
        return 1 + Math.max(height(node.left), height(node.right));
    }
}

```
<img width="723" height="524" alt="image" src="https://github.com/user-attachments/assets/74287b4c-ee5e-459f-9603-ee2cf79a3050" />

### Optimal:

```
class SolutionBrute {
    int diameter = 0;

 int diameterOfBinaryTree(Node root) {
        calculateHeight(root);
        return diameter;
    }
    int calculateHeight(Node node) {
        if (node == null) {
            return 0;
        }
        int leftHeight = calculateHeight(node.left);
        int rightHeight = calculateHeight(node.right);

        diameter = Math.max(diameter, leftHeight + rightHeight);
        return 1 + Math.max(leftHeight, rightHeight);
    }

   
}
```
<img width="578" height="79" alt="image" src="https://github.com/user-attachments/assets/eb149df0-2797-4c10-a6ad-4878622f7451" />


## Comparison
<img width="910" height="607" alt="image" src="https://github.com/user-attachments/assets/ec945894-6513-451f-8142-302e9ac95d90" />

<img width="914" height="580" alt="image" src="https://github.com/user-attachments/assets/f0fb3a0c-29dd-4897-a221-a162311e920d" />


