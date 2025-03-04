---
title: 2154 Keep Multiplying Found Values by Two
summary: 2154 Keep Multiplying Found Values by Two LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2154 Keep Multiplying Found Values by Two LeetCode Solution Explained in all languages", "2154 Keep Multiplying Found Values by Two", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2154 Keep Multiplying Found Values by Two - Solution Explained/problem-solving.webp
    alt: 2154 Keep Multiplying Found Values by Two
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2154. Keep Multiplying Found Values by Two](https://leetcode.com/problems/keep-multiplying-found-values-by-two)


## Description

<p>You are given an array of integers <code>nums</code>. You are also given an integer <code>original</code> which is the first number that needs to be searched for in <code>nums</code>.</p>

<p>You then do the following steps:</p>

<ol>
	<li>If <code>original</code> is found in <code>nums</code>, <strong>multiply</strong> it by two (i.e., set <code>original = 2 * original</code>).</li>
	<li>Otherwise, <strong>stop</strong> the process.</li>
	<li><strong>Repeat</strong> this process with the new number as long as you keep finding the number.</li>
</ol>

<p>Return <em>the <strong>final</strong> value of </em><code>original</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,3,6,1,12], original = 3
<strong>Output:</strong> 24
<strong>Explanation:</strong> 
- 3 is found in nums. 3 is multiplied by 2 to obtain 6.
- 6 is found in nums. 6 is multiplied by 2 to obtain 12.
- 12 is found in nums. 12 is multiplied by 2 to obtain 24.
- 24 is not found in nums. Thus, 24 is returned.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,7,9], original = 4
<strong>Output:</strong> 4
<strong>Explanation:</strong>
- 4 is not found in nums. Thus, 4 is returned.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i], original &lt;= 1000</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findFinalValue(self, nums: List[int], original: int) -> int:
        s = set(nums)
        while original in s:
            original <<= 1
        return original
```

```java
class Solution {

    public int findFinalValue(int[] nums, int original) {
        Set<Integer> s = new HashSet<>();
        for (int num : nums) {
            s.add(num);
        }
        while (s.contains(original)) {
            original <<= 1;
        }
        return original;
    }
}
```

```cpp
class Solution {
public:
    int findFinalValue(vector<int>& nums, int original) {
        unordered_set<int> s;
        for (int num : nums) s.insert(num);
        while (s.count(original)) original <<= 1;
        return original;
    }
};
```

```go
func findFinalValue(nums []int, original int) int {
	s := make(map[int]bool)
	for _, num := range nums {
		s[num] = true
	}
	for s[original] {
		original <<= 1
	}
	return original
}
```

```ts
function findFinalValue(nums: number[], original: number): number {
    let set: Set<number> = new Set(nums);
    while (set.has(original)) {
        original *= 2;
    }
    return original;
}
```

<!-- tabs:end -->

<!-- end -->
