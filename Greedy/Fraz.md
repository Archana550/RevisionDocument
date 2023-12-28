# RAMDEV codechef
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
