**Binary Search**
- https://leetcode.com/problems/binary-search/submissions/

-  mid= low + (high-low)/2;-> to prevent integer overflow.
- Find a page of the book.
- Find the first occurance of true.
- Search the element in sorted array.
- First and last occurance of sorted array(Leetcode 34)

**Minimum difference element in sorted array**
- https://www.youtube.com/watch?v=3RhGdmoF_ac&t=914s

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
- Take care to check the soted pat first and then check with target.
- https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/
  ```java
  class Solution {
    public int search(int[] nums, int target) {
        int low=0;
        int high = nums.length-1;
    int n = nums.length;
        while(low<=high){
            int mid = low + (high-low)/2;
            if(nums[mid]==target){
                return mid;
            }else if(nums[mid]>=nums[low]){
                if(target>=nums[low]&& target<nums[mid]){
                    high = mid-1;
                    
                }else{
                    low=mid+1;
                }
            }else{
                if(target<=nums[high]&&target>nums[mid]){
                    low=mid+1;
                }else{
                    high= mid-1;
                }
            }
        }
        return -1;
    }
}



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
  
 **Peak element**
  - Binary search on answer concept
  - from mid move towars the more promising side
  - our answer is the element which is geater than the left as well as the right side element.
  - so accordingly decide the more promising side and move on.
  - if mid element is greater than mid+1 or mid-1 return mid element.
  - https://leetcode.com/problems/find-peak-element/
  - edge case id mid=0 or if mid=n-1 only compare with the next or prev element and return;

**Find maximum element in Bitonic Array**
- similar to peak element
- https://www.geeksforgeeks.org/find-element-bitonic-array/
  

**Search in row wise and column wise sorted matrix [good question]**
  - binary search on sorted matrix
  - start from top rigth corner
  - return when indexes goes out of bound
  - https://leetcode.com/problems/search-a-2d-matrix/
  
**Allocate minimum number of pages**
- https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1
- imp

**Find Nth root of M**
- Search space is 1 to m, apply binary search on that
- check if the mid element is answer by creating one extra function that checks mid times value is equal to m or not.
- https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article

 # Search an element in Bitonic Array
 # Matrix median
 # Find the elemetn that appeared once in a sorted array
 # Median of two sorted arrays
 - search space - length of smaller array, will find mid and take that much element from smaller array and remaining from larger array.
 - answer found if the four variables are balanced i.e l1<r2 && l2<r1
 - if l1>r2 then decreade the search space i.e high = mid-1;
 - else low = mid+1;
 ```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n1 = nums1.length;
        int n2 = nums2.length;

        if(n1>n2){
            return findMedianSortedArrays(nums2, nums1);
        }
        int low = 0;
        int high = n1;
        int left = (n1+n2+1)/2;
        int n = n1+n2;
        while(low<=high){

            int mid1 = low + (high-low)/2;
            int mid2 = left-mid1;
            int l1 = Integer.MIN_VALUE;
            int r1= Integer.MAX_VALUE;
            int l2 = Integer.MIN_VALUE;
            int r2= Integer.MAX_VALUE;

            if(mid1<n1)r1 = nums1[mid1];
            if(mid2<n2)r2 = nums2[mid2];

            if(mid1 - 1>= 0)l1= nums1[mid1-1];
            if(mid2 - 1>= 0)l2= nums2[mid2-1];


            if(l1<=r2 && l2<=r1){
                if(n%2!=0){
                    return Math.max(l1,l2);
                }else{
                    return (double)(Math.max(l1,l2)+Math.min(r1,r2))/2.0;
                }
            }else if(l1>r2){
                high= mid1-1;
            }else{
                low=mid1+1;
            }
        }
        return 0;
    }
}
```
 # kth element of two sorted arrays

 ```java
public class Solution {
    public static int ninjaAndLadoos(int nums1[], int nums2[], int n1, int n2, int k) {
        // Write your code here.
   

       if(n1>n2){
           return ninjaAndLadoos(nums2, nums1,n2,n1,k);
       }
       int low = Math.max(0, k-n2);
       int high = Math.min(k,n1);
       int left = k;
       int n = n1+n2;
       while(low<=high){

           int mid1 = low + (high-low)/2;
           int mid2 = left-mid1;
           int l1 = Integer.MIN_VALUE;
           int r1= Integer.MAX_VALUE;
           int l2 = Integer.MIN_VALUE;
           int r2= Integer.MAX_VALUE;

           if(mid1<n1)r1 = nums1[mid1];
           if(mid2<n2)r2 = nums2[mid2];

           if(mid1 - 1>= 0)l1= nums1[mid1-1];
           if(mid2 - 1>= 0)l2= nums2[mid2-1];


           if(l1<=r2 && l2<=r1){
              
                   return Math.max(l1,l2);
               
           }else if(l1>r2){
               high= mid1-1;
           }else{
               low=mid1+1;
           }
       }
       return 0;
    }
}

```
 # Aggressive cows
 - search space max-min element in array
 - apply binarysearch, return high
 - make function inside to check if mid value can the req answer or not
```java
 import java.util.*;
public class Solution {
    public static boolean func(int[]stalls,int dis, int cows){
        int countcows = 1;
        int prev = stalls[0];

        for(int i=1;i<stalls.length;i++){
            if((stalls[i]-prev)>=dis){
                countcows++;
                prev=stalls[i];
            }
            if(countcows>=cows)return true;
        }
        return false;
    }
    public static int aggressiveCows(int []stalls, int k) {
        //    Write your code here.
        Arrays.sort(stalls);
        int n = stalls.length;
        int low=1;
        int high=stalls[n-1]-stalls[0];

        while(low<=high){
            int mid = low + (high-low)/2;

            if(func(stalls,mid, k)==true){
                low = mid+1;
            }else{
                high= mid-1;
            }
        }

        return high;
    }
}
```
# Allocate Books
- count number of students can be allocated with the mid values, and accordingly adjust mid
```java
public class Solution {
    
    public static int countStudents(ArrayList<Integer> arr, int mid){
        
        long countPages=0;
        int numStudent=1;
       
        for(int i=0;i<arr.size();i++){
            if(countPages+arr.get(i)<=mid){
                countPages+=arr.get(i);
            }else{
                numStudent++;
                countPages=arr.get(i);
            }
        }
    return numStudent;
    }
    public int books(ArrayList<Integer> arr, int B) {
        
        int n = arr.size();
        if(B>n)return -1;
        int low = Collections.max(arr);
        int high=0;
        for(int i:arr){
            high+=i;
        }
        
        while(low<=high){
            int mid = low + (high-low)/2;
            int students=countStudents(arr, mid);
            if(students>B){
               low=mid+1;
            }else{
                high = mid-1;
            }
        }
        return low;
    }
}
```
