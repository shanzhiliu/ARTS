###leedcode55 - Jump Game
#####题目:
 
 ``` 
 
 Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

Example 1:

Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
             
 ```


```
- 1)设置变量jump代表当前所处的位置，初始化为0；
- 2)设置变量max_index代表从第0位置至第jump位置这个过程中，最远可到达的位置，
初始化为index[0]。
- 3.利用jump扫描index数组，直到jump达到index数组尾部或jump超过max_index，扫描过程中，
更新max_index。
- 4.若最终jump 为数组长度，则返回true，否则返回false。
```

```
 class Solution {
public:
    bool canJump(vector<int>& nums) {
        
        std::vector<int> index;

        for(int i = 0; i < nums.size() ; i++) {
            index.push_back(i+nums[i]);
        }

        int jump = 0;
        int max_index = index[0];

        while(jump < index.size()  &&  jump <= max_index) {

            if(max_index < index[jump]){
                max_index = index[jump];
            }
            jump ++;
        }

        if(jump == nums.size()) {
        return true;
        }

        return false;

        
    }
};

```
