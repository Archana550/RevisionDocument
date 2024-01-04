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
```
# DFS TRAVERSAL
```java
public void dfs(int j, ArrayList<ArrayList<Integer>> adj,int[] visited, ArrayList<Integer> ans){
        visited[j]=1;
        ans.add(j);
        
        for(int i: adj.get(j)){
            if(visited[i]==0){
                dfs(i,adj,visited,ans);
            }
        }
    }
    public ArrayList<Integer> dfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
        int visited[]= new int[V];
        ArrayList<Integer> ans = new ArrayList<Integer>();
        for(int i=0;i<V;i++){
            if(visited[i]==0)
            dfs(i,adj,visited,ans);
        }
        
        return ans;
    }

```
# BFS TRAVERSAL
- take care of visited array
```java
 public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
        ArrayList<Integer> ans = new ArrayList<Integer>();
        
        Queue<Integer> q = new LinkedList<Integer>();
        int vis[]= new int[V];
        
        q.add(0);
        
        while(!q.isEmpty()){
            
            int i=q.poll();
            ans.add(i);
            vis[i]=1;
            
            for(int j: adj.get(i)){
                if(vis[j]==0){
                    vis[j]=1;
                    q.add(j);
                }
            }
            
        }
        
        return ans;
        
    }
```