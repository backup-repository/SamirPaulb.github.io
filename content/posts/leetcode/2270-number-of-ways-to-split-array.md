---
title: 2270 Number of Ways to Split Array
summary: 2270 Number of Ways to Split Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2270 Number of Ways to Split Array LeetCode Solution Explained in all languages", "2270 Number of Ways to Split Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2270 Number of Ways to Split Array - Solution Explained/problem-solving.webp
    alt: 2270 Number of Ways to Split Array
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2270. Number of Ways to Split Array](https://leetcode.com/problems/number-of-ways-to-split-array)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> of length <code>n</code>.</p>

<p><code>nums</code> contains a <strong>valid split</strong> at index <code>i</code> if the following are true:</p>

<ul>
	<li>The sum of the first <code>i + 1</code> elements is <strong>greater than or equal to</strong> the sum of the last <code>n - i - 1</code> elements.</li>
	<li>There is <strong>at least one</strong> element to the right of <code>i</code>. That is, <code>0 &lt;= i &lt; n - 1</code>.</li>
</ul>

<p>Return <em>the number of <strong>valid splits</strong> in</em> <code>nums</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [10,4,-8,7]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
There are three ways of splitting nums into two non-empty parts:
- Split nums at index 0. Then, the first part is [10], and its sum is 10. The second part is [4,-8,7], and its sum is 3. Since 10 &gt;= 3, i = 0 is a valid split.
- Split nums at index 1. Then, the first part is [10,4], and its sum is 14. The second part is [-8,7], and its sum is -1. Since 14 &gt;= -1, i = 1 is a valid split.
- Split nums at index 2. Then, the first part is [10,4,-8], and its sum is 6. The second part is [7], and its sum is 7. Since 6 &lt; 7, i = 2 is not a valid split.
Thus, the number of valid splits in nums is 2.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,1,0]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
There are two valid splits in nums:
- Split nums at index 1. Then, the first part is [2,3], and its sum is 5. The second part is [1,0], and its sum is 1. Since 5 &gt;= 1, i = 1 is a valid split. 
- Split nums at index 2. Then, the first part is [2,3,1], and its sum is 6. The second part is [0], and its sum is 0. Since 6 &gt;= 0, i = 2 is a valid split.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def waysToSplitArray(self, nums: List[int]) -> int:
        s = sum(nums)
        ans = t = 0
        for v in nums[:-1]:
            t += v
            if t >= s - t:
                ans += 1
        return ans
```

```java
class Solution {
    public int waysToSplitArray(int[] nums) {
        long s = 0;
        for (int v : nums) {
            s += v;
        }
        int ans = 0;
        long t = 0;
        for (int i = 0; i < nums.length - 1; ++i) {
            t += nums[i];
            if (t >= s - t) {
                ++ans;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int waysToSplitArray(vector<int>& nums) {
        long long s = accumulate(nums.begin(), nums.end(), 0ll);
        long long t = 0;
        int ans = 0;
        for (int i = 0; i < nums.size() - 1; ++i) {
            t += nums[i];
            ans += t >= s - t;
        }
        return ans;
    }
};
```

```go
func waysToSplitArray(nums []int) int {
	s := 0
	for _, v := range nums {
		s += v
	}
	ans, t := 0, 0
	for _, v := range nums[:len(nums)-1] {
		t += v
		if t >= s-t {
			ans++
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
