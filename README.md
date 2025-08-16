# dsa-preparation
This is an ongoing repository with helpful resources to prepare for coding assessments.  
For every pattern, I have selected a set of LeetCode questions. Some of the medium questions are quite hard, so you’re not expected to finish them all in a single day. Feel free to complete as many as you’d like — the problems are arranged in a helpful order.

## Resources
[Leetcode patterns](https://seanprashad.com/leetcode-patterns)  
[Grind based on how much time you have](https://www.techinterviewhandbook.org/grind75/?weeks=26)  
[14 week plan - free blog](https://veedaily19.substack.com/p/master-dsa-in-14-weeks?open=false#§week-two-pointers-and-fast-and-slow-pointers)  
[Algomaster's dsa patterns](https://algomaster.io/practice/dsa-patterns)  
[Algomaster's other account](https://youtu.be/DjYZk8nrXVY?si=c-yEpxZ9WHwaxSq7)  
[Neetcode](https://neetcode.io/practice)  
[Roadmap overview](https://roadmap.sh/datastructures-and-algorithms)  
[Useful tips](https://aman.ai/code/)

## Patterns
I like how Algomaster's YT channel includes when to use each pattern, what the pattern is and questions you can complete on that pattern - their vids are mainly the concept vids attached.

### Day 1: Two pointers
[YT: Two Pointers concept](https://www.youtube.com/watch?v=QzZ7nmouLTI)

#### 1.1 Types of pointers
1. Converging pointers - use case: palindromes/reverse
2. Parallel pointers - use case: sliding window
3. Trigger based pointers - use case: linked lists (e.g. obtaining the fourth node from the back)

#### 1.2 When to use?
Questions that contain arrays, strings and linked lists.  
Keywords to look out for: arrays that are SORTED, questions that ask to **return indices/pairs**.
#### 1.3 Questions to practice:

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
[Full list of sliding window problems with complexity analysis](https://aman.ai/code/sliding-window)
#### 2.1 Fixed window code template
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
#### 2.2 Variable window code template
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
#### 2.3 Practice: Fixed size
EASY
- [Maximum Average Subarray I (Fixed window size)](https://leetcode.com/problems/maximum-average-subarray-i/description)

MEDIUM
- [Find ALl Anagrams in a String](leetcode.com/problems/find-all-anagrams-in-a-string/description)
- [Permutation in String](https://leetcode.com/problems/permutation-in-string/description)
- [Maximum Sum of Distinct Subarrays With Length K](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/description)

HARD
- [Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/description)

#### 2.4 Practice: Dynamic size
MEDIUM
- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)
- [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement)
- ([fruits into baskets (at most K distinct), min subarray length ≥ target]
- [Minimum Size Subarray Sum]
- [Max Consecutive Ones III]

HARD
- Minimum Window Substring)

### Day 3/4: Fast and slow pointers / Linked Lists
[Short overview](https://www.youtube.com/watch?v=b139yf7Ik-E&t=178s)  
[More detailed with exercises](https://www.youtube.com/watch?v=XWyXy2aNrXM)  

#### 3.1 Floyd's algorithm
[Floyd's algorithm - used in MEDIUM questions](https://www.youtube.com/watch?v=PvrxZaH_eZ4)    

Floyd's cycle detection algorithm: Distance from meeting node to start of cycle node = Distance from starting node to start of cycle node  
- Space complexity: O(n)
- Time complexity: O(1)

#### 3.2 Practice
EASY
- [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)
- [Happy Number](https://leetcode.com/problems/happy-number/)
- [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description)
- [Reverse Linked List (try iteratively and recursively)](https://leetcode.com/problems/reverse-linked-list/description)
- [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list)

MEDIUM
- [Find the Duplicate Number - Floyd's algorithm](https://leetcode.com/problems/find-the-duplicate-number/description)
- [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii)
- [Reorder List](https://leetcode.com/problems/reorder-list/description)
- [Add Two Numbers](https://leetcode.com/problems/add-two-numbers)
- [Circular Array Loop]

#### 3.3 Template code
Don't look until you have completed the practice questions above. No spoilers!

##### 3.3.1 Find the start of a linked list cycle
```python
slow, fast = head, head
while True:
    if fast == None or fast.next == None:
        return None # Return None if end of Linked List met
    slow = slow.next
    fast = fast.next.next
    if slow == fast:
        break # When two pointers meet, there is a cycle
    
# Find the start node of the cycle using Floyd's algorithm
while True:
    if head == slow:
        return head
    head = head.next
```
##### 3.3.2 Merge two Linked Lists together
```python
left, right = list1, list2
while right:
  temp1, temp2 = left.next, right.next
  left.next = right
  right.next = temp1

  left, right = temp1, temp2

return list1
```
