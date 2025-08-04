# Leetcode-2460.-Apply-Operations-to-an-Array
# Description
You are given a 0-indexed array nums of size n consisting of non-negative integers.

You need to apply n - 1 operations to this array where, in the ith operation (0-indexed), you will apply the following on the ith element of nums:

If nums[i] == nums[i + 1], then multiply nums[i] by 2 and set nums[i + 1] to 0. Otherwise, you skip this operation.
After performing all the operations, shift all the 0's to the end of the array.

For example, the array [1,0,2,0,0,1] after shifting all its 0's to the end, is [1,2,1,0,0,0].
Return the resulting array.

Note that the operations are applied sequentially, not all at once.
# Solution
In the given problem we have been given an array nums which contains positive integers . We need to perform operations on the array in such a way that:

1. If the nums[i] and nums[i+1] are equal then multiplu nums[i] with 2 and make nums[i+1] as 0.
2. After performing this operation we need to push all the 0's at the end of the array and return the array.

Example :

Input: nums = [1,2,2,1,1,0]

Output: [1,4,2,0,0,0]

Explanation: We do the following operations:

- i = 0: nums[0] and nums[1] are not equal, so we skip this operation.
- 
- i = 1: nums[1] and nums[2] are equal, we multiply nums[1] by 2 and change nums[2] to 0. The array becomes [1,4,0,1,1,0].
- 
- i = 2: nums[2] and nums[3] are not equal, so we skip this operation.
- 
- i = 3: nums[3] and nums[4] are equal, we multiply nums[3] by 2 and change nums[4] to 0. The array becomes [1,4,0,2,0,0].
- 
- i = 4: nums[4] and nums[5] are equal, we multiply nums[4] by 2 and change nums[5] to 0. The array becomes [1,4,0,2,0,0].
- 
After that, we shift the 0's to the end, which gives the array [1,4,2,0,0,0].
# Algorithm
1. Loop through the nums array and check whether the nums[i] and nums[i+1] elements are the same .
2. If they are same then multiply nums[i] with 2 and make nums[i+1] as 0.
3. After all the operations are performed , then push all the 0's to the end of the array.
4. Return the array.
# Code 
class Solution:

    def applyOperations(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)-1):
            if nums[i]==nums[i+1]:
                nums[i]*=2
                nums[i+1]=0
        res=[]
        for num in nums:
            if num!=0:
                res.append(num)
        while len(res)<len(nums):
            res.append(0)
        return res
# Complexity
Time Complexity: O(n)

First loop (for i in range(len(nums)-1)):

Executes n-1 times → O(n)

Second loop (for num in nums):

Scans entire list → O(n)

Third loop (while len(res) < len(nums)):

At most n iterations → O(n)

Total: O(n + n + n) = O(n)

Space Complexity: O(n)

The extra list res may store up to n elements.

Total: O(n) = O(n)
