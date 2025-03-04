---
title: 1542 Find Longest Awesome Substring
summary: 1542 Find Longest Awesome Substring LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1542 Find Longest Awesome Substring LeetCode Solution Explained in all languages", "1542 Find Longest Awesome Substring", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1542 Find Longest Awesome Substring - Solution Explained/problem-solving.webp
    alt: 1542 Find Longest Awesome Substring
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1542. Find Longest Awesome Substring](https://leetcode.com/problems/find-longest-awesome-substring)


## Description

<p>You are given a string <code>s</code>. An <strong>awesome</strong> substring is a non-empty substring of <code>s</code> such that we can make any number of swaps in order to make it a palindrome.</p>

<p>Return <em>the length of the maximum length <strong>awesome substring</strong> of</em> <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;3242415&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> &quot;24241&quot; is the longest awesome substring, we can form the palindrome &quot;24142&quot; with some swaps.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;12345678&quot;
<strong>Output:</strong> 1
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;213123&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> &quot;213123&quot; is the longest awesome substring, we can form the palindrome &quot;231132&quot; with some swaps.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists only of digits.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def longestAwesome(self, s: str) -> int:
        st = 0
        d = {0: -1}
        ans = 1
        for i, c in enumerate(s):
            v = int(c)
            st ^= 1 << v
            if st in d:
                ans = max(ans, i - d[st])
            else:
                d[st] = i
            for v in range(10):
                if st ^ (1 << v) in d:
                    ans = max(ans, i - d[st ^ (1 << v)])
        return ans
```

```java
class Solution {
    public int longestAwesome(String s) {
        int[] d = new int[1024];
        int st = 0, ans = 1;
        Arrays.fill(d, -1);
        d[0] = 0;
        for (int i = 1; i <= s.length(); ++i) {
            int v = s.charAt(i - 1) - '0';
            st ^= 1 << v;
            if (d[st] >= 0) {
                ans = Math.max(ans, i - d[st]);
            } else {
                d[st] = i;
            }
            for (v = 0; v < 10; ++v) {
                if (d[st ^ (1 << v)] >= 0) {
                    ans = Math.max(ans, i - d[st ^ (1 << v)]);
                }
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int longestAwesome(string s) {
        vector<int> d(1024, -1);
        d[0] = 0;
        int st = 0, ans = 1;
        for (int i = 1; i <= s.size(); ++i) {
            int v = s[i - 1] - '0';
            st ^= 1 << v;
            if (~d[st]) {
                ans = max(ans, i - d[st]);
            } else {
                d[st] = i;
            }
            for (v = 0; v < 10; ++v) {
                if (~d[st ^ (1 << v)]) {
                    ans = max(ans, i - d[st ^ (1 << v)]);
                }
            }
        }
        return ans;
    }
};
```

```go
func longestAwesome(s string) int {
	d := [1024]int{}
	d[0] = 1
	st, ans := 0, 1
	for i, c := range s {
		i += 2
		st ^= 1 << (c - '0')
		if d[st] > 0 {
			ans = max(ans, i-d[st])
		} else {
			d[st] = i
		}
		for v := 0; v < 10; v++ {
			if d[st^(1<<v)] > 0 {
				ans = max(ans, i-d[st^(1<<v)])
			}
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
