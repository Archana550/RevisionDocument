-- Reverse a linkedlist
-- merge sort in singly linked list

**LRU (Least Recently Used) CACHE**
- https://leetcode.com/problems/lru-cache/submissions/
- Use a doubly linked list "class Node" and a hashmap<Integer, Node>
- create two functions add and delete Node.
- make sure to initialize the head, tail, capacity and create link between tail and head in capacity function.
- In the addition function insert the key and Node to hashmap also .
- In the remove function delete it from the HashMap also.
- remove the least recently used node, right before the tail while adding if capacity is reached.
- and if already present delete from there and insert again

**LFU CACHE(Least Frequently Used)**
- https://leetcode.com/problems/lfu-cache/

-- slow and fast pointer approach
[Take care of the base cases and the condition in while loop]
 public static Node<Integer> midPoint(Node<Integer> head) {
        //Your code goes here
      
        if(head==null )return null;
        if(head.next==null) return head;

          Node<Integer> slow=head;
        Node<Integer> fast = head.next;
        
        while( fast!=null&& fast.next!=null ){
            slow=slow.next;
            fast= fast.next.next;
        }

        return slow;
    }

-- Merge two sorted linked list

[Take care of the base cases]
    
    public static Node<Integer> mergeTwoSorteds(Node<Integer> head1, Node<Integer> head2) {
        //Your code goes here
        if(head1==null&& head2==null)return null;
        if(head1==null)return head2;
        if(head2==null)return head1;
        Node<Integer> res=null;
        Node<Integer> tail= null;

        Node<Integer> temp1= head1;
        Node<Integer> temp2 = head2;

        while(temp1!=null && temp2!=null){
            if(temp1.data<=temp2.data){
                if(res==null){
                    res=new Node<Integer>(temp1.data);
                    tail= res;
                   // tail= tail.next;
                }else{
                    tail.next = new Node(temp1.data);
                    tail= tail.next;
                }
                temp1= temp1.next;
            }else{

                if(res==null){
                    res=new Node<Integer>(temp2.data);
                    tail= res;
                   // tail= tail.next;
                }else{
                    tail.next = new Node(temp2.data);
                    tail= tail.next;
                }
                temp2= temp2.next;

            }
        }

       if(temp1!=null){
            tail.next=temp1;
        }
        if(temp2!=null){
            tail.next = temp2;
        }

        return res;
    }

}
