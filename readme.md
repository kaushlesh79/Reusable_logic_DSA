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
