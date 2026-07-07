"""

#1 TwoSum:

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        index1 = 0; index2 = 0
        for i in range(len(nums)):
            numc1 = nums[index1]
            for eachnum in nums:
                if numc1 + eachnum == target and index1 != index2:
                    return [index1, index2]
                index2 += 1
            index1 += 1
            index2 = 0

solution = Solution()
print(solution.twoSum([2, 7, 11, 15], 9))
print(solution.twoSum([3, 2, 4], 6))
print(solution.twoSum([3, 3], 6))
"""

"""
#2 ContainsDuplicate:

from ast import List

class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        duplicates = len(set(nums)) != len(nums)
        return duplicates

solution = Solution()
print(solution.containsDuplicate([1, 2, 3, 1]))
print(solution.containsDuplicate([1, 2, 3, 4]))
"""

"""
#3 ValidAnagram:

from ast import List

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        freq = {}
        for char in s:
            if char in freq:
                freq[char] += 1
            else:
                freq[char] = 1
        for char in t:
            if char in freq:
                freq[char] -= 1
            else:
                freq[char] = -1
        for value in freq.values():
            if value != 0:
                return False
        return True
                
    
    def isAnagram2(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
    
solution = Solution()
print(solution.isAnagram("anagram", "nagaram"))
print(solution.isAnagram("rat", "car"))
print(solution.isAnagram2("anagram", "nagaram"))
print(solution.isAnagram2("rat", "car"))
"""

"""
#4 GroupAnagrams:

from ast import List

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        anagram_groups = {}
        for word in strs:
            sorted_word = ''.join(sorted(word))
            if sorted_word in anagram_groups:
                anagram_groups[sorted_word].append(word)
            else:
                anagram_groups[sorted_word] = [word]
        return list(anagram_groups.values())
    
solution = Solution()
print(solution.groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))
print(solution.groupAnagrams([""]))
print(solution.groupAnagrams(["a"]))
"""
"""
#5 topkfrequent:
from typing import List


class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        element_freq = {}
        for num in nums:
            if num in element_freq:
                element_freq[num] += 1
            else:
                element_freq[num] = 1
        sorted_freq = sorted(element_freq.items(), key=lambda x: x[1], reverse=True)
        top_k_elements = [item[0] for item in sorted_freq[:k]]
        return top_k_elements
    
solution = Solution()
print(solution.topKFrequent([1, 1, 1, 2, 2, 3], 2))
print(solution.topKFrequent([1], 1))
"""