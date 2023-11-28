**Binary Search**
- https://leetcode.com/problems/binary-search/submissions/

-  mid= low + (high-low)/2;
- Find a page of the book.
- Find the first occurance of true.
- Search the element in sorted array.
- First and last occurance of sorted array(Leetcode 34)

**Find the first and last occurrence of an element in an array**
- make two different functions for first and last occurance. Change the code of binary search a little accordingly.
- https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/submissions/

**Number of Occurance**
- find the difference between first and last occurance
- write seperate codes for both first and last occurance, try if we can merge them if we want
- only one answer, keep a flag and try to merge.
- https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article

**Find the rotation count in rotated sorted array**
- Number of rotation = index of minimum element
- minimum index is smaller than left as well as right index element
- Compare the mid element with start and end. If start is greater than mid then first half is 
  sorted and if mid is smaller than end then second half is sorted. Go towards the unsorted part.
- https://www.geeksforgeeks.org/problems/rotation4723/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article

**Search in rotated sorted array**
- https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/


**Searching in a nearly sorted array**
- compare with the mid, mid-1 and mid+1 th elements and increment/decrement mid by 2.
- https://www.geeksforgeeks.org/search-almost-sorted-array/

**Single element in a sorted array**
- https://leetcode.com/problems/single-element-in-a-sorted-array/submissions/

**Find ceil of an element in an array**
- https://www.geeksforgeeks.org/ceil-in-a-sorted-array/

**Find floor of an element in an array**
- https://www.geeksforgeeks.org/floor-in-a-sorted-array/

**Next alphabetical element**
- similar to ceil problem
- https://leetcode.com/problems/find-smallest-letter-greater-than-target/

**Find the position of element in infinite sorted array**
- mark arr[0]=low and arr[1]= high and then low=high and high = high*2 till high<target.
- this way we bound the target and then apply binary search.
- https://www.geeksforgeeks.org/find-position-element-sorted-array-infinite-numbers/

**Find the index of 1st one in a binary sorted array**
- https://www.geeksforgeeks.org/find-index-first-1-sorted-array-0s-1s/

**Find the index of 1st one in an infinite binary sorted array**
- infinite sorted and
- first occurrance combination
- https://www.geeksforgeeks.org/find-index-first-1-infinite-sorted-array-0s-1s/

- **Minimum difference element in a sorted array**
- **Binary search on answer concept**
- **Peak element**
- **Find maximum element in Bitonic Array**
- **Search an element in Bitonic Array**
- **Search in row wise and column wise sorted array**
- **Allocate minimum number of pages**

**Find Nth root of M**
- https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article
