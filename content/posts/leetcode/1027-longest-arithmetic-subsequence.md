---
title: 1027 Longest Arithmetic Subsequence
summary: 1027 Longest Arithmetic Subsequence LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1027 Longest Arithmetic Subsequence LeetCode Solution Explained in all languages", "1027 Longest Arithmetic Subsequence", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1027 Longest Arithmetic Subsequence - Solution Explained/problem-solving.webp
    alt: 1027 Longest Arithmetic Subsequence
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1027. Longest Arithmetic Subsequence](https://leetcode.com/problems/longest-arithmetic-subsequence)


## Description

<p>Given an array <code>nums</code> of integers, return <em>the length of the longest arithmetic subsequence in</em> <code>nums</code>.</p>

<p><strong>Note</strong> that:</p>

<ul>
	<li>A <strong>subsequence</strong> is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.</li>
	<li>A sequence <code>seq</code> is arithmetic if <code>seq[i + 1] - seq[i]</code> are all the same value (for <code>0 &lt;= i &lt; seq.length - 1</code>).</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,6,9,12]
<strong>Output:</strong> 4
<strong>Explanation: </strong> The whole array is an arithmetic sequence with steps of length = 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [9,4,7,2,10]
<strong>Output:</strong> 3
<strong>Explanation: </strong> The longest arithmetic subsequence is [4,7,10].
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [20,1,15,3,10,5,8]
<strong>Output:</strong> 4
<strong>Explanation: </strong> The longest arithmetic subsequence is [20,15,10,5].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 500</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def longestArithSeqLength(self, nums: List[int]) -> int:
        n = len(nums)
        f = [[1] * 1001 for _ in range(n)]
        ans = 0
        for i in range(1, n):
            for k in range(i):
                j = nums[i] - nums[k] + 500
                f[i][j] = max(f[i][j], f[k][j] + 1)
                ans = max(ans, f[i][j])
        return ans
```

```java
class Solution {
    public int longestArithSeqLength(int[] nums) {
        int n = nums.length;
        int ans = 0;
        int[][] f = new int[n][1001];
        for (int i = 1; i < n; ++i) {
            for (int k = 0; k < i; ++k) {
                int j = nums[i] - nums[k] + 500;
                f[i][j] = Math.max(f[i][j], f[k][j] + 1);
                ans = Math.max(ans, f[i][j]);
            }
        }
        return ans + 1;
    }
}
```

```cpp
class Solution {
public:
    int longestArithSeqLength(vector<int>& nums) {
        int n = nums.size();
        int f[n][1001];
        memset(f, 0, sizeof(f));
        int ans = 0;
        for (int i = 1; i < n; ++i) {
            for (int k = 0; k < i; ++k) {
                int j = nums[i] - nums[k] + 500;
                f[i][j] = max(f[i][j], f[k][j] + 1);
                ans = max(ans, f[i][j]);
            }
        }
        return ans + 1;
    }
};
```

```go
func longestArithSeqLength(nums []int) int {
	n := len(nums)
	f := make([][]int, n)
	for i := range f {
		f[i] = make([]int, 1001)
	}
	ans := 0
	for i := 1; i < n; i++ {
		for k := 0; k < i; k++ {
			j := nums[i] - nums[k] + 500
			f[i][j] = max(f[i][j], f[k][j]+1)
			ans = max(ans, f[i][j])
		}
	}
	return ans + 1
}
```

```ts
function longestArithSeqLength(nums: number[]): number {
    const n = nums.length;
    let ans = 0;
    const f: number[][] = Array.from({ length: n }, () => new Array(1001).fill(0));
    for (let i = 1; i < n; ++i) {
        for (let k = 0; k < i; ++k) {
            const j = nums[i] - nums[k] + 500;
            f[i][j] = Math.max(f[i][j], f[k][j] + 1);
            ans = Math.max(ans, f[i][j]);
        }
    }
    return ans + 1;
}
```

<!-- tabs:end -->

<!-- end -->
