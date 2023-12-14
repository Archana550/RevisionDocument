Variable length sliding window
create one hashmap and go through the string and keeps pushing in the hashmap. If the size of the hmap becomes k then calculate and store ans.
If it becomes  greater than k, remove elements and start increasing the i pointer.

 HashMap<Character, Integer> hm = new HashMap<Character,Integer>();
        
        int n = s.length();
        int i=0;
        int j=0;
        
        
        int  resLen =-1;
        
        while(j<n){
            
            
            char ch = s.charAt(j);
            int freq = hm.getOrDefault(ch,0);
            
            hm.put(ch, freq+1);
            
            
            if(hm.size()>k){
                
                while(hm.size()>k){
                char ch1 = s.charAt(i);
                int freq1= hm.get(ch1);
                hm.put(ch1, freq1-1);
                
                if(hm.get(ch1)==0){
                    hm.remove(ch1);
                }
                 i++;
                }
               
            }
            
            if(hm.size()==k){
               int len = j - i + 1; 
               resLen = Math.max(resLen, len);
               
            }
            j++;
        }
        
        return resLen;
