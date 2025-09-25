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
