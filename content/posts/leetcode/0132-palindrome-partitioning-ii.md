---
title: 0132 Palindrome Partitioning II
summary: 0132 Palindrome Partitioning II LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0132 Palindrome Partitioning II LeetCode Solution Explained in all languages", "0132 Palindrome Partitioning II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0132 Palindrome Partitioning II - Solution Explained/problem-solving.webp
    alt: 0132 Palindrome Partitioning II
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [132. Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii)


## Description

<p>Given a string <code>s</code>, partition <code>s</code> such that every <span data-keyword="substring-nonempty">substring</span> of the partition is a <span data-keyword="palindrome-string">palindrome</span>.</p>

<p>Return <em>the <strong>minimum</strong> cuts needed for a palindrome partitioning of</em> <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aab&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> The palindrome partitioning [&quot;aa&quot;,&quot;b&quot;] could be produced using 1 cut.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a&quot;
<strong>Output:</strong> 0
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ab&quot;
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> consists of lowercase English letters only.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minCut(self, s: str) -> int:
        n = len(s)
        g = [[True] * n for _ in range(n)]
        for i in range(n - 1, -1, -1):
            for j in range(i + 1, n):
                g[i][j] = s[i] == s[j] and g[i + 1][j - 1]
        f = list(range(n))
        for i in range(1, n):
            for j in range(i + 1):
                if g[j][i]:
                    f[i] = min(f[i], 1 + f[j - 1] if j else 0)
        return f[-1]
```

```java
class Solution {
    public int minCut(String s) {
        int n = s.length();
        boolean[][] g = new boolean[n][n];
        for (var row : g) {
            Arrays.fill(row, true);
        }
        for (int i = n - 1; i >= 0; --i) {
            for (int j = i + 1; j < n; ++j) {
                g[i][j] = s.charAt(i) == s.charAt(j) && g[i + 1][j - 1];
            }
        }
        int[] f = new int[n];
        for (int i = 0; i < n; ++i) {
            f[i] = i;
        }
        for (int i = 1; i < n; ++i) {
            for (int j = 0; j <= i; ++j) {
                if (g[j][i]) {
                    f[i] = Math.min(f[i], j > 0 ? 1 + f[j - 1] : 0);
                }
            }
        }
        return f[n - 1];
    }
}
```

```cpp
class Solution {
public:
    int minCut(string s) {
        int n = s.size();
        bool g[n][n];
        memset(g, true, sizeof(g));
        for (int i = n - 1; ~i; --i) {
            for (int j = i + 1; j < n; ++j) {
                g[i][j] = s[i] == s[j] && g[i + 1][j - 1];
            }
        }
        int f[n];
        iota(f, f + n, 0);
        for (int i = 1; i < n; ++i) {
            for (int j = 0; j <= i; ++j) {
                if (g[j][i]) {
                    f[i] = min(f[i], j ? 1 + f[j - 1] : 0);
                }
            }
        }
        return f[n - 1];
    }
};
```

```go
func minCut(s string) int {
	n := len(s)
	g := make([][]bool, n)
	f := make([]int, n)
	for i := range g {
		g[i] = make([]bool, n)
		f[i] = i
		for j := range g[i] {
			g[i][j] = true
		}
	}
	for i := n - 1; i >= 0; i-- {
		for j := i + 1; j < n; j++ {
			g[i][j] = s[i] == s[j] && g[i+1][j-1]
		}
	}
	for i := 1; i < n; i++ {
		for j := 0; j <= i; j++ {
			if g[j][i] {
				if j == 0 {
					f[i] = 0
				} else {
					f[i] = min(f[i], f[j-1]+1)
				}
			}
		}
	}
	return f[n-1]
}
```

```ts
function minCut(s: string): number {
    const n = s.length;
    const g: boolean[][] = Array(n)
        .fill(0)
        .map(() => Array(n).fill(true));
    for (let i = n - 1; ~i; --i) {
        for (let j = i + 1; j < n; ++j) {
            g[i][j] = s[i] === s[j] && g[i + 1][j - 1];
        }
    }
    const f: number[] = Array(n)
        .fill(0)
        .map((_, i) => i);
    for (let i = 1; i < n; ++i) {
        for (let j = 0; j <= i; ++j) {
            if (g[j][i]) {
                f[i] = Math.min(f[i], j ? 1 + f[j - 1] : 0);
            }
        }
    }
    return f[n - 1];
}
```

```cs
public class Solution {
    public int MinCut(string s) {
        int n = s.Length;
        bool[,] g = new bool[n,n];
        int[] f = new int[n];
        for (int i = 0; i < n; ++i) {
            f[i] = i;
            for (int j = 0; j < n; ++j) {
                g[i,j] = true;
            }
        }
        for (int i = n - 1; i >= 0; --i) {
            for (int j = i + 1; j < n; ++j) {
                g[i,j] = s[i] == s[j] && g[i + 1,j - 1];
            }
        }
        for (int i = 1; i < n; ++i) {
            for (int j = 0; j <= i; ++j) {
                if (g[j,i]) {
                    f[i] = Math.Min(f[i], j > 0 ? 1 + f[j - 1] : 0);
                }
            }
        }
        return f[n - 1];
    }
}
```

<!-- tabs:end -->

<!-- end -->
