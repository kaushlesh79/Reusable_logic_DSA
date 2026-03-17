### Comparator Sort Function

```cpp
sort(intervals.begin(), intervals.end(), [](vector<int>& a, vector<int>& b) {
    return a[0] < b[0];
});

```

### Boyles Moore Voting Algorithm (For Majority Element 2)
```cpp
 class Solution {
public:
// optimal approach O(1) space and O(n) Times Complexity using boyles moore 
    vector<int> majorityElement(vector<int>& nums) {

        vector<int>res;

        int e1 = 0 , e2=0 , c1 =0 ,c2=0;

        for(auto x : nums){
        
        if(x==e1) c1++;
        else if (x==e2) c2++;
        else if (c1 ==0 ){
            e1=x;
            c1=1;
        }else if (c2==0){
            e2=x;
            c2=1;
        }else{
            c1--;
            c2--;
        }


        }
        c1=0 , c2=0;

        for(auto x : nums){
           if(x==e1)c1++;
           else if(x==e2) c2++;
        }

        if(c1> nums.size()/3) res.push_back(e1);
        if(c2>nums.size()/3) res.push_back(e2);

        return res;
        
    }
};
```

### dfs traversal in graph 
```cpp
 Things to take care of in dfs
1. parent element , //from whe are starting the traversal
2. visited array (vector<int>Vis(v+1 , false) ,// helps in tracking all the element traverse till now
3. condition (if (vis[parent]) return ;  // already visited helps us to check if there is any cycle there
4. vis[parent] = true ;  ,// marking the parent visited and entering in their teritory that is traversing their child
5. for(auto v : vis[parent])  , //if(!vis[v]) dfs(adj , v , vis)  going to child and recursively calling dfs traversal for its child considering it as parent 










   class Solution {
  public:
  
  vector<int>dfs_ordered_element;  // array storing vertices in the order how we traverse through dfs
  
  
  void dfs_in_graph(vector<vector<int>>& adj , int parent , vector<int>&Visited){
      
      if(Visited[parent] == true) return;
      
      Visited[parent] = true;
      
      dfs_ordered_element.push_back(parent);
      
      for(auto v : adj[parent]){
          
          if(!Visited[v]){
              
              dfs_in_graph(adj , v , Visited);
          }
          
      }
  }
  
    vector<int> dfs(vector<vector<int>>& adj) {
        // Code here
        int V = adj.size();
        
        vector<int>Visited(V , false); // visited array in dfs for tracking which all vertices has been visited also can be used for tracking if there is cycle in graph
        
        int parent =0; // as given we have to start traversal from 0
        
        dfs_in_graph(adj , parent , Visited);
        
        return dfs_ordered_element;
    }
};

```
