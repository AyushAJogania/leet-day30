# leet-day30

# Valid Partition of Array

This C++ solution aims to determine if a given array can be partitioned into valid subarrays based on specific conditions. The problem statement asks to check if the array can be divided into subarrays, satisfying these conditions:

1. The subarray consists of exactly 2 equal elements.
2. The subarray consists of exactly 3 equal elements.
3. The subarray consists of exactly 3 consecutive increasing elements.

The provided solution uses dynamic programming with memoization to efficiently solve the problem by avoiding redundant computations. Here's a detailed explanation of the code:

### Solution Description

1. The class `Solution` contains two functions:
   - `c`: A recursive helper function that checks whether a valid partition can be achieved starting from a particular index.
   - `validPartition`: The main function that initializes the dynamic programming array and triggers the recursive process.

2. The `c` function takes three parameters:
   - `v`: A reference to the input array.
   - `dp`: A memoization array to store already calculated results.
   - `i`: The current index being considered in the recursion.

3. Inside the `c` function:
   - The base case checks if the index `i` has reached the end of the array. If so, it returns `true` since a valid partition has been found.
   - The next base case checks if the result for index `i` is already calculated and stored in the DP array. If yes, it returns the cached result.

4. The code then checks three conditions:
   - If the current element and the next element are equal, it means a subarray of exactly 2 equal elements is possible. The function recursively calls itself with `i + 2`.
   - If the current element is equal to the next two elements, it means a subarray of exactly 3 equal elements is possible. The function recursively calls itself with `i + 3`.
   - If the current element and the next two elements form a consecutive sequence, it means a subarray of exactly 3 consecutive increasing elements is possible. The function recursively calls itself with `i + 3`.

5. If none of the above conditions are met, the DP array at index `i` is set to `false`, indicating that a valid partition is not possible starting from that index. The function returns `false`.

6. The `validPartition` function initializes the DP array and triggers the recursive process by calling the `c` function with index `0`.

### Complexity Analysis

- The time complexity of this solution heavily depends on the number of recursive calls made. It can be upper-bounded by O(N), where N is the number of elements in the array.
- The space complexity is O(N) due to the memoization array `dp`.

This solution provides an efficient way to determine if a given array can be partitioned according to the specified conditions, utilizing dynamic programming to avoid redundant calculations.
