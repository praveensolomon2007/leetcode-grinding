"""
# 16 binary search

from typing import *

class Solution:
    def search(self, nums: List[int], target: int) -> int:

        left = 0
        right = len(nums) - 1
        middle = 0


        while left <= right:
            middle = (left + right) // 2

            if target < nums[middle]:
                right = middle - 1

            elif target > nums[middle]:
                left = middle + 1

            else:
                return middle
            
        return -1
    

solution = Solution()

print(solution.search([-1,0,3,5,9,12], 9))
print(solution.search([-1,0,3,5,9,12], 2))
print(solution.search([1, 2], 2))
"""

"""
# 17 search in rotated sorted array

from typing import *

class Solution:
    def search(self, nums: List[int], target: int) -> int:

        left = 0
        right = len(nums) - 1
        middle = 0

        while left <= right:
            
            middle = (left + right) // 2

            if nums[middle] == target:
                return middle
            
            if nums[left] <= nums[middle]:

                if nums[left] <= target < nums[middle]:
                    right = middle - 1
                else:
                    left = middle + 1

            else:

                if nums[middle] < target <= nums[right]:
                    left = middle + 1
                else:
                    right = middle - 1


        return -1
    

solution = Solution()

print(solution.search([4,5,6,7,0,1,2], 0))
print(solution.search([4,5,6,7,0,1,2], 3))
print(solution.search([1], 0))
"""

"""
# 18 find minimum in roatated sorted array

from typing import *

class Solution():
    def findMin(self, nums: List[int]) -> int:

        left = 0
        right = len(nums) - 1
        middle = 0

        while left < right:

            middle = (left + right) // 2

            if nums[middle] > nums[right]:
                left = middle + 1

            else:
                right = middle

        return nums[left]
    
solution = Solution()

print(solution.findMin([3,4,5,1,2]))
print(solution.findMin([4,5,6,7,0,1,2]))
print(solution.findMin([5,6,7,0,1,2,4]))
print(solution.findMin([11,13,15,17]))
"""

"""
# 19 koko eating bananas

from typing import *

class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        
        left = 1
        right = max(piles)

        if len(piles) == h:
            return right

        while left < right:

            middle = (left + right) // 2

            total_hours = 0

            for pile in piles:

                hours_per_pile = (pile + middle - 1) // middle
                total_hours += hours_per_pile

            if total_hours > h:
                left = middle + 1

            else:
                right = middle

        return left

solution = Solution()

print(solution.minEatingSpeed([3,6,7,11], 8))
print(solution.minEatingSpeed([30,11,23,4,20], 5))
print(solution.minEatingSpeed([30,11,23,4,20], 6))
"""

"""
# 20 median of two sorted arrays

from typing import *

class Solution():
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:

        nums1 += nums2
        nums1 = sorted(nums1)
        if len(nums1) % 2 == 0:
            left = 0
            right = len(nums1) - 1
            middle = (left + right) // 2
            median = (nums1[middle] + nums1[middle + 1]) / 2
            return median
        else:
            left = 0
            right = len(nums1) - 1
            middle = (left + right) // 2
            median = nums1[middle]
            return median
        
solution = Solution()

print(solution.findMedianSortedArrays(nums1 = [1,3], nums2 = [2]))
print(solution.findMedianSortedArrays(nums1 = [1,2], nums2 = [3,4]))
"""