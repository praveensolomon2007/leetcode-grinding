"""
# 11 valid parantheses

class Solution:
    def isValid(self, s: str) -> bool:
        if (len(s.strip()) % 2) == 0:

            pairs = {
                ")" : "(",
                "]" : "[",
                "}" : "{"
            }
            stack = []
            for char in s:
                if char in ("(", "[", "{"):
                    stack.append(char)
                else:
                    if not stack:
                        return False
                    
                    if not stack[-1] == pairs[char]:
                        return False
                    
                    stack.pop()
            
            if not stack:
                return True
            else:
                return False

        else:
            return False

solution = Solution()
print(solution.isValid("))"))
print(solution.isValid("()[]{}"))
print(solution.isValid("(]"))
print(solution.isValid("([])"))
print(solution.isValid("([)]"))
"""

"""
# 12 min stack

class MinStack:
    
    def __init__(self):
        self.stack = []
        self.minstack = []

    def push(self, val):
        self.stack.append(val)

        if not self.minstack:
            self.minstack.append(val)
        
        else:
            self.minstack.append(min(val, self.minstack[-1]))

    def pop(self):

        if self.stack:
            self.stack.pop()
            self.minstack.pop()

        else:
            raise IndexError("Stack is Empty!")
        
    def top(self):

        if self.stack:
            return self.stack[-1]
        
        else:
            raise IndexError("Stack is Empty!")
    
    def getMin(self):

        if self.stack:
            return self.minstack[-1]
        
        else:
            raise IndexError("Stack is Empty!")
        

minstack = MinStack()
minstack.push(-2)
minstack.push(0)
minstack.push(-3)
print(minstack.getMin())
minstack.pop()
print(minstack.top())
print(minstack.getMin())
"""




"""
# 13 daily temperatures

Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

 

Example 1:

Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
Example 2:

Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
Example 3:

Input: temperatures = [30,60,90]
Output: [1,1,0]

from typing import *

# brute force

class Solution:
    def dailyTemperatures1(self, temperatures: List[int]) -> List[int]:
        left = 0

        answer = []

        while left < len(temperatures):
            current_temp = temperatures[left]

            count = 0
            found = False
            
            i = left
            while i < len(temperatures) - 1:

                count += 1

                if current_temp < temperatures[i + 1]:
                    answer.append(count)
                    found = True
                    break

                else:
                    i += 1

            if not found:
                answer.append(0)

            left += 1


        return answer
    
    # stacks approach
    def dailyTemperatures2(self, temperatures: List[int]) -> List[int]:

        answer = [0] * len(temperatures)

        stack = []

        for i, temp in enumerate(temperatures):

            while stack and temp > stack[-1][0]:

                _, old_index = stack.pop()

                answer[old_index] = i - old_index

            stack.append((temp, i))

        return answer



solution = Solution()
# 1
print(solution.dailyTemperatures1([73,74,75,71,69,72,76,73]))
print(solution.dailyTemperatures1([30,40,50,60]))
print(solution.dailyTemperatures1([30,60,90]))
# 2
print(solution.dailyTemperatures2([73,74,75,71,69,72,76,73]))
print(solution.dailyTemperatures2([30,40,50,60]))
print(solution.dailyTemperatures2([30,60,90]))
            
"""

"""
# 14 generate parantheses
from typing import *

class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        # initializing empty string storage to append str as the recursing ends and to return this as the final output for the function generateParantheses
        answer = []

        def backtrack(current: str, open_count: int, close_count: int) -> None:

            if len(current) == 2 * n:
                answer.append(current)
                return
            
            if open_count < n:
                
                backtrack(
                    current + "(",
                    open_count + 1,
                    close_count
                )       

            if close_count < open_count:

                backtrack(
                    current + ")",
                    open_count,
                    close_count + 1
                )

        backtrack("", 0, 0)

        return answer
    
solution = Solution()

print(solution.generateParantheses(3))
print(solution.generateParantheses(1)) 
"""

"""
# 15 largest rectangle in hist

from typing import *

class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:

        stack = []

        max_area = 0

        for index, height in enumerate(heights):

            start_index = index

            while stack and stack[-1][1] > height:
                old_index, old_height = stack.pop()

                width = index - old_index
                area = old_height * width
                max_area = max(max_area, area)

                start_index = old_index

            stack.append((start_index, height))

        for start_index, height in stack:

            width = len(heights) - start_index
            area = height * width
            max_area = max(max_area, area)

        return max_area
    

solution = Solution()

print(solution.largestRectangleArea([2, 1, 5, 6, 2, 3]))
print(solution.largestRectangleArea([2,4]))
"""