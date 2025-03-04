---
title: 0754 Reach a Number
summary: 0754 Reach a Number LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0754 Reach a Number LeetCode Solution Explained in all languages", "0754 Reach a Number", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0754 Reach a Number - Solution Explained/problem-solving.webp
    alt: 0754 Reach a Number
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [754. Reach a Number](https://leetcode.com/problems/reach-a-number)


## Description

<p>You are standing at position <code>0</code> on an infinite number line. There is a destination at position <code>target</code>.</p>

<p>You can make some number of moves <code>numMoves</code> so that:</p>

<ul>
	<li>On each move, you can either go left or right.</li>
	<li>During the <code>i<sup>th</sup></code> move (starting from <code>i == 1</code> to <code>i == numMoves</code>), you take <code>i</code> steps in the chosen direction.</li>
</ul>

<p>Given the integer <code>target</code>, return <em>the <strong>minimum</strong> number of moves required (i.e., the minimum </em><code>numMoves</code><em>) to reach the destination</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> target = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong>
On the 1<sup>st</sup> move, we step from 0 to 1 (1 step).
On the 2<sup>nd</sup> move, we step from 1 to -1 (2 steps).
On the 3<sup>rd</sup> move, we step from -1 to 2 (3 steps).
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> target = 3
<strong>Output:</strong> 2
<strong>Explanation:</strong>
On the 1<sup>st</sup> move, we step from 0 to 1 (1 step).
On the 2<sup>nd</sup> move, we step from 1 to 3 (2 steps).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><code>target != 0</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def reachNumber(self, target: int) -> int:
        target = abs(target)
        s = k = 0
        while 1:
            if s >= target and (s - target) % 2 == 0:
                return k
            k += 1
            s += k
```

```java
class Solution {
    public int reachNumber(int target) {
        target = Math.abs(target);
        int s = 0, k = 0;
        while (true) {
            if (s >= target && (s - target) % 2 == 0) {
                return k;
            }
            ++k;
            s += k;
        }
    }
}
```

```cpp
class Solution {
public:
    int reachNumber(int target) {
        target = abs(target);
        int s = 0, k = 0;
        while (1) {
            if (s >= target && (s - target) % 2 == 0) return k;
            ++k;
            s += k;
        }
    }
};
```

```go
func reachNumber(target int) int {
	if target < 0 {
		target = -target
	}
	var s, k int
	for {
		if s >= target && (s-target)%2 == 0 {
			return k
		}
		k++
		s += k
	}
}
```

```js
/**
 * @param {number} target
 * @return {number}
 */
var reachNumber = function (target) {
    target = Math.abs(target);
    let [s, k] = [0, 0];
    while (1) {
        if (s >= target && (s - target) % 2 == 0) {
            return k;
        }
        ++k;
        s += k;
    }
};
```

<!-- tabs:end -->

<!-- end -->
