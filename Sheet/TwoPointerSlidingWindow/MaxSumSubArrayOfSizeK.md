
  long globalSum=0;
        for(int i=0;i<K;i++)globalSum+=Arr.get(i);
        
        
       
        long sum=globalSum;
        for(int i=K;i<N;i++){
           sum +=  Arr.get(i) - Arr.get(i-K);
           if(sum>globalSum){
               globalSum=sum;
           }
            
        }
        
        return globalSum;


        take care of the way you are adjusting the window. start from k and then increment i and decremetn i-k;
