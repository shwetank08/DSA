<aside>
💡  Given an integer array nums of length n and an integer target, find three integers
in nums such that the sum is closest to the target.
Return the sum of the three integers.
</aside>

```
int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(),nums.end());
        int close = INT_MAX;
        int ans = 0;
        for(int i=0;i<nums.size()-1;i++){
            int s = i+1, e = nums.size()-1;
            while(s<e){
                int cursum = nums[i]+nums[s]+nums[e];
                if(abs(target - cursum)<close){
                    close = abs(target-cursum);
                    ans= cursum;
                }
                if(cursum>target){
                    e--;
                }else{
                    s++;
                }
            }
        }
        return ans;
    }
```
<aside>
💡 Given an array nums of n integers, return an array of all the unique quadruplets
 [nums[a], nums[b], nums[c], nums[d]] such that:
           ● 0 <= a, b, c, d < n
           ● a, b, c, and d are distinct.
           ● nums[a] + nums[b] + nums[c] + nums[d] == target

You may return the answer in any order.
 </aside>

```
vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>>ans;
        if(nums.empty()){
            return ans;
        }
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size();i++){
            for(int j=i+1;j<nums.size();j++){
                
                int target2 = target-nums[i]-nums[j];
                int s=j+1,e=nums.size()-1;
                
                while(s<e){
                    int twosum = nums[s]+nums[e];
                    if(twosum < target2){
                        s++;
                    }else if(twosum > target2){
                        e--;
                    }else{
                        vector<int>quad(4,0);
                        quad[0] = nums[i];
                        quad[1] = nums[j];
                        quad[2] = nums[s];
                        quad[3] = nums[e];
                        ans.push_back(quad);
                        while(s < e && nums[s]==quad[2]){
                            s++;
                        }
                        while(s < e && nums[e]==quad[3]){
                            e--;
                        }
                    }
                }
                while(j+1<nums.size() && nums[j+1]==nums[j]){
                    j++;
                }
            }
            while(i+1<nums.size() && nums[i+1]==nums[i]){
                i++;
            }
        }
        return ans;
    }
```

<aside>
💡 A permutation of an array of integers is an arrangement of its members into a
sequence or linear order.

For example, for arr = [1,2,3], the following are all the permutations of arr:
[1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1].

The next permutation of an array of integers is the next lexicographically greater
permutation of its integer. More formally, if all the permutations of the array are
sorted in one container according to their lexicographical order, then the next
permutation of that array is the permutation that follows it in the sorted container.

If such an arrangement is not possible, the array must be rearranged as the
lowest possible order (i.e., sorted in ascending order).

● For example, the next permutation of arr = [1,2,3] is [1,3,2].
● Similarly, the next permutation of arr = [2,3,1] is [3,1,2].
● While the next permutation of arr = [3,2,1] is [1,2,3] because [3,2,1] does not
have a lexicographical larger rearrangement.

Given an array of integers nums, find the next permutation of nums.
The replacement must be in place and use only constant extra memory.
</aside>

```
void nextPermutation(vector<int>& nums) {
        int k = nums.size()-2, i = nums.size()-1;
        for(;k>=0;k--){
            if(nums[k]<nums[k+1]){
                break;
            }
        }
        if(k<0){
            reverse(nums.begin(),nums.end());
            return;
        }
        for(;i>k;i--){
            if(nums[i]>nums[k]){
                break;
            }
        }
        swap(nums[i],nums[k]);
        reverse(nums.begin()+k+1,nums.end());
    }
```
<aside>
💡 Given a sorted array of distinct integers and a target value, return the index if the
target is found. If not, return the index where it would be if it were inserted in
order.

You must write an algorithm with O(log n) runtime complexity.
</aside>

```
int searchInsert(vector<int>& nums, int target) {
        int s = 0, e = nums.size()-1;
        while(s<=e){
            int mid = s+(e-s)/2;
            if(nums[mid]==target){
                return mid;
            }else if(nums[mid]>target){
                e = mid-1;
            }else{
                s = mid+1;
            }
        }
        return s;
    }
```

<aside>
💡 You are given a large integer represented as an integer array digits, where each
digits[i] is the ith digit of the integer. The digits are ordered from most significant
to least significant in left-to-right order. The large integer does not contain any
leading 0's.

Increment the large integer by one and return the resulting array of digits.
</aside>

```
vector<int> plusOne(vector<int>& digits) {
        int c = 1;
        for(int i=digits.size()-1;i>=0;i--){
            if(c){
                int sum = digits[i]+c;
                c = sum/10;
                sum = sum%10;
                digits[i] = sum;
            }
        }
        if(c){
            digits.insert(digits.begin(),1);
        }
        return digits;
    }
```

<aside>
💡 Given a non-empty array of integers nums, every element appears twice except
for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only
constant extra space.
</aside>

```
int singleNumber(vector<int>& nums) {
        int uni = 0;
        for(auto i:nums){
            uni^=i;
        }
        return uni;
    }
```

<aside>
💡 You are given an inclusive range [lower, upper] and a sorted unique integer array
nums, where all elements are within the inclusive range.

A number x is considered missing if x is in the range [lower, upper] and x is not in
nums.

Return the shortest sorted list of ranges that exactly covers all the missing
numbers. That is, no element of nums is included in any of the ranges, and each
missing number is covered by one of the ranges.

</aside>

```
vector<string> summaryRanges(vector<int>& nums) {
       int n = nums.size();
       vector<string>ans;

       string tmp = "";

       for(int i=0;i<n;i++){
           int j = i;
           while(j+1<n && nums[j+1]==nums[j]+1){
               j++;
           }
           if(j>i){
               tmp+=to_string(nums[i]);
               tmp+="->";
               tmp+=to_string(nums[j]);
           }else{
               tmp+=to_string(nums[i]);
           }
           ans.push_back(tmp);
           tmp="";
           i=j;
       }
       return ans;
    }
```