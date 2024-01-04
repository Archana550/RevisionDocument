# Clone graph
```java
class Solution {
    public void dfs(Node currnode, HashMap<Node,Node> hmap){
      // Node currnodeclone= hmap.get(currnode);
       for(Node n : currnode.neighbors){
           if(!hmap.containsKey(n)){
            Node neighborclone = new Node(n.val);
          
            hmap.put(n,neighborclone);
            
           }
           hmap.get(currnode).neighbors.add(hmap.get(n));
       }
     for(Node n : currnode.neighbors){
         if(hmap.get(n).neighbors.size()==0){
             dfs(n,hmap);
        }
     }
       return;
    }
    public Node cloneGraph(Node node) {
        if(node==null)return null;
        HashMap<Node, Node> hmap = new HashMap<Node, Node>();

        Node newhead = new Node(node.val);
        hmap.put(node,newhead);
        dfs(node, hmap);
        return newhead;
    }
}
