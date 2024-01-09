# Tower of hanoi
- Remember, we have to move N-1 disks from rod  to  rod using aux rod.
- We have to move N-1 disks from aux rod to to rod using from rod.
```java
class Hanoi {

    public long toh(int N, int from, int to, int aux) {
        // Your code here
        long moves = 0;
         if (N >= 1) {
      
        moves += toh(N - 1, from, aux, to);
        System.out.println( "move disk " + N + " from rod " +from + " to rod "+ to);
       
        moves++;
        
       
        moves += toh(N - 1, aux, to, from);
    }
    return moves;
    }
}
```
