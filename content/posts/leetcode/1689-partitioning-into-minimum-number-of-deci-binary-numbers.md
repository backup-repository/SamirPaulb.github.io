---
title: 1689 Partitioning Into Minimum Number Of Deci Binary Numbers
summary: 1689 Partitioning Into Minimum Number Of Deci Binary Numbers LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1689 Partitioning Into Minimum Number Of Deci Binary Numbers LeetCode Solution Explained in all languages", "1689 Partitioning Into Minimum Number Of Deci Binary Numbers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1689 Partitioning Into Minimum Number Of Deci Binary Numbers - Solution Explained/problem-solving.webp
    alt: 1689 Partitioning Into Minimum Number Of Deci Binary Numbers
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1689. Partitioning Into Minimum Number Of Deci-Binary Numbers](https://leetcode.com/problems/partitioning-into-minimum-number-of-deci-binary-numbers)


## Description

<p>A decimal number is called <strong>deci-binary</strong> if each of its digits is either <code>0</code> or <code>1</code> without any leading zeros. For example, <code>101</code> and <code>1100</code> are <strong>deci-binary</strong>, while <code>112</code> and <code>3001</code> are not.</p>

<p>Given a string <code>n</code> that represents a positive decimal integer, return <em>the <strong>minimum</strong> number of positive <strong>deci-binary</strong> numbers needed so that they sum up to </em><code>n</code><em>.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = &quot;32&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> 10 + 11 + 11 = 32
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = &quot;82734&quot;
<strong>Output:</strong> 8
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = &quot;27346209830709182346&quot;
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n.length &lt;= 10<sup>5</sup></code></li>
	<li><code>n</code> consists of only digits.</li>
	<li><code>n</code> does not contain any leading zeros and represents a positive integer.</li>
</ul>

## Solutions

### Solution 1: Quick Thinking

The problem is equivalent to finding the maximum number in the string.

The time complexity is $O(n)$, where $n$ is the length of the string. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def minPartitions(self, n: str) -> int:
        return int(max(n))
```

```java
class Solution {
    public int minPartitions(String n) {
        int ans = 0;
        for (int i = 0; i < n.length(); ++i) {
            ans = Math.max(ans, n.charAt(i) - '0');
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int minPartitions(string n) {
        int ans = 0;
        for (char& c : n) ans = max(ans, c - '0');
        return ans;
    }
};
```

```go
func minPartitions(n string) (ans int) {
	for _, c := range n {
		if t := int(c - '0'); ans < t {
			ans = t
		}
	}
	return
}
```

```ts
function minPartitions(n: string): number {
    let nums = n.split('').map(d => parseInt(d));
    let ans = Math.max(...nums);
    return ans;
}
```

```rust
impl Solution {
    pub fn min_partitions(n: String) -> i32 {
        let mut ans = 0;
        for c in n.as_bytes() {
            ans = ans.max((c - b'0') as i32);
        }
        ans
    }
}
```

```c
int minPartitions(char* n) {
    int ans = 0;
    for (int i = 0; n[i]; i++) {
        int v = n[i] - '0';
        if (v > ans) {
            ans = v;
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
