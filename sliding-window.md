"""
# 21 best time to buy and sell stock || prices = [3, 10, 1, 4]

from typing import *

class Solution():
    def maxProfit(self, prices: List[int]) -> int:
        left = 0
        right = 1
        max_profit = 0

        while right < len(prices):
            profit = prices[right] - prices[left]

            if profit > 0:
                max_profit = max(max_profit, profit)

            else:
                left = right

            right += 1

        return max_profit
    

solution = Solution()

print(solution.maxProfit([3,10,1,4]))
print(solution.maxProfit([7,1,5,3,6,4]))
print(solution.maxProfit([7,6,4,3,1]))
"""

"""
# 22 longest substring without repeating characters

class Solution():
    def lengthOfLongestSubstring(self, s: str) -> int:
        left = 0
        seen = set()
        max_length = 0

        for right in range(len(s)):
            while s[right] in seen:
                seen.remove(s[left])
                left += 1

            seen.add(s[right])
            max_length = max(max_length, right - left + 1)

        return max_length

solution = Solution()

print(solution.lengthOfLongestSubstring("abcabcbb"))
print(solution.lengthOfLongestSubstring("bbbbb"))
print(solution.lengthOfLongestSubstring("pwwkew"))
"""

"""
# 23 minimum window substring

from typing import *

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if len(t) > len(s):
            return ""
        
        need = Counter(t)
        window = {}

        have = 0
        need_count = len(need)
        
        best = ""
        best_len = float("inf")
        left = 0

        for right in range(len(s)):
            char = s[right]

            window[char] = window.get(char, 0) + 1

            if char in need and window[char] == need[char]:
                have += 1

            while have == need_count:
                current_len = right - left + 1

                if current_len < best_len:
                    best_len = current_len
                    best = s[left : right + 1]

                left_char = s[left]
                window[left_char] -= 1

                if left_char in need and window[left_char] < need[left_char]:
                    have -= 1

                left += 1

        return best
    

solution = Solution()

print(solution.minWindow(s = "ADOBECODEBANC", t = "ABC"))
print(solution.minWindow(s = "a", t = "a"))
print(solution.minWindow(s = "a", t = "aa"))
"""

"""
# 24 longest repeating character replacement

from typing import *

class Solution():
    def characterReplacement(self, s: str, k: int) -> int:
        key_value = {}

        left = 0
        max_freq = 0
        max_length = 0

        for right in range(len(s)):
            char = s[right]
            key_value[char] = key_value.get(char, 0) + 1

            max_freq = max(max_freq, key_value[char])
            window_length = right - left + 1

            changes_needed = window_length - max_freq

            if changes_needed > k:
                key_value[s[left]] -= 1
                left += 1

            max_length = max(max_length, right - left + 1)

        return max_length
    

solution = Solution()

print(solution.characterReplacement(s = "ABAB", k = 2))
print(solution.characterReplacement(s = "AABABBA", k = 1))
"""

"""
# 25 sliding window maximum

# only passed 33 test cases out of 58
from typing import *

class Solution:
    def maxslidingWindow(self, nums: List[int], k: int) -> List[int]:
        list_max = []
        current_window = []

        for right in range(len(nums)):

            if len(current_window) < k:
                current_window.append(nums[right])

            if len(current_window) == k:
                list_max.append(max(current_window))
                current_window.pop(0)

        return list_max

from collections import *

class Solution:
    def maxslidingWindow(self, nums: List[int], k: int) -> List[int]:
        q = deque()
        result = []

        for right in range(len(nums)):

            while q and q[0] < nums[right]:
                q.pop()

            q.append(right)

            if q[0] < right - k:
                q.popleft()

            if right >= k - 1:
                result.append(nums[q[0]])

        return result
    
solution = Solution()

print(solution.maxslidingWindow([1,3,-1,-3,5,3,6,7], k = 3))
print(solution.maxslidingWindow([1], k = 1))
"""