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

# CYCLE DETECTION USING BFS

```java
class Solution {
    // Function to detect cycle in an undirected graph.
     class Pair
    {
        int node;
        int parent;
        Pair(int x,int y)
        {
            this.node=x;
            this.parent=y;
        }
    }
    public boolean bfs(int v, ArrayList<ArrayList<Integer>> adj, boolean vis[]){
        vis[v]= true;
        Queue<Pair> q = new LinkedList<Pair>();
        Pair p = new Pair(v,-1);
        q.add(p);
         while(!q.isEmpty()){
            int node = q.peek().node;
            int parent = q.peek().parent;
            q.remove();
            
            for(int i: adj.get(node)){
                if(vis[i]==false){
                    vis[i]=true;
                    q.add(new Pair(i, node));
                }else if(i!=parent){
                   return true;
                }
            }
        }
        return false;
    }
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
       
        
        boolean vis[]= new boolean[V];
       for(int i=0;i<V;i++){
           if(!vis[i]){
               if(bfs(i, adj, vis))return true;
           }
       }
       return false;
        
       
        
    }
}
```

# Cycle detection using dfs- TLE

```java
class Solution {
    // Function to detect cycle in an undirected graph.
    public static boolean dfs(int node, int parent, ArrayList<ArrayList<Integer>> adj, boolean vis[]){
        
        vis[node]=true;
        
        for(int i : adj.get(node)){
            if(vis[i]==false){
                vis[i]=true;
                if(dfs(i, node,adj, vis))return true;
            }else if(i !=parent){
                return true;
            }
        }
        return false;
        
    }
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
        
        boolean vis[]= new boolean[V];
        for(int i=0;i<V;i++){
            if(vis[i]==false){
                if(dfs(i, -1, adj, vis))return true;
            }
        }
        
        return false;
    }
}
```

# Cycle detection in directed graph using dfs
- same as the dfs code just one extra visited array and backtrack it after returning so as to check if this is the result of this dfs search itself.

```java

class Solution {
    
    public boolean dfs(int i,ArrayList<ArrayList<Integer>> adj, boolean vis[], boolean dfsvis[] ){
        
        vis[i]=true;
        dfsvis[i]= true;
        
        for(int j: adj.get(i)){
            if(vis[j]==false){
                vis[j]=true;
                if(dfs(j,adj,vis,dfsvis))return true;
            }else if(dfsvis[j]==true){
                return true;
            }
        }
        dfsvis[i]= false;
        return false;
        
    }
    // Function to detect cycle in a directed graph.
    public boolean isCyclic(int V, ArrayList<ArrayList<Integer>> adj) {
        // code here
        
        boolean vis[]= new boolean[V];
        boolean dfsvis[]= new boolean[V];
        
        for(int i=0;i<V;i++){
            if(dfs(i,adj, vis, dfsvis))return true;
        }
        
        return false;
    }
}
```

# Detect cycle in directed graph using bfs
- bfs code and indegree calculation easy one.

```java
//{ Driver Code Starts
import java.util.*;
import java.io.*;
import java.lang.*;

class DriverClass {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();

        while (t-- > 0) {
            ArrayList<ArrayList<Integer>> list = new ArrayList<>();
            int V = sc.nextInt();
            int E = sc.nextInt();
            for (int i = 0; i < V; i++)
                list.add(i, new ArrayList<Integer>());
            for (int i = 0; i < E; i++) {
                int u = sc.nextInt();
                int v = sc.nextInt();
                list.get(u).add(v);
            }
            if (new Solution().isCyclic(V, list) == true)
                System.out.println("1");
            else
                System.out.println("0");
        }
    }
}
// } Driver Code Ends


/*Complete the function below*/

class Solution {
    // Function to detect cycle in a directed graph.
    public boolean isCyclic(int V, ArrayList<ArrayList<Integer>> adj) {
        // code here
        
        int indegree[]= new int[V];
        
        for(int i=0;i<V;i++){
            for(int j : adj.get(i)){
                indegree[j]++;
            }
        }
        
        Queue<Integer> q = new LinkedList<Integer>();
        
        for(int i=0;i<V;i++){
            if(indegree[i]==0){
                q.add(i);
            }
        }
        int count=0;
        while(!q.isEmpty()){
            int top = q.poll();
            count++;
            
            
            for(int i : adj.get(top)){
                indegree[i]--;
                 if(indegree[i]==0){
                  q.add(i);
               }
            }
        }
        
        
        if(count==V)return false;
        else return true;
    }
}
```

# Topological sort -bfs

```java

class Solution
{
    //Function to return list containing vertices in Topological order. 
    static int[] topoSort(int V, ArrayList<ArrayList<Integer>> adj) 
    {
        // add your code here
        
        int topo[]= new int[V];
        int p=0;
        Queue<Integer> q = new LinkedList<Integer>();
        int indegree[] = new int[V];
        
        for(int i=0;i<V;i++){
            for(int k: adj.get(i)){
                indegree[k]++;
            }
        }
        
        for(int i=0;i<V;i++){
           if(indegree[i]==0){
               q.add(i);
           }
        }
        
        while(!q.isEmpty()){
            int node = q.poll();
            
            topo[p++]=node;
            
            for(int k: adj.get(node)){
                indegree[k]--;
                if(indegree[k]==0){
                    q.add(k);
                }
            }
        }
        
        return topo;
    }
}
```
# Topological sort dfs
```java
class Solution
{
    //Function to return list containing vertices in Topological order. 
    
    public static void dfstopo(int i, ArrayList<ArrayList<Integer>> adj, boolean vis[], Stack<Integer> st ){
        
            vis[i]= true;
            
            for(Integer t: adj.get(i)){
                
                if(vis[t]==false){
                    //vis[t]= true;
                    dfstopo(t, adj,vis,st);
                }
            }
        st.push(i);
        return;
        
    }
    
    static int[] topoSort(int V, ArrayList<ArrayList<Integer>> adj) 
    {
        // add your code here
        
        //ArrayList<Integer> topo= new ArrayList<Integer>();
        boolean vis[]= new boolean[V];
        Stack<Integer> st= new Stack<Integer>();
        
        for(int i=0;i<V;i++){
            if(vis[i]==false)
            dfstopo(i,adj,vis,st);
        }
        
        int res[]= new int[V];
        int k=0;
        while(!st.isEmpty()){
            res[k++]= st.peek();
            st.pop();
        }
        return res;
    }
}
```

# Number of Island- Stack overflow somehow

```java
class Solution {

    public void dfs(int i, int j, char[][]grid, boolean vis[][]){
        vis[i][j]=true;
        int n = grid.length;
        int m = grid[0].length;
        if(i<0||i>=n||j<0||j>=m|| grid[i][j]=='0')return;
       dfs(i,j+1, grid, vis);
       dfs(i, j-1, grid, vis);
       dfs(i+1,j, grid, vis);
       dfs(i-1, j, grid, vis);
    }
    public int numIslands(char[][] grid) {
         int n = grid.length;
         if(n==0)return 0;
        int m = grid[0].length;
        boolean vis[][]= new boolean[n][m];
        int cnt=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1'&& vis[i][j]==false){
                    dfs(i,j,grid,vis);
                    cnt++;
                }
            }
        }

        return cnt;
    }
}
```
