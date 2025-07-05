# Nth Root of a Number using Binary Search

video: https://www.youtube.com/watch?v=WjpswYrS2nY&list=PLgUwDviBIf0p4ozDR_kJJkONnb1wdx2Ma&index=64

notes: https://takeuforward.org/data-structure/nth-root-of-a-number-using-binary-search/
```
import java.util.*;

public class tUf {
    //Return 1 if mid == m
    //Return 0 if mid < m
    //Return 2 if mid > m
    public static int func(int mid, int n, int m) {
        long ans = 1;
        for (int i = 1; i <= n; i++) {
            ans = ans * mid;
            if (ans > m) return 2;
        }
        if (ans == m) return 1;
        return 0;
    }

    public static int NthRoot(int n, int m) {
        // Use binary search on the answer space:
        int low = 1, high = m;
        while (low <= high) {
            int mid = (low + high) / 2;
            int midN = func(mid, n, m);
            if (midN == 1) {
                return mid;
            } else if (midN == 0) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int n = 3, m = 27;
        int ans = NthRoot(n, m);
        System.out.println("The answer is: " + ans);
    }
}

```
