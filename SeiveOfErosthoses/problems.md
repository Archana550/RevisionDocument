# Count Primes leetcode medium
```java
class Solution {
    public int countPrimes(int n) {
        boolean seive[]= new boolean[n+1];
        //if(n<=2)return 0;
        for(int i=0;i<=n;i++)seive[i]=true;
        int count=0;

        for(int i=2;i*i<=n;i++){
            if(seive[i]==true){
                for(int j=i*i;j<=n;j=j+i){
                    seive[j]=false;
                }
            }
        }

        for(int i=2;i<n;i++){
            if(seive[i]==true){
                count++;
            }
        }

        return count;
    }
}
```
