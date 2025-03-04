---
title: 0495 Teemo Attacking
summary: 0495 Teemo Attacking LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0495 Teemo Attacking LeetCode Solution Explained in all languages", "0495 Teemo Attacking", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0495 Teemo Attacking - Solution Explained/problem-solving.webp
    alt: 0495 Teemo Attacking
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [495. Teemo Attacking](https://leetcode.com/problems/teemo-attacking)


## Description

<p>Our hero Teemo is attacking an enemy Ashe with poison attacks! When Teemo attacks Ashe, Ashe gets poisoned for a exactly <code>duration</code> seconds. More formally, an attack at second <code>t</code> will mean Ashe is poisoned during the <strong>inclusive</strong> time interval <code>[t, t + duration - 1]</code>. If Teemo attacks again <strong>before</strong> the poison effect ends, the timer for it is <strong>reset</strong>, and the poison effect will end <code>duration</code> seconds after the new attack.</p>

<p>You are given a <strong>non-decreasing</strong> integer array <code>timeSeries</code>, where <code>timeSeries[i]</code> denotes that Teemo attacks Ashe at second <code>timeSeries[i]</code>, and an integer <code>duration</code>.</p>

<p>Return <em>the <strong>total</strong> number of seconds that Ashe is poisoned</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> timeSeries = [1,4], duration = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Teemo&#39;s attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 4, Teemo attacks, and Ashe is poisoned for seconds 4 and 5.
Ashe is poisoned for seconds 1, 2, 4, and 5, which is 4 seconds in total.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> timeSeries = [1,2], duration = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong> Teemo&#39;s attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 2 however, Teemo attacks again and resets the poison timer. Ashe is poisoned for seconds 2 and 3.
Ashe is poisoned for seconds 1, 2, and 3, which is 3 seconds in total.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= timeSeries.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= timeSeries[i], duration &lt;= 10<sup>7</sup></code></li>
	<li><code>timeSeries</code> is sorted in <strong>non-decreasing</strong> order.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        ans = duration
        for a, b in pairwise(timeSeries):
            ans += min(duration, b - a)
        return ans
```

```java
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        int n = timeSeries.length;
        int ans = duration;
        for (int i = 1; i < n; ++i) {
            ans += Math.min(duration, timeSeries[i] - timeSeries[i - 1]);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int ans = duration;
        int n = timeSeries.size();
        for (int i = 1; i < n; ++i) {
            ans += min(duration, timeSeries[i] - timeSeries[i - 1]);
        }
        return ans;
    }
};
```

```go
func findPoisonedDuration(timeSeries []int, duration int) (ans int) {
	ans = duration
	for i, x := range timeSeries[1:] {
		ans += min(duration, x-timeSeries[i])
	}
	return
}
```

```ts
function findPoisonedDuration(timeSeries: number[], duration: number): number {
    const n = timeSeries.length;
    let ans = duration;
    for (let i = 1; i < n; ++i) {
        ans += Math.min(duration, timeSeries[i] - timeSeries[i - 1]);
    }
    return ans;
}
```

```cs
public class Solution {
    public int FindPoisonedDuration(int[] timeSeries, int duration) {
        int ans = duration;
        int n = timeSeries.Length;
        for (int i = 1; i < n; ++i) {
            ans += Math.Min(duration, timeSeries[i] - timeSeries[i - 1]);
        }
        return ans;
    }
}
```

<!-- tabs:end -->

<!-- end -->
