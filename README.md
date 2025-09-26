------------------------------------------------------
Week 6: Memoization (Intro to DP)
------------------------------------------------------
Day 36: Fibonacci with memoization (LC #509)
Day 37: Climbing stairs optimized (LC #70, #746)
Day 38: Unique paths (LC #62, #63)
Day 39: Coin change (LC #322)
Day 40: Min cost path problems
Day 41: Review recursion + memoization
Day 42: Practice 4-5 DP problems (easy-medium)



"""
Day 36: Fibonacci with Memoization (LC #509)
Author: [Your Name]
Date: [Today's Date]

Problem Statement (LC #509):
The Fibonacci numbers are defined as:
F(0) = 0, F(1) = 1
F(n) = F(n-1) + F(n-2), for n > 1

Given n, calculate F(n).
"""

# ----------------------------------------------------
# Approach:
# ----------------------------------------------------
"""
Naive recursion → O(2^n) time due to repeated calculations.
Memoization (Top-Down DP) → store results in a dictionary
to avoid recomputation.

Steps:
1. Use recursion for formula F(n) = F(n-1) + F(n-2).
2. Store already computed results in memo dict.
3. Return directly if result exists in memo.

Time Complexity: O(n)
Space Complexity: O(n) (recursion + memo storage)
"""

def fib(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]


# ----------------------------------------------------
# Example Usage
# ----------------------------------------------------
if __name__ == "__main__":
    print("Fibonacci(0):", fib(0))   # Expected: 0
    print("Fibonacci(1):", fib(1))   # Expected: 1
    print("Fibonacci(10):", fib(10)) # Expected: 55
    print("Fibonacci(30):", fib(30)) # Expected: 832040


# ----------------------------------------------------
# Key Notes:
# ----------------------------------------------------
# - Memoization converts exponential recursion → linear time.
# - Same as Top-Down Dynamic Programming.
# - Space used for recursion stack + memo dictionary.
# ----------------------------------------------------


"""
Day 37: Climbing Stairs Optimized (LC #70, #746)
Author: [Your Name]
Date: [Today's Date]

Problems Covered:
1. LC #70 – Climbing Stairs
2. LC #746 – Min Cost Climbing Stairs
"""

# ----------------------------------------------------
# 1. LC #70 – Climbing Stairs
# ----------------------------------------------------
"""
Problem:
You are climbing a staircase. It takes n steps to reach the top.
Each time you can climb either 1 or 2 steps.
Return how many distinct ways you can climb to the top.

Approach:
- Same recurrence as Fibonacci: ways(n) = ways(n-1) + ways(n-2)
- Optimize DP to use O(1) space.
"""

def climbStairs(n):
    if n <= 2:
        return n
    prev1, prev2 = 1, 2
    for _ in range(3, n+1):
        prev1, prev2 = prev2, prev1 + prev2
    return prev2


# ----------------------------------------------------
# 2. LC #746 – Min Cost Climbing Stairs
# ----------------------------------------------------
"""
Problem:
You are given an integer array cost where cost[i] is the cost of i-th step.
Once you pay the cost, you can climb 1 or 2 steps.
Return the minimum cost to reach the top.

Example:
Input: cost = [10,15,20]
Output: 15
(Explanation: start at step 1 with cost 15, climb two steps to top)

Approach:
- DP: minCost(i) = cost[i] + min(minCost(i+1), minCost(i+2))
- Optimize to O(1) space using two variables.
"""

def minCostClimbingStairs(cost):
    n = len(cost)
    prev1, prev2 = 0, 0  # cost to reach top from i+1, i+2
    for i in range(n-1, -1, -1):
        curr = cost[i] + min(prev1, prev2)
        prev1, prev2 = curr, prev1
    return min(prev1, prev2)


# ----------------------------------------------------
# Example Usage
# ----------------------------------------------------
if __name__ == "__main__":
    # LC #70
    print("Climbing Stairs (n=5):", climbStairs(5))  # Expected: 8
    
    # LC #746
    cost1 = [10,15,20]
    print("Min Cost Climbing Stairs [10,15,20]:", minCostClimbingStairs(cost1))  # Expected: 15
    
    cost2 = [1,100,1,1,1,100,1,1,100,1]
    print("Min Cost Climbing Stairs [1,100,1,1,1,100,1,1,100,1]:", minCostClimbingStairs(cost2))  # Expected: 6


# ----------------------------------------------------
# Time & Space Complexity:
# ----------------------------------------------------
# Climb Stairs (#70): Time O(n), Space O(1)
# Min Cost Climbing Stairs (#746): Time O(n), Space O(1)
# ----------------------------------------------------
