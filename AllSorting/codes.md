
# Bubble sort
- T.C = O(N^2)
-  S.C =o(1)
- no of rounds=n-1
- number of iterations= n*(n-1)/2
- swap each adjacent elemnet in one iteration if its greater than the next one.

```java
class Solution
{
    public static void swap(int arr[], int i, int j){
        int temp = arr[i];
        arr[i]= arr[j];
        arr[j]= temp;
    }
    //Function to sort the array using bubble sort algorithm.
	public static void bubbleSort(int arr[], int n)
    {
        //code here
     
        
        int cnt=0;
        for(int j=0;j<n-1;j++){
            cnt=0;
            for(int i=0;i<n-j-1;i++){
                if(arr[i]>arr[i+1]){
                    cnt++;
                    swap(arr,i,i+1);
                }
            }
            if(cnt==0)break;
        }
    }
}


```
