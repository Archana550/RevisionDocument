**CSUMQ**
import java.util.*;
import java.lang.*;

class Main
{
	public static void main (String[] args) throws java.lang.Exception
	{
		Scanner sc = new Scanner(System.in);
		
		int n= sc.nextInt();
		int[] arr= new int[n];
		int[] prefixSum = new int[n];
		
		int sum=0;
		for(int i=0;i<n;i++){
			arr[i]= sc.nextInt();
			sum+= arr[i];
			prefixSum[i]= sum;
		}
		int Q = sc.nextInt();
		while(Q>0){
			int l= sc.nextInt();
			int r = sc.nextInt();
			int right = prefixSum[r];
			
			int left = 0;
			if(l!=0)
			left=prefixSum[l-1];
			System.out.println(right-left);
			Q--;
		}
	}
}
