# Merge Sort
- make illusionary partition in the array
- in the merge part make two arrays of the size of the left and riht part of mid, copy elements and then use two pinter to sort
```java
int len1 = m-l+1;
         int len2 = r-m;
         
        //  creating two empty arrays
         int first[] = new int[len1];
         int second[] = new int[len2];
         
        //  inserting value of first sub array in newly created array 
         int mainArrayIndex = l;
         for(int i=0;i<len1;i++){
             first[i] = arr[mainArrayIndex++];
         }
         
         //  inserting value of second sub array in newly created array 
         mainArrayIndex = m+1;
         for(int i=0;i<len2;i++){
             second[i] = arr[mainArrayIndex++];
         }
         
         
        //  merge two sorted array
        
        int index1 = 0;
        int index2 = 0;
        mainArrayIndex = l ;
        while(index1<len1 && index2<len2){
            if(first[index1]<second[index2]){
                arr[mainArrayIndex++] = first[index1++];
            }
            else{
                arr[mainArrayIndex++] = second[index2++];
            }
        }
        
        while(index1<len1){
            arr[mainArrayIndex++] = first[index1++];
        }
        
        while(index2<len2){
            arr[mainArrayIndex++] = second[index2++];
        }
    }
    void mergeSort(int arr[], int l, int r)
    {
        //code here
        if(l>=r)return;
        int mid = l +(r-l)/2;
        
        mergeSort(arr,l,mid);
        mergeSort(arr,mid+1,r);
        
        merge(arr,l,mid,r);
        
    }
}
```
# Quick Sort
