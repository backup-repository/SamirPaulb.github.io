---
title: 0397 Integer Replacement
summary: 0397 Integer Replacement LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0397 Integer Replacement LeetCode Solution Explained in all languages", "0397 Integer Replacement", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0397 Integer Replacement - Solution Explained/problem-solving.webp
    alt: 0397 Integer Replacement
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [397. Integer Replacement](https://leetcode.com/problems/integer-replacement)


## Description

<p>Given a positive integer <code>n</code>,&nbsp;you can apply one of the following&nbsp;operations:</p>

<ol>
	<li>If <code>n</code> is even, replace <code>n</code> with <code>n / 2</code>.</li>
	<li>If <code>n</code> is odd, replace <code>n</code> with either <code>n + 1</code> or <code>n - 1</code>.</li>
</ol>

<p>Return <em>the minimum number of operations needed for</em> <code>n</code> <em>to become</em> <code>1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 8
<strong>Output:</strong> 3
<strong>Explanation:</strong> 8 -&gt; 4 -&gt; 2 -&gt; 1
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> 4
<strong>Explanation: </strong>7 -&gt; 8 -&gt; 4 -&gt; 2 -&gt; 1
or 7 -&gt; 6 -&gt; 3 -&gt; 2 -&gt; 1
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 4
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def integerReplacement(self, n: int) -> int:
        ans = 0
        while n != 1:
            if (n & 1) == 0:
                n >>= 1
            elif n != 3 and (n & 3) == 3:
                n += 1
            else:
                n -= 1
            ans += 1
        return ans
```

```java
class Solution {
    public int integerReplacement(int n) {
        int ans = 0;
        while (n != 1) {
            if ((n & 1) == 0) {
                n >>>= 1;
            } else if (n != 3 && (n & 3) == 3) {
                ++n;
            } else {
                --n;
            }
            ++ans;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int integerReplacement(int N) {
        int ans = 0;
        long n = N;
        while (n != 1) {
            if ((n & 1) == 0)
                n >>= 1;
            else if (n != 3 && (n & 3) == 3)
                ++n;
            else
                --n;
            ++ans;
        }
        return ans;
    }
};
```

```go
func integerReplacement(n int) int {
	ans := 0
	for n != 1 {
		if (n & 1) == 0 {
			n >>= 1
		} else if n != 3 && (n&3) == 3 {
			n++
		} else {
			n--
		}
		ans++
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
