**Note**
- Think  of searching, sorting , priority queue, binary search , may be used in the solution.
# 1. RAMDEV codechf
# 2. Sell all the cars codechef
```java
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc=new Scanner(System.in);
		int t=sc.nextInt();
		long mod=1000000007;
		
		while(t>0){
		    
		    int n=sc.nextInt();
           Long a[]=new Long[n];
           
		    for(int i=0;i<n;i++)
		    a[i]=sc.nextLong();
		    
		    Arrays.sort(a,  Collections.reverseOrder());
		    
		    long ans=0;
		    for(int j=0;j<n;j++){
		        
                ans+=(Math.max(0,a[j]-j));
		         ans%=mod;
		      
		    }
		     
		     
		     	System.out.println(ans);
		     --t;
		}
		
	
	}
}

```
# 3. Activity Selection Problem
# x. Chef and his study plans
# 4. Job Scheduling with Profit
# 5. Save Konoha 
# 6. Fractional Knapsack
# 7. Polo the penguine and the test
# 8. Efficient Delivery
# 9. Job Scheduling
- There are mainly six types of process scheduling algorithms-
- First come first serve
- shortest job first scheduling
- shortest remaining time
- priority scheduling
- round robin scheduling
- multilevel queue scheduling
# 10. Fair Elections 
# 11. Maximum weight difference
# 12. Ciel and Receipt
# 13. Hard Cash
