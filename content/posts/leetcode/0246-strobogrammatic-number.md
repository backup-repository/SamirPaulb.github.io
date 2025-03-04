---
title: 0246 Strobogrammatic Number
summary: 0246 Strobogrammatic Number LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0246 Strobogrammatic Number LeetCode Solution Explained in all languages", "0246 Strobogrammatic Number", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0246 Strobogrammatic Number - Solution Explained/problem-solving.webp
    alt: 0246 Strobogrammatic Number
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [246. Strobogrammatic Number](https://leetcode.com/problems/strobogrammatic-number)


## Description

<p>Given a string <code>num</code> which represents an integer, return <code>true</code> <em>if</em> <code>num</code> <em>is a <strong>strobogrammatic number</strong></em>.</p>

<p>A <strong>strobogrammatic number</strong> is a number that looks the same when rotated <code>180</code> degrees (looked at upside down).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;69&quot;
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;88&quot;
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> num = &quot;962&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num.length &lt;= 50</code></li>
	<li><code>num</code> consists of only digits.</li>
	<li><code>num</code> does not contain any leading zeros except for zero itself.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isStrobogrammatic(self, num: str) -> bool:
        d = [0, 1, -1, -1, -1, -1, 9, -1, 8, 6]
        i, j = 0, len(num) - 1
        while i <= j:
            a, b = int(num[i]), int(num[j])
            if d[a] != b:
                return False
            i, j = i + 1, j - 1
        return True
```

```java
class Solution {
    public boolean isStrobogrammatic(String num) {
        int[] d = new int[] {0, 1, -1, -1, -1, -1, 9, -1, 8, 6};
        for (int i = 0, j = num.length() - 1; i <= j; ++i, --j) {
            int a = num.charAt(i) - '0', b = num.charAt(j) - '0';
            if (d[a] != b) {
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
    bool isStrobogrammatic(string num) {
        vector<int> d = {0, 1, -1, -1, -1, -1, 9, -1, 8, 6};
        for (int i = 0, j = num.size() - 1; i <= j; ++i, --j) {
            int a = num[i] - '0', b = num[j] - '0';
            if (d[a] != b) {
                return false;
            }
        }
        return true;
    }
};
```

```go
func isStrobogrammatic(num string) bool {
	d := []int{0, 1, -1, -1, -1, -1, 9, -1, 8, 6}
	for i, j := 0, len(num)-1; i <= j; i, j = i+1, j-1 {
		a, b := int(num[i]-'0'), int(num[j]-'0')
		if d[a] != b {
			return false
		}
	}
	return true
}
```

<!-- tabs:end -->

<!-- end -->
