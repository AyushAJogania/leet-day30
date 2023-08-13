# leet-day30

# Reverse Integer

Given a signed 32-bit integer `x`, you need to reverse its digits. If reversing `x` causes the value to go outside the signed 32-bit integer range \([-2^{31}, 2^{31} - 1]\), then return 0.

## Problem Description

You are given an integer `x`, and you need to reverse its digits while taking care of the overflow condition.

**Example 1:**
```
Input: x = 123
Output: 321
```

**Example 2:**
```
Input: x = -123
Output: -321
```

**Example 3:**
```
Input: x = 120
Output: 21
```

## Approach and Optimization

To solve this problem, we can iterate through the digits of the input integer `x` and build the reversed integer by repeatedly adding digits. However, to ensure that the reversed integer does not cause an overflow, we need to check for overflow conditions.

The maximum and minimum values that a 32-bit signed integer can hold are `INT_MAX` and `INT_MIN`, respectively. We will use these values to check for overflow.

The optimized approach involves checking for overflow before updating the reversed result. We do this by comparing the current reversed result with `INT_MAX / 10` and `INT_MIN / 10` to anticipate whether the next digit will cause an overflow or not.

Additionally, since the last digit of the reversed integer will affect overflow conditions, we compare the last digit (8 for positive and -8 for negative) to the upcoming digit to ensure it's within bounds.

## Algorithm

1. Initialize a variable `reversed` to store the reversed integer.
2. While `x` is not zero:
   - Get the last digit of `x` using `x % 10`.
   - Check for overflow using the following conditions:
     - If `reversed > INT_MAX / 10`, or if `reversed` is equal to `INT_MAX / 10` and the current digit is greater than 7, return 0 (overflow).
     - If `reversed < INT_MIN / 10`, or if `reversed` is equal to `INT_MIN / 10` and the current digit is less than -8, return 0 (overflow).
   - Update `x` by performing integer division `x /= 10`.
   - Update the `reversed` result by multiplying it by 10 and adding the current digit.
3. Return the `reversed` result.

## Complexity Analysis

- Time Complexity: O(log(x)) where x is the input integer.
- Space Complexity: O(1), as we are using constant extra space.

## Summary

The "Reverse Integer" problem involves reversing the digits of an integer while taking care of overflow conditions. The optimized approach checks for overflow before updating the reversed result by comparing it with `INT_MAX / 10` and `INT_MIN / 10`. This ensures that the reversed integer is within the range of a 32-bit signed integer. The algorithm has a time complexity of O(log(x)) and a space complexity of O(1).
