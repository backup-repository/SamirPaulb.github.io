---
title: 1954 Minimum Garden Perimeter to Collect Enough Apples
summary: 1954 Minimum Garden Perimeter to Collect Enough Apples LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1954 Minimum Garden Perimeter to Collect Enough Apples LeetCode Solution Explained in all languages", "1954 Minimum Garden Perimeter to Collect Enough Apples", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1954 Minimum Garden Perimeter to Collect Enough Apples - Solution Explained/problem-solving.webp
    alt: 1954 Minimum Garden Perimeter to Collect Enough Apples
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1954. Minimum Garden Perimeter to Collect Enough Apples](https://leetcode.com/problems/minimum-garden-perimeter-to-collect-enough-apples)


## Description

<p>In a garden represented as an infinite 2D grid, there is an apple tree planted at <strong>every</strong> integer coordinate. The apple tree planted at an integer coordinate <code>(i, j)</code> has <code>|i| + |j|</code> apples growing on it.</p>

<p>You will buy an axis-aligned <strong>square plot</strong> of land that is centered at <code>(0, 0)</code>.</p>

<p>Given an integer <code>neededApples</code>, return <em>the <strong>minimum perimeter</strong> of a plot such that <strong>at least</strong></em><strong> </strong><code>neededApples</code> <em>apples are <strong>inside or on</strong> the perimeter of that plot</em>.</p>

<p>The value of <code>|x|</code> is defined as:</p>

<ul>
	<li><code>x</code> if <code>x &gt;= 0</code></li>
	<li><code>-x</code> if <code>x &lt; 0</code></li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1954.Minimum%20Garden%20Perimeter%20to%20Collect%20Enough%20Apples/images/1527_example_1_2.png" style="width: 442px; height: 449px;" />
<pre>
<strong>Input:</strong> neededApples = 1
<strong>Output:</strong> 8
<strong>Explanation:</strong> A square plot of side length 1 does not contain any apples.
However, a square plot of side length 2 has 12 apples inside (as depicted in the image above).
The perimeter is 2 * 4 = 8.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> neededApples = 13
<strong>Output:</strong> 16
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> neededApples = 1000000000
<strong>Output:</strong> 5040
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= neededApples &lt;= 10<sup>15</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minimumPerimeter(self, neededApples: int) -> int:
        x = 1
        while 2 * x * (x + 1) * (2 * x + 1) < neededApples:
            x += 1
        return x * 8
```

```java
class Solution {
    public long minimumPerimeter(long neededApples) {
        long x = 1;
        while (2 * x * (x + 1) * (2 * x + 1) < neededApples) {
            ++x;
        }
        return 8 * x;
    }
}
```

```cpp
class Solution {
public:
    long long minimumPerimeter(long long neededApples) {
        long long x = 1;
        while (2 * x * (x + 1) * (2 * x + 1) < neededApples) {
            ++x;
        }
        return 8 * x;
    }
};
```

```go
func minimumPerimeter(neededApples int64) int64 {
	var x int64 = 1
	for 2*x*(x+1)*(2*x+1) < neededApples {
		x++
	}
	return 8 * x
}
```

```ts
function minimumPerimeter(neededApples: number): number {
    let x = 1;
    while (2 * x * (x + 1) * (2 * x + 1) < neededApples) {
        ++x;
    }
    return 8 * x;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def minimumPerimeter(self, neededApples: int) -> int:
        l, r = 1, 100000
        while l < r:
            mid = (l + r) >> 1
            if 2 * mid * (mid + 1) * (2 * mid + 1) >= neededApples:
                r = mid
            else:
                l = mid + 1
        return l * 8
```

```java
class Solution {
    public long minimumPerimeter(long neededApples) {
        long l = 1, r = 100000;
        while (l < r) {
            long mid = (l + r) >> 1;
            if (2 * mid * (mid + 1) * (2 * mid + 1) >= neededApples) {
                r = mid;
            } else {
                l = mid + 1;
            }
        }
        return l * 8;
    }
}
```

```cpp
class Solution {
public:
    long long minimumPerimeter(long long neededApples) {
        long long l = 1, r = 100000;
        while (l < r) {
            long mid = (l + r) >> 1;
            if (2 * mid * (mid + 1) * (2 * mid + 1) >= neededApples) {
                r = mid;
            } else {
                l = mid + 1;
            }
        }
        return l * 8;
    }
};
```

```go
func minimumPerimeter(neededApples int64) int64 {
	var l, r int64 = 1, 100000
	for l < r {
		mid := (l + r) >> 1
		if 2*mid*(mid+1)*(2*mid+1) >= neededApples {
			r = mid
		} else {
			l = mid + 1
		}
	}
	return l * 8
}
```

```ts
function minimumPerimeter(neededApples: number): number {
    let l = 1;
    let r = 100000;
    while (l < r) {
        const mid = (l + r) >> 1;
        if (2 * mid * (mid + 1) * (2 * mid + 1) >= neededApples) {
            r = mid;
        } else {
            l = mid + 1;
        }
    }
    return 8 * l;
}
```

<!-- tabs:end -->

<!-- end -->
