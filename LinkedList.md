

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

# Reverse a linked list(Iterative)
```java
 public ListNode reverseList(ListNode head) {
        ListNode prev= null;
        ListNode curr = head;

        while(curr!=null){
            ListNode next = curr.next;
            curr.next=prev;
            prev= curr;
            curr= next;
        }

        return prev;
    }
```
# Reverse a linked list (Recursive)

```java
public ListNode reverseList(ListNode head) {

       if(head==null || head.next ==null)return head;
       ListNode prev =null;
       ListNode h2 = reverseList(head.next);
       head.next.next = head;
       head.next =prev;
       return h2; 
    }
```

# Middle of linked list
- Take care of && in the while loop
  ```java
   public ListNode middleNode(ListNode head) {
        
        if(head==null||head.next==null)return head;
        ListNode slow = head;
        ListNode fast = head;

        while(fast!=null &&fast.next!=null){
            fast= fast.next.next;
            slow=slow.next;
        }

        return slow;

    }
  ```

  # Remove nth node from end of linked list

  ```java
   public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode fast=head,slow=head;
        while(n>0){
            fast=fast.next;
            n--;
        }
        //edge case
        //if n==length of lkned list, then return head.next as new head
     if (fast==null) return head.next;
        while(fast.next!=null){
            slow=slow.next;
            fast=fast.next;
        }

        slow.next=slow.next.next;
        return head;
    }
  ```

  # Linked List Cycle

  ```java
  public boolean hasCycle(ListNode head) {
        ListNode fast=head, slow=head;
        if(head==null || head.next==null) return false;

        while(fast!=null&&fast.next!=null){
            fast= fast.next.next;
            slow=slow.next;
            if(slow==fast){
                return true;
            }
        }

       
        return false;
    }
  ```
  # Reverse LinkedList in group of K

  ```java
   static int lengthOfLinkedList(ListNode head) {
    int length = 0;
    while(head != null) {
        ++length;
        head = head.next;
    }
    return length;
   }

    public ListNode reverseKGroup(ListNode head, int k) {
        if(head == null||head.next == null) return head;
    
    int length = lengthOfLinkedList(head);
    
    ListNode dummyHead = new ListNode(0);
    dummyHead.next = head;
    
    ListNode pre = dummyHead;
    ListNode cur;
    ListNode nex;
    
    while(length >= k) {
        cur = pre.next;
        nex = cur.next;
        for(int i=1;i<k;i++) {
            cur.next = nex.next;
            nex.next = pre.next;
            pre.next = nex;
            nex = cur.next;
        }
        pre = cur;
        length -= k;
    }
    return dummyHead.next;
    }
  ```
# Delete Node

```java
public void deleteNode(ListNode node) {
        if(node==null) return;
        if(node.next==null){
            node=null;
            return;
        }
    ListNode prev=null;
        while(node.next!=null){
            node.val = node.next.val;
            prev=node;
            node=node.next;
        }
        prev.next=null;
       // node=null;
    }
```

# Detect the node where the cycle begins 

```java
 public ListNode detectCycle(ListNode head) {
        ListNode slow= head;
        ListNode fast = head;
        int idx = -1;
        boolean loopPresent=false;
        if(head==null || head.next==null)return null;

        while(fast!=null && fast.next!=null){
            fast = fast.next.next;
            slow= slow.next;
            if(fast==slow){
               
                loopPresent=true;
                 break;
            }
        }

        if(loopPresent==false)return null;
        fast=head;
        ListNode res=head;
        while(fast!=slow){
            fast=fast.next;
            slow=slow.next;
            idx++;
            res=fast;
        }
        return res;

    }
```
