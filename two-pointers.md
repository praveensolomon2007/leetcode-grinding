"""
#6 valid palindrome
class Solution:
    def isPalindrome(self, s: str) -> bool:
        cleaned = ''.join(filter(str.isalnum, s)).lower()
        return cleaned == cleaned[::-1]

solution = Solution()
print(solution.isPalindrome("A man, a plan, a canal: Panama"))
print(solution.isPalindrome ("race a car"))
print(solution.isPalindrome (" "))
"""

"""
#7 3sum
# O(n^3) time complexity, O(n) space complexity
class Solution:
    def threeSum(self, nums: list[int]) -> list[list[int]]:
        no_duplicates = set()
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                for k in range(j + 1, len(nums)):
                    if nums[i] + nums[j] + nums[k] == 0:
                        a = sorted([nums[i], nums[j], nums[k]])
                        no_duplicates.add(tuple(a))
        return [list(triplet) for triplet in no_duplicates]

solution = Solution()
print(solution.threeSum([-1, 0, 1, 2, -1, -4]))
print(solution.threeSum([0, 1, 1]))
print(solution.threeSum([0, 0, 0]))
print(solution.threeSum([-2, 0, 1, 1, 2]))

# O(n^2) time complexity, O(n) space complexity
class Solution:
    def threeSum(self, nums):

        nums.sort()

        result = []

        for i in range(len(nums) - 2):

            if i > 0 and nums[i] == nums[i - 1]:
                continue

            left = i + 1
            right = len(nums) - 1

            while left < right:

                total = nums[i] + nums[left] + nums[right]

                if total < 0:
                    left += 1

                elif total > 0:
                    right -= 1

                else:

                    result.append([
                        nums[i],
                        nums[left],
                        nums[right]
                    ])

                    left += 1
                    right -= 1

                    while left < right and nums[left] == nums[left - 1]:
                        left += 1

                    while left < right and nums[right] == nums[right + 1]:
                        right -= 1

        return result
"""
"""
# 8 container with most water

class Solution:
    def maxArea(self, height: List[int]) -> int:
        left_index = 0
        right_index = len(height) - 1
        max_area = 0

        while left_index < right_index:
            w = right_index - left_index #width of the container, distance between the current two pillars
            h = min(height[left_index], height[right_index]) #max height the container can have, minimum height that is the smallest of the current two pillars
            current_area = h * w

            max_area = max(current_area, max_area)

            if height[left_index] < height[right_index]:
                left_index += 1
            else:
                right_index -= 1
        
        return max_area
    
solution = Solution()
print(solution.maxArea([1,8,6,2,5,4,8,3,7]))
print(solution.maxArea([1,1]))
"""

"""
# 9 trapping rain water

class Solution:
    def trap(self, height: List[int]) -> int:

        left_index = 0
        right_index = len(height) - 1

        left_max = 0
        right_max = 0

        total_trapped_water = 0

        while left_index < right_index:

            if height[left_index] < height[right_index]:

                if height[left_index] >= left_max:
                    left_max = height[left_index]
                else:
                    total_trapped_water += left_max - height[left_index]

                left_index += 1

            else:

                if height[right_index] >= right_max:
                    right_max = height[right_index]
                else:
                    total_trapped_water += right_max - height[right_index]

                right_index -= 1

        return total_trapped_water
    
solution = Solution()

print(solution.trap([4, 2, 0, 3, 2, 5]))
print(solution.trap([5, 2, 0, 3, 2, 4]))
print(solution.trap([0,1,0,2,1,0,1,3,2,1,2,1]))
"""

"""
# 10 two sum II - Input Array Is Sorted

class Solution:
    def twoSum(Self, numbers: List[int], target: int) -> List[int]:

        left = 0
        right = len(numbers) - 1

        while left < right:
            sum = numbers[left] + numbers[right]
            if sum > target:
                right -= 1
            elif sum < target:
                left += 1
            else:
                return [left + 1, right + 1]
            
solution = Solution()
print(solution.twoSum([2,7,11,15], 9))
print(solution.twoSum([2,3,4], 6))
print(solution.twoSum([-1,0], -1))
"""