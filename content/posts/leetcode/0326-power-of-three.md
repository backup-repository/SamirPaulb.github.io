---
title: 0326 Power of Three
summary: 0326 Power of Three LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0326 Power of Three LeetCode Solution Explained in all languages", "0326 Power of Three", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0326 Power of Three - Solution Explained/problem-solving.webp
    alt: 0326 Power of Three
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [326. Power of Three](https://leetcode.com/problems/power-of-three)


## Description

<p>Given an integer <code>n</code>, return <em><code>true</code> if it is a power of three. Otherwise, return <code>false</code></em>.</p>

<p>An integer <code>n</code> is a power of three, if there exists an integer <code>x</code> such that <code>n == 3<sup>x</sup></code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 27
<strong>Output:</strong> true
<strong>Explanation:</strong> 27 = 3<sup>3</sup>
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 0
<strong>Output:</strong> false
<strong>Explanation:</strong> There is no x where 3<sup>x</sup> = 0.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = -1
<strong>Output:</strong> false
<strong>Explanation:</strong> There is no x where 3<sup>x</sup> = (-1).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup> &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you solve it without loops/recursion?

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        while n > 2:
            if n % 3:
                return False
            n //= 3
        return n == 1
```

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        while (n > 2) {
            if (n % 3 != 0) {
                return false;
            }
            n /= 3;
        }
        return n == 1;
    }
}
```

```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        while (n > 2) {
            if (n % 3) {
                return false;
            }
            n /= 3;
        }
        return n == 1;
    }
};
```

```go
func isPowerOfThree(n int) bool {
	for n > 2 {
		if n%3 != 0 {
			return false
		}
		n /= 3
	}
	return n == 1
}
```

```ts
function isPowerOfThree(n: number): boolean {
    return n > 0 && 1162261467 % n == 0;
}
```

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function (n) {
    return n > 0 && 1162261467 % n == 0;
};
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        return n > 0 and 1162261467 % n == 0
```

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
}
```

```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
};
```

```go
func isPowerOfThree(n int) bool {
	return n > 0 && 1162261467%n == 0
}
```

<!-- tabs:end -->

<!-- end -->
