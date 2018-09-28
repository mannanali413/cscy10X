https://leetcode.com/problems/house-robber-ii/description/

**Example 1:**
```
Input: [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2),
             because they are adjacent houses.
```

**Example 2:**

```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```

``` python
class Solution(object):
    def robHelper(self, numsNew):    
        prevYes = 0  # represents the ongoing sum if the previousHouse was robbed
        prevNo = 0  # represents the ongoing sum if the previousHouse was not robbed
        for entry in numsNew:
            temp = prevNo
            prevNo = max(prevYes, prevNo) 
            prevYes = temp + entry
        return max(prevYes, prevNo)
    
    def rob(self, nums):
        if len(nums) == 1:
            return nums[0] 
        else:
            return max(self.robHelper(nums[1:]), self.robHelper(nums[:-1]))
```

The key insight is to find the maximum after excluding the first home and then computing the maximum excluding the last home.

With the two maximums computed, we need to compute the maximum between the two.