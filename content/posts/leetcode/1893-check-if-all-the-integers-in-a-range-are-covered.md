---
title: 1893 Check if All the Integers in a Range Are Covered
summary: 1893 Check if All the Integers in a Range Are Covered LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1893 Check if All the Integers in a Range Are Covered LeetCode Solution Explained in all languages", "1893 Check if All the Integers in a Range Are Covered", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1893 Check if All the Integers in a Range Are Covered - Solution Explained/problem-solving.webp
    alt: 1893 Check if All the Integers in a Range Are Covered
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1893. Check if All the Integers in a Range Are Covered](https://leetcode.com/problems/check-if-all-the-integers-in-a-range-are-covered)


## Description

<p>You are given a 2D integer array <code>ranges</code> and two integers <code>left</code> and <code>right</code>. Each <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> represents an <strong>inclusive</strong> interval between <code>start<sub>i</sub></code> and <code>end<sub>i</sub></code>.</p>

<p>Return <code>true</code> <em>if each integer in the inclusive range</em> <code>[left, right]</code> <em>is covered by <strong>at least one</strong> interval in</em> <code>ranges</code>. Return <code>false</code> <em>otherwise</em>.</p>

<p>An integer <code>x</code> is covered by an interval <code>ranges[i] = [start<sub>i</sub>, end<sub>i</sub>]</code> if <code>start<sub>i</sub> &lt;= x &lt;= end<sub>i</sub></code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> ranges = [[1,2],[3,4],[5,6]], left = 2, right = 5
<strong>Output:</strong> true
<strong>Explanation:</strong> Every integer between 2 and 5 is covered:
- 2 is covered by the first range.
- 3 and 4 are covered by the second range.
- 5 is covered by the third range.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> ranges = [[1,10],[10,20]], left = 21, right = 21
<strong>Output:</strong> false
<strong>Explanation:</strong> 21 is not covered by any range.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= ranges.length &lt;= 50</code></li>
	<li><code>1 &lt;= start<sub>i</sub> &lt;= end<sub>i</sub> &lt;= 50</code></li>
	<li><code>1 &lt;= left &lt;= right &lt;= 50</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isCovered(self, ranges: List[List[int]], left: int, right: int) -> bool:
        diff = [0] * 52
        for l, r in ranges:
            diff[l] += 1
            diff[r + 1] -= 1
        cur = 0
        for i, x in enumerate(diff):
            cur += x
            if left <= i <= right and cur == 0:
                return False
        return True
```

```java
class Solution {
    public boolean isCovered(int[][] ranges, int left, int right) {
        int[] diff = new int[52];
        for (int[] range : ranges) {
            int l = range[0], r = range[1];
            ++diff[l];
            --diff[r + 1];
        }
        int cur = 0;
        for (int i = 0; i < diff.length; ++i) {
            cur += diff[i];
            if (i >= left && i <= right && cur == 0) {
                return false;
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool isCovered(vector<vector<int>>& ranges, int left, int right) {
        int diff[52]{};
        for (auto& range : ranges) {
            int l = range[0], r = range[1];
            ++diff[l];
            --diff[r + 1];
        }
        int cur = 0;
        for (int i = 0; i < 52; ++i) {
            cur += diff[i];
            if (i >= left && i <= right && cur <= 0) {
                return false;
            }
        }
        return true;
    }
};
```

```go
func isCovered(ranges [][]int, left int, right int) bool {
	diff := [52]int{}
	for _, rg := range ranges {
		l, r := rg[0], rg[1]
		diff[l]++
		diff[r+1]--
	}
	cur := 0
	for i, x := range diff {
		cur += x
		if i >= left && i <= right && cur <= 0 {
			return false
		}
	}
	return true
}
```

```ts
function isCovered(ranges: number[][], left: number, right: number): boolean {
    const diff = new Array(52).fill(0);
    for (const [l, r] of ranges) {
        ++diff[l];
        --diff[r + 1];
    }
    let cur = 0;
    for (let i = 0; i < 52; ++i) {
        cur += diff[i];
        if (i >= left && i <= right && cur <= 0) {
            return false;
        }
    }
    return true;
}
```

```js
/**
 * @param {number[][]} ranges
 * @param {number} left
 * @param {number} right
 * @return {boolean}
 */
var isCovered = function (ranges, left, right) {
    const diff = new Array(52).fill(0);
    for (const [l, r] of ranges) {
        ++diff[l];
        --diff[r + 1];
    }
    let cur = 0;
    for (let i = 0; i < 52; ++i) {
        cur += diff[i];
        if (i >= left && i <= right && cur <= 0) {
            return false;
        }
    }
    return true;
};
```

<!-- tabs:end -->

<!-- end -->
