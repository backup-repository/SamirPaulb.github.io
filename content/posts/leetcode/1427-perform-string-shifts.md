---
title: 1427 Perform String Shifts
summary: 1427 Perform String Shifts LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1427 Perform String Shifts LeetCode Solution Explained in all languages", "1427 Perform String Shifts", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1427 Perform String Shifts - Solution Explained/problem-solving.webp
    alt: 1427 Perform String Shifts
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1427. Perform String Shifts](https://leetcode.com/problems/perform-string-shifts)


## Description

<p>You are given a string <code>s</code> containing lowercase English letters, and a matrix <code>shift</code>, where <code>shift[i] = [direction<sub>i</sub>, amount<sub>i</sub>]</code>:</p>

<ul>
	<li><code>direction<sub>i</sub></code> can be <code>0</code> (for left shift) or <code>1</code> (for right shift).</li>
	<li><code>amount<sub>i</sub></code> is the amount by which string <code>s</code> is to be shifted.</li>
	<li>A left shift by 1 means remove the first character of <code>s</code> and append it to the end.</li>
	<li>Similarly, a right shift by 1 means remove the last character of <code>s</code> and add it to the beginning.</li>
</ul>

<p>Return the final string after all operations.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abc&quot;, shift = [[0,1],[1,2]]
<strong>Output:</strong> &quot;cab&quot;
<strong>Explanation:</strong>&nbsp;
[0,1] means shift to left by 1. &quot;abc&quot; -&gt; &quot;bca&quot;
[1,2] means shift to right by 2. &quot;bca&quot; -&gt; &quot;cab&quot;</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcdefg&quot;, shift = [[1,1],[1,1],[0,2],[1,3]]
<strong>Output:</strong> &quot;efgabcd&quot;
<strong>Explanation:</strong>&nbsp; 
[1,1] means shift to right by 1. &quot;abcdefg&quot; -&gt; &quot;gabcdef&quot;
[1,1] means shift to right by 1. &quot;gabcdef&quot; -&gt; &quot;fgabcde&quot;
[0,2] means shift to left by 2. &quot;fgabcde&quot; -&gt; &quot;abcdefg&quot;
[1,3] means shift to right by 3. &quot;abcdefg&quot; -&gt; &quot;efgabcd&quot;</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> only contains lower case English letters.</li>
	<li><code>1 &lt;= shift.length &lt;= 100</code></li>
	<li><code>shift[i].length == 2</code></li>
	<li><code>direction<sub>i</sub></code><sub> </sub>is either <code>0</code> or <code>1</code>.</li>
	<li><code>0 &lt;= amount<sub>i</sub> &lt;= 100</code></li>
</ul>

## Solutions

### Solution 1: Simulation

We can denote the length of the string $s$ as $n$. Next, we traverse the array $shift$, accumulate to get the final offset $x$, then take $x$ modulo $n$, the final result is to move the first $n - x$ characters of $s$ to the end.

The time complexity is $O(n + m)$, where $n$ and $m$ are the lengths of the string $s$ and the array $shift$ respectively. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def stringShift(self, s: str, shift: List[List[int]]) -> str:
        x = sum((b if a else -b) for a, b in shift)
        x %= len(s)
        return s[-x:] + s[:-x]
```

```java
class Solution {
    public String stringShift(String s, int[][] shift) {
        int x = 0;
        for (var e : shift) {
            if (e[0] == 0) {
                e[1] *= -1;
            }
            x += e[1];
        }
        int n = s.length();
        x = (x % n + n) % n;
        return s.substring(n - x) + s.substring(0, n - x);
    }
}
```

```cpp
class Solution {
public:
    string stringShift(string s, vector<vector<int>>& shift) {
        int x = 0;
        for (auto& e : shift) {
            if (e[0] == 0) {
                e[1] = -e[1];
            }
            x += e[1];
        }
        int n = s.size();
        x = (x % n + n) % n;
        return s.substr(n - x, x) + s.substr(0, n - x);
    }
};
```

```go
func stringShift(s string, shift [][]int) string {
	x := 0
	for _, e := range shift {
		if e[0] == 0 {
			e[1] = -e[1]
		}
		x += e[1]
	}
	n := len(s)
	x = (x%n + n) % n
	return s[n-x:] + s[:n-x]
}
```

```ts
function stringShift(s: string, shift: number[][]): string {
    let x = 0;
    for (const [a, b] of shift) {
        x += a === 0 ? -b : b;
    }
    x %= s.length;
    if (x < 0) {
        x += s.length;
    }
    return s.slice(-x) + s.slice(0, -x);
}
```

<!-- tabs:end -->

<!-- end -->
