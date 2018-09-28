https://leetcode.com/problems/house-robber/description/

*Example-1*

```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.

```

*Example-2*
```
Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
```

Recursive solution, that tries to compute the sum if we 
a) include the current element
b) exclude the current element

``` python
class Solution(object):
    def maxSumNonContiguous(self, arr, sum):
        arrLen = len(arr)
        if arrLen == 0:
            return 0
        if arrLen == 1:
            elemToAdd = arr[0]
            return max(sum + elemToAdd, sum)
        if arrLen == 2:
            return max(sum, sum + arr[0], sum + arr[1])
        return max(self.maxSumNonContiguous(arr[2:], sum+arr[0]) , self.maxSumNonContiguous(arr[1:], sum))
    def rob(self, nums):
        return self.maxSumNonContiguous(nums, 0)
```

The above is highly inefficient way of computing the sum. we need to memoize, the sum at each stage.

Let us maintain a 2-D array of size nums.length * 2.
Corresponding to each of the num in nums, the 2-D maintains the sum if a num is included in the sum or not.

``` python
def rob(nums):
    dp = [[0,0] for j in range(nums.length + 1)]
    for i in range(1, nums.length+1):
        dp[i][0] = max(dp[i - 1][0], dp[i - 1][1])
        dp[i][1] = num[i - 1] + dp[i - 1][0]
    return max(dp[num.length][0], dp[num.length][1])
```

In dp[][], the houses are numbered from 1 ... n, whereas in nums[], the houses are numbered 0 ... n-1.

For example for input [2, 7, 9, 3, 1], this is the 2D array that gets populated:
```
0 [0 0]
1 [0 2]
2 [2 7]
3 [7 11]
4 [11 10]
5 [11 12]
```

Note that dp[1][1] represents that if you rob the first house, which is nums[0], you will get $2.

Now instead of maintaining this 2-D Array, we can use 2 variables to check if the current House should be robbed or not.

the implementation for that is as follows:

``` python
def rob(self, nums):
    prevYes = 0  # represents the ongoing sum if the previousHouse was robbed
    prevNo = 0  # represents the ongoing sum if the previousHouse was not robbed
    for entry in nums:
        temp = prevNo
        prevNo = max(prevYes, prevNo) # ongoing sum which will become previous sum in next pass if we exclude the current house in the array
        prevYes = temp + entry # ongoing sum which will become previous sum in next pass if we include the current house in the array
        # also, note since discontinuous houses are to be robbed, for current house to be robbed the previous house shouldn't be robbed
    return max(prevYes, prevNo)
```