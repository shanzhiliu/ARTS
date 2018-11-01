###leedcode402 - Remove K Digits
#####题目:
 
 ```
 Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.

Note:
The length of num is less than 10002 and will be ≥ k.
The given num does not contain any leading zero.
Example 1:

Input: num = "1432219", k = 3
Output: "1219"
Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
Example 2:

Input: num = "10200", k = 1
Output: "200"
Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.
Example 3:

Input: num = "10", k = 2
Output: "0"
Explanation: Remove all the digits from the number and it is left with nothing which is 0.


 ```


- 实现思路是标准的贪心算法,如果 i 位数字比 i+1 位数字大,便可以去掉.

```
     class Solution {
public:
    string removeKdigits(string num, int k) {
        
 vector<int> S;
    string result = "";

    for (int i = 0; i < num.length(); ++i) {
        int number = num[i] - '0';

        while (S.size() && S[S.size() - 1]  > number  && k > 0) {
            S.pop_back();
            k--;
        }

        if(number !=0 || S.size()!= 0 )
        {
            S.push_back(number);
        }

    }



    while (S.size() != 0 && k> 0)
    {
        S.pop_back();
        k--;
    }

    for (int j = 0; j < S.size(); ++j) {
        result.append(1,'0' + S[j]);
    }

    if(result == "")
    {
        result = "0";
    }

    return result;

    }
};

```
