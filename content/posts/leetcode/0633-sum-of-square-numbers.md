---
title: 0633 Sum of Square Numbers
summary: 0633 Sum of Square Numbers LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0633 Sum of Square Numbers LeetCode Solution Explained in all languages", "0633 Sum of Square Numbers", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0633 Sum of Square Numbers - Solution Explained/problem-solving.webp
    alt: 0633 Sum of Square Numbers
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [633. Sum of Square Numbers](https://leetcode.com/problems/sum-of-square-numbers)


## Description

<p>Given a non-negative integer <code>c</code>, decide whether there&#39;re two integers <code>a</code> and <code>b</code> such that <code>a<sup>2</sup> + b<sup>2</sup> = c</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> c = 5
<strong>Output:</strong> true
<strong>Explanation:</strong> 1 * 1 + 2 * 2 = 5
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> c = 3
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= c &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        a, b = 0, int(sqrt(c))
        while a <= b:
            s = a**2 + b**2
            if s == c:
                return True
            if s < c:
                a += 1
            else:
                b -= 1
        return False
```

```java
class Solution {
    public boolean judgeSquareSum(int c) {
        long a = 0, b = (long) Math.sqrt(c);
        while (a <= b) {
            long s = a * a + b * b;
            if (s == c) {
                return true;
            }
            if (s < c) {
                ++a;
            } else {
                --b;
            }
        }
        return false;
    }
}
```

```cpp
class Solution {
public:
    bool judgeSquareSum(int c) {
        long a = 0, b = (long) sqrt(c);
        while (a <= b) {
            long s = a * a + b * b;
            if (s == c) return true;
            if (s < c)
                ++a;
            else
                --b;
        }
        return false;
    }
};
```

```go
func judgeSquareSum(c int) bool {
	a, b := 0, int(math.Sqrt(float64(c)))
	for a <= b {
		s := a*a + b*b
		if s == c {
			return true
		}
		if s < c {
			a++
		} else {
			b--
		}
	}
	return false
}
```

```ts
function judgeSquareSum(c: number): boolean {
    let a = 0,
        b = Math.floor(Math.sqrt(c));
    while (a <= b) {
        let sum = a ** 2 + b ** 2;
        if (sum == c) return true;
        if (sum < c) {
            ++a;
        } else {
            --b;
        }
    }
    return false;
}
```

```rust
use std::cmp::Ordering;
impl Solution {
    pub fn judge_square_sum(c: i32) -> bool {
        let c = c as i64;
        let mut left = 0;
        let mut right = (c as f64).sqrt() as i64;
        while left <= right {
            let num = left * left + right * right;
            match num.cmp(&c) {
                Ordering::Less => {
                    left += 1;
                }
                Ordering::Greater => {
                    right -= 1;
                }
                Ordering::Equal => {
                    return true;
                }
            }
        }
        false
    }
}
```

<!-- tabs:end -->

<!-- end -->
