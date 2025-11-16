"""
CONTAINS DUPLICATE

Description:

Given an integer array nums, return true if any value appears at least twice in the array, 
and return false if every element is distinct.

The function must efficiently determine whether there are any duplicate values in the input array.


Output:

- Return `true` if at least one value appears more than once
- Return `false` if all elements are unique


Examples:

Example 1:
Input: nums = [1,2,3,1]
Output: true
Explanation: The element 1 occurs at the indices 0 and 3.

Example 2:
Input: nums = [1,2,3,4]
Output: false
Explanation: All elements are distinct.

Example 3:
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true


Constraints:

- 1 <= nums.length <= 105
- -109 <= nums[i] <= 109


Tips:

* Use a set to track elements you've already seen for O(1) lookup time
* The most efficient solution has O(n) time complexity and O(n) space complexity
* You can return early as soon as you find a duplicate to optimize performance
* Consider edge cases like single-element arrays (always return false)
* Alternative approaches include sorting first or using a hash map, but sets are clearest

Source:
https://leetcode.com/problems/contains-duplicate/description/
"""

# 0. SETUP

# TODO: Create the containsDuplicate() function that accepts nums array as parameter


# TODO: Initialize an empty set called 'seen' to track visited numbers




# 1. CORE LOGIC

# TODO: Set up a for loop to iterate through each number in nums


# TODO: Check if the current number already exists in the 'seen' set


# TODO: If number exists in 'seen', immediately return True (duplicate found)


# TODO: If number doesn't exist, add it to the 'seen' set




# 2. COMPLETION

# TODO: After loop completes without finding duplicates, return False




# 3. ALTERNATIVE APPROACH (SORTING)

# TODO: (Optional) Create alternative solution using sorted() function


# TODO: Sort the array and store in a variable


# TODO: Loop through sorted array comparing adjacent elements


# TODO: If any adjacent elements are equal, return True


# TODO: If no adjacent duplicates found, return False




# 4. ALTERNATIVE APPROACH (LENGTH COMPARISON)

# TODO: (Optional) Create one-line solution comparing len(nums) with len(set(nums))


# TODO: Return True if lengths differ, False if they're equal




# 5. TESTING

# TODO: Test with example 1: [1,2,3,1] - should return True


# TODO: Test with example 2: [1,2,3,4] - should return False


# TODO: Test with example 3: [1,1,1,3,3,4,3,2,4,2] - should return True


# TODO: Test edge case: single element [1] - should return False


# TODO: Test edge case: two identical elements [5,5] - should return True


# TODO: Test with large array near constraint limit (10^5 elements)


# TODO: Test with negative numbers [-1,-2,-3,-1] - should return True




# 6. OPTIMIZATION

# TODO: Verify solution handles maximum constraint values (-10^9 to 10^9)


# TODO: Compare time complexity of set approach vs sorting approach


# TODO: Measure actual performance with time.time() for large inputs

