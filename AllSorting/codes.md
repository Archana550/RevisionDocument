
# Bubble sort
- T.C = O(N^2)
-  S.C =o(1)
- no of rounds=n-1
- number of iterations= n*(n-1)/2
- swap each adjacent elemnet in one iteration if its greater than the next one.
- ![bubblesort](https://github.com/Archana550/RevisionDocument/assets/51438542/78293d31-7f4a-4035-807e-a6187e4cf436)

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

# Selection sort
- select the element that is smallest and inset at first
- ![selectionsort](https://github.com/Archana550/RevisionDocument/assets/51438542/f45b8cad-0224-49d0-b0e6-669419c60ddc)
```java

class Solution
{
	int  select(int arr[], int i)
	{
        // code here such that selectionSort() sorts arr[]
        int min=arr[i];
        int minidx=i;
        for(int idx=i+1;idx<arr.length;idx++ ){
            if(arr[idx]<min){
                min= arr[idx];
                minidx=idx;
            }
        }
        return minidx;
	}
	
	void selectionSort(int arr[], int n)
	{
	    //code here
	    
	    for(int i=0;i<n-1;i++){
	       
	       int minidx= select(arr, i);
	      
	       int temp=arr[minidx];
	       arr[minidx]=arr[i];

	       arr[i]= temp;
	       
	    }
	}
}
```
# Insertion Sort
- heap adjust algorithm uses this.
- insert the target element in it's right position by shifting other greater elements back.

- ![insertionsort](https://github.com/Archana550/RevisionDocument/assets/51438542/e7507b30-b177-4aaa-ad0f-6faebc9880ef)

```java

class Solution
{
  static void insert(int arr[],int i)
  {
       // Your code here
       int j=i-1;
       int key = arr[i];
       while(j>=0 && arr[j]>key){
           arr[j+1]=arr[j];
           j--;
       }
       arr[j+1]=key;
       
  }
  //Function to sort the array using insertion sort algorithm.
  public void insertionSort(int arr[], int n)
  {
      //code here
      for(int i=1;i<n;i++){
          insert(arr, i);
      }
  }
}
