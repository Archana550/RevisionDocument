- https://www.youtube.com/watch?v=qDdQeB5PpA4&list=PL3MjzjRBJNQEAWJ3CCRg8qX9C7dDuOFPo&index=2

- Heap
- Key operations-
- getMin()-O(1)
- insert()-O(logn)
- delete()-adjust()-O(logn)
- (n/2-0)heapify.-O(n)

 ``` import java.util.* ;
import java.io.*; 

public class Solution {
    

    public static void insert( ArrayList<Integer> heap,int val){
        
        int n = heap.size();
        if(n==0){
        heap.add(val);
        return;
        }
        heap.add(val);
         n = heap.size();
        int parent = (n-2)/2;
        int child = n-1;
        while(child>0 && heap.get(child)<heap.get(parent)){
        if(heap.get(child)<heap.get(parent)){
            int temp = heap.get(child);
            heap.set(child, heap.get(parent));
            heap.set(parent, temp);
            child = parent;
            parent= (child-1)/2;
           

        }
         
        }


        
    }

    public static void adjust( ArrayList<Integer> heap,int ind, int n){

        int item = heap.get(ind);
        int child = 2*ind + 1;
        int minIndex=0;
        while(child<heap.size()){
            if(heap.get(ind)<heap.get(child)){
                minIndex= child;
            }
            if(heap.size()>child+1 && heap.get(minIndex)<heap.get(child+1)){
                minIndex = child+1;
            }
            int temp = heap.get(minIndex);
            heap.set(ind, heap.get(minIndex));
            ind = minIndex;
            child = 2*ind+1;


       }
    }

    public static int delete( ArrayList<Integer> heap){
        int min= heap.get(0);
        if(heap.size()==1)return min;
        heap.set(0, heap.size()-1);
        heap.remove(heap.size()-1);
        adjust(heap, 0, heap.size());

        return min;
    }

    static int[] minHeap(int n, int[][] q) {
        // Write your code here.
        ArrayList<Integer> ans = new ArrayList<Integer>();
        
         ArrayList<Integer> heap = new ArrayList<Integer>();
        for(int i=0;i<n;i++){
            if(q[i][0]==0){
                insert(heap,q[i][1]);
            }else{
               int v= delete(heap);
               ans.add(v);
            }
        }
        int size= ans.size();
        int res[] = new int[size];
        for(int i=0;i<res.length;i++){
            res[i]= ans.get(i);
        }

        return res;
    }
}```
