---
title: 0668 Kth Smallest Number in Multiplication Table
summary: 0668 Kth Smallest Number in Multiplication Table LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0668 Kth Smallest Number in Multiplication Table LeetCode Solution Explained in all languages", "0668 Kth Smallest Number in Multiplication Table", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0668 Kth Smallest Number in Multiplication Table - Solution Explained/problem-solving.webp
    alt: 0668 Kth Smallest Number in Multiplication Table
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [668. Kth Smallest Number in Multiplication Table](https://leetcode.com/problems/kth-smallest-number-in-multiplication-table)


## Description

<p>Nearly everyone has used the <a href="https://en.wikipedia.org/wiki/Multiplication_table" target="_blank">Multiplication Table</a>. The multiplication table of size <code>m x n</code> is an integer matrix <code>mat</code> where <code>mat[i][j] == i * j</code> (<strong>1-indexed</strong>).</p>

<p>Given three integers <code>m</code>, <code>n</code>, and <code>k</code>, return <em>the </em><code>k<sup>th</sup></code><em> smallest element in the </em><code>m x n</code><em> multiplication table</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0668.Kth%20Smallest%20Number%20in%20Multiplication%20Table/images/multtable1-grid.jpg" style="width: 500px; height: 254px;" />
<pre>
<strong>Input:</strong> m = 3, n = 3, k = 5
<strong>Output:</strong> 3
<strong>Explanation:</strong> The 5<sup>th</sup> smallest number is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0668.Kth%20Smallest%20Number%20in%20Multiplication%20Table/images/multtable2-grid.jpg" style="width: 493px; height: 293px;" />
<pre>
<strong>Input:</strong> m = 2, n = 3, k = 6
<strong>Output:</strong> 6
<strong>Explanation:</strong> The 6<sup>th</sup> smallest number is 6.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= m, n &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= m * n</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findKthNumber(self, m: int, n: int, k: int) -> int:
        left, right = 1, m * n
        while left < right:
            mid = (left + right) >> 1
            cnt = 0
            for i in range(1, m + 1):
                cnt += min(mid // i, n)
            if cnt >= k:
                right = mid
            else:
                left = mid + 1
        return left
```

```java
class Solution {
    public int findKthNumber(int m, int n, int k) {
        int left = 1, right = m * n;
        while (left < right) {
            int mid = (left + right) >>> 1;
            int cnt = 0;
            for (int i = 1; i <= m; ++i) {
                cnt += Math.min(mid / i, n);
            }
            if (cnt >= k) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

```cpp
class Solution {
public:
    int findKthNumber(int m, int n, int k) {
        int left = 1, right = m * n;
        while (left < right) {
            int mid = (left + right) >> 1;
            int cnt = 0;
            for (int i = 1; i <= m; ++i) cnt += min(mid / i, n);
            if (cnt >= k)
                right = mid;
            else
                left = mid + 1;
        }
        return left;
    }
};
```

```go
func findKthNumber(m int, n int, k int) int {
	left, right := 1, m*n
	for left < right {
		mid := (left + right) >> 1
		cnt := 0
		for i := 1; i <= m; i++ {
			cnt += min(mid/i, n)
		}
		if cnt >= k {
			right = mid
		} else {
			left = mid + 1
		}
	}
	return left
}
```

<!-- tabs:end -->

<!-- end -->
