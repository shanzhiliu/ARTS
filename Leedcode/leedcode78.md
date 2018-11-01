###leedcode78 - Subsets
#####题目:
 
 ``` 
 Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]

 ```


> 位运算操作,一个元素可以选择放入不放入.如果4个元素那就是那就2^4 = 16种 ,二进制边是(0000,0001,0010,0011,0100,0101,0110,0111,1000,1001,1010,1011,1100,1101,1110,1111)<br>
> 1是放入,0不放入.正好16种方式

```
 class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
         
         int all_set = 1<<nums.size();

    vector<vector<int>> result;

    for (int i = 0; i < all_set; ++i) {

        vector<int> item;
        for (int j = 0; j < nums.size(); ++j) {

            if(i & (1<<j))
            {
                item.push_back(nums[j]);
            }

        }

        result.push_back(item);
    }

    return result;
        
    }
};

```
