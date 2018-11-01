### leedcode35 - Search Insert Position
##### 题目:
 
 ``` 
 
 Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Example 1:

Input: [1,3,5,6], 5
Output: 2
Example 2:

Input: [1,3,5,6], 2
Output: 1
Example 3:

Input: [1,3,5,6], 7
Output: 4
Example 4:

Input: [1,3,5,6], 0
Output: 0

 ```


- 实现思路主要二分查找对应位置 注意临界值的判断即可, 插入数据.

```
 
 class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        
        
         
 int index = -1;

    int begin = 0;
    int end = nums.size() - 1;


    while (index == -1)
    {
        int mid = (begin + end )/ 2;

        if(target == nums[mid])
        {
            index = mid;
        }

        else if(  target < nums[mid])
        {
              if(mid == 0 || nums[mid - 1] < target)
              {
                  index =  mid;
              }

            end = mid - 1;
        }

        else if(  target > nums[mid])
        {

            if(mid == (nums.size() - 1) || nums[mid + 1] > target)
            {

                index =  mid + 1;
            }

            begin = mid + 1;

        }

    }

    return index;

        
        
        
    }
};

```
