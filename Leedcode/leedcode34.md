### leedcode34 - Find First and Last Position of Element in Sorted Array
##### 题目:
 
 ```
 
 Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]


 ```


- 实现思路主要是二分法 查找对应的数字.

```
  class Solution {
public:
    
    int seachLeft(vector<int> &nums, int target)
{
    int begin = 0;
    int end = nums.size() - 1;
    

    while (begin <= end)
    {
        int mid = (begin + end) / 2;

        if(nums[mid] == target )
        {
            
            if(mid == 0 ||  nums[mid - 1] < target)
            {
                return mid;
            }
            end = mid -1;
        }


        else  if(nums[mid] > target)
        {
            end = mid -1;
        }

        else  if(nums[mid] < target)
        {
            begin = mid + 1;
        }
        
    }

    return  -1;
    
}


int  seachRight(vector<int> &nums, int target)
{
    int begin = 0;
    int end = nums.size() - 1;


    while (begin <= end)
    {
        int mid = (begin + end) / 2;

        if(nums[mid] == target )
        {

            if(mid == (nums.size() - 1) ||  nums[mid + 1] > target)
            {
                return mid;
            }
            
            begin = mid + 1;
        }


        else  if(nums[mid] > target)
        {
            end = mid -1;
        }

        else  if(nums[mid] < target)
        {
            begin = mid + 1;
        }

    }

    return  -1;
}
    
    
    vector<int> searchRange(vector<int>& nums, int target) {
        
         
       vector<int> result(2,-1);

       result[0] =  seachLeft(nums,target);
       result[1] =  seachRight(nums,target);

    return result;
        
        
        
    }
};

```
