**Implement stack using array**
- https://www.codingninjas.com/studio/problems/stack-implementation-using-array_3210209?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf&leftPanelTabValue=SUBMISSION

**Implement queue using array**
-  https://www.codingninjas.com/studio/problems/implement-queue-using-arrays_8390825?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf&leftPanelTabValue=SUBMISSION

- https://leetcode.com/problems/remove-duplicate-letters/
- https://practice.geeksforgeeks.org/problems/nearest-smaller-tower--170647/1
- Good question


- https://leetcode.com/problems/removing-stars-from-a-string/description/
- class Solution {
    public String removeStars(String s) {
        StringBuilder c = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '*') {
                c.deleteCharAt(c.length() - 1);
            } else {
                c.append(s.charAt(i));
            }
        }
        return c.toString();
    }
}

- Balanced parenthesis
https://leetcode.com/problems/valid-parentheses/solutions/4316750/java-easy-code/

- Redundant brackets

**Next Greater Element | Next Largest Element**
- There will be three cases, if stack is empty, ans will be -1.
- Case 2: Stack top is greater than input element, then ans will be st top
- Case 3: St top is smaller than input element, than pop until we get something bigger.Take care of stack being empty here.
- https://www.geeksforgeeks.org/next-greater-element/
  
**Nearest Smaller Element**
- https://www.geeksforgeeks.org/next-smaller-element/
- https://www.geeksforgeeks.org/problems/help-classmates--141631/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article
- https://leetcode.com/problems/final-prices-with-a-special-discount-in-a-shop/description/

**Previous greater element**
- https://www.geeksforgeeks.org/previous-greater-element/
  
**Nearest Smaller to Right**
-
**Stock Span Problem**
- previous greater element ka index we need
- make stack of Pair and store the element ans it's index.
- at last just subtract i-index and we will get the answer.
- https://practice.geeksforgeeks.org/problems/stock-span-problem-1587115621/1
  
**Maximum Area Histogram**
-
**Max Area Rectangle in binary matrix**
-
**Rain Water Trapping**
-
**Minimum Element in Stack with Extra space**
-
**Minimum Element in Stack in 0(1) space**
-



