[Question](https://leetcode.com/problems/two-sum/)

 ```
 vector<int> twoSum(vector<int>& nums, int target) {
       unordered_map<int,int>m;
       for(int i=0;i<nums.size();i++){
           if(m.find(target-nums[i])!=m.end()){
               return {m[target-nums[i]],i};
           }
           m[nums[i]] = i;
       }
       return {};
  }
  ```
[Question](https://leetcode.com/problems/remove-element/)

```
int removeElement(vector<int>& nums, int val) {
       int i=0;
       for(int j=0;j<nums.size();j++){
           if(nums[j]!=val){
               nums[i] = nums[j];
               i++;
           }
       }
       return i;
    }
```
[Question](https://leetcode.com/problems/search-insert-position/)

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

[Question](https://leetcode.com/problems/plus-one/)

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
[Question](https://leetcode.com/problems/merge-sorted-array/)

```
void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int k = m+n-1;
        int i = m-1;
        int j = n-1;
        while(i>=0 && j>=0){
            if(nums1[i]>nums2[j]){
                nums1[k--] = nums1[i--];
            }else{
                nums1[k--] = nums2[j--];
            }
        }

        while(i>=0){
            nums1[k--] = nums1[i--];
        }
        while(j>=0){
            nums1[k--] = nums2[j--];
        }
    } 
```
[Question](https://leetcode.com/problems/contains-duplicate/)

```
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int,int>m;
        for(auto i:nums){
            if(m.find(i)!=m.end()){
                return true;
            }
            m[i]++;
        }
        return false;
    }
```
[Question](https://leetcode.com/problems/move-zeroes/)

```
void moveZeroes(vector<int>& nums) {
        int zc = 0;
        for(auto i: nums){
            if(i!=0){
                nums[zc]=i;
                zc++;
            }
        }

        for(int i=zc;i<nums.size();i++){
            nums[i]=0;
        }
    }
```