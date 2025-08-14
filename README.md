# dsa-preparation
An ongoing repository with resources I used to prepare for coding assessments.

## Resources
[Leetcode patterns](https://seanprashad.com/leetcode-patterns)  
[14 week free blog](https://veedaily19.substack.com/p/master-dsa-in-14-weeks?open=false#§week-two-pointers-and-fast-and-slow-pointers)  
[Algomaster](https://algomaster.io/practice/dsa-patterns)  
[Algomaster's other account](https://youtu.be/DjYZk8nrXVY?si=c-yEpxZ9WHwaxSq7)  
[Neetcode](https://neetcode.io/practice)  
[Roadmap overview](https://roadmap.sh/datastructures-and-algorithms)  
[Useful tips](https://aman.ai/code/)

## Patterns
Found that Algomaster is the best YT channel for tutorials on concepts. Do one pattern per day.  
### Day 1: Two pointers
[YT: Two Pointers concept](https://www.youtube.com/watch?v=QzZ7nmouLTI)

#### Types of pointers
1. Converging pointers - use case: palindromes/reverse
2. Parallel pointers - use case: sliding window
3. Trigger based pointers - use case: linked lists (e.g. obtaining the fourth node from the back)

#### When to use?
Questions that contain arrays, strings and linked lists.  
Keywords to look out for: arrays that are SORTED, questions that ask to **return indices/pairs**.
#### Questions to practice:

EASY
- Contains duplicate
- Two Sum variants
- Move Zeros
- Valid Anagram
- Isomorphic Strings
- Remove duplicates
- Merge Sorted Array 

MEDIUM
- 3Sum
- 3Sum closest
- Two Sum II
- Container with most water

HARD
- Trapping Rain Water

### Day 2: Sliding window
[YT: Sliding Window concept](https://www.youtube.com/watch?v=y2d0VHdvfdc&t=81s)  
[Full list of problems with complexity analysis](https://aman.ai/code/sliding-window)
#### Fixed window code template
```python
window_sum = 0
max_result = 0 # or other computation

# Set up the initial window (by summing values for that window length, k)
for i in range(k):
  window_sum += arr[i]

max_result = window_sum

for i in range(k, len(arr)):
  window_sum += arr[i] - arr[i-k]
  max_result = max(max_result, window_sum)  # or other computation

return max_result # or other computation
```
#### Variable window code template
```python
initialise window_state (sum, count, frequency map, etc.)
left = 0
min_or_max_result = 0

for right in range(len(arr)):
  # Expand the window
  update window_state to include arr[right]

  # Shrink window until valid
  while window_state violates the condition:
    update min_or_max_result (if needed)
    update window_state to exclude arr[left] # Shrink the window
    mleft += 1

return min_or_max result
```
#### Practice: Fixed size
EASY
- [Maximum Average Subarray I (Fixed window size)](https://leetcode.com/problems/maximum-average-subarray-i)

MEDIUM
- [Find ALl Anagrams in a String](leetcode.com/problems/find-all-anagrams-in-a-string)
- [Permutation in String](https://leetcode.com/problems/permutation-in-string)
- [Maximum Sum of Distinct Subarrays With Length K]

HARD
- [Substring with Concatenation of All Words]

#### Practice: Dynamic size
MEDIUM
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)
- [Longest Repeating character replacement]
- [fruits into baskets (at most K distinct), min subarray length ≥ target]
- [Minimum Size Subarray Sum]
- [Max Consecutive Ones III]

HARD
- Minimum Window Substrung
