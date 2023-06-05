[Question](https://leetcode.com/problems/array-partition/)

```
int arrayPairSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int sum = 0;
        for(int i=0;i<nums.size()-1;i+=2){
            sum+=min(nums[i],nums[i+1]);
        }
        return sum;
    }
```

[Question](https://leetcode.com/problems/distribute-candies/)

```
int distributeCandies(vector<int>& candyType) {
        unordered_set<int>s;
        for(auto i:candyType){
            s.insert(i);
        }

        int req = candyType.size()/2;
        if(s.size()>=req){
            return req;
        }
        return s.size();
    }
```

[Question](https://leetcode.com/problems/longest-harmonious-subsequence/)

```
int findLHS(vector<int>& nums) {
        unordered_map<int,int>m;
        for(auto i:nums){
            m[i]++;
        }

        int mx = 0;
        for(auto i:m){
            if(m.find(i.first+1)!=m.end()){
                mx = max(mx, i.second+m[i.first+1]);
            }
        }

        return mx;
    }
```

[Question](https://leetcode.com/problems/can-place-flowers/)

```
bool canPlaceFlowers(vector<int>& f, int n) {
        int cnt = 0;
        for(int i=0;i<f.size();i++){
            if(f[i]==0){
                bool left = (i==0)||(f[i-1]==0);
                bool right = (i==f.size()-1)||(f[i+1]==0);
                if(left && right){
                    f[i]=1;
                    cnt++;
                }
            }
        }
        return cnt>=n;
    }
```

[Question](https://leetcode.com/problems/maximum-product-of-three-numbers/)

```
int maximumProduct(vector<int>& nums) {
        int mx1 = INT_MIN;
        int mx2 = INT_MIN;
        int mx3 = INT_MIN;
        int mn1 = INT_MAX;
        int mn2 = INT_MAX;

        for(int i=0;i<nums.size();i++){
            if(nums[i]>mx1){
                mx3 = mx2;
                mx2 = mx1;
                mx1 = nums[i];
            }else if(nums[i]>mx2){
                mx3 = mx2;
                mx2 = nums[i];
            }else if(nums[i]>mx3){
                mx3 = nums[i];
            }

            if(nums[i]<mn1){
                mn2 = mn1;
                mn1 = nums[i];
            }else if(nums[i]<mn2){
                mn2 = nums[i];
            }
        }

        return max(mx1*mx2*mx3, mx1*mn1*mn2);
    }
```

[Question](https://leetcode.com/problems/binary-search/)

```
 int search(vector<int>& nums, int target) {
        int s = 0, e = nums.size()-1;
        while(s<=e){
            int mid = (s+e)/2;
            if(nums[mid] == target){
                return mid;
            }else if(nums[mid]<target){
                s = mid+1;
            }else{
                e = mid-1;
            }
        }
        return -1;
    }
```

[Question](https://leetcode.com/problems/monotonic-array/)

```
 bool isMonotonic(vector<int>& nums) {
       bool inc = true;
       bool dec = true;
       for(int i=1;i<nums.size();i++){
           inc&=(nums[i-1]<=nums[i]);
           dec&=(nums[i-1]>=nums[i]);
       }
       return inc || dec;
    }
```

[Question](https://leetcode.com/problems/smallest-range-i/solutions/)

```
int smallestRangeI(vector<int>& nums, int k) {
        int mn = nums[0];
        int mx = nums[0];

        for(int i=1;i<nums.size();i++){
            mn = min(mn, nums[i]);
            mx = max(mx, nums[i]);
        }

        if(mn+k>=mx-k){
            return 0;
        }

        return ((mx-k) - (mn+k));
    }
```
