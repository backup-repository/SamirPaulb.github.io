---
title: 0319 Bulb Switcher
summary: 0319 Bulb Switcher LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0319 Bulb Switcher LeetCode Solution Explained in all languages", "0319 Bulb Switcher", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0319 Bulb Switcher - Solution Explained/problem-solving.webp
    alt: 0319 Bulb Switcher
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [319. Bulb Switcher](https://leetcode.com/problems/bulb-switcher)


## Description

<p>There are <code>n</code> bulbs that are initially off. You first turn on all the bulbs, then&nbsp;you turn off every second bulb.</p>

<p>On the third round, you toggle every third bulb (turning on if it&#39;s off or turning off if it&#39;s on). For the <code>i<sup>th</sup></code> round, you toggle every <code>i</code> bulb. For the <code>n<sup>th</sup></code> round, you only toggle the last bulb.</p>

<p>Return <em>the number of bulbs that are on after <code>n</code> rounds</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0319.Bulb%20Switcher/images/bulb.jpg" style="width: 421px; height: 321px;" />
<pre>
<strong>Input:</strong> n = 3
<strong>Output:</strong> 1
<strong>Explanation:</strong> At first, the three bulbs are [off, off, off].
After the first round, the three bulbs are [on, on, on].
After the second round, the three bulbs are [on, off, on].
After the third round, the three bulbs are [on, off, off]. 
So you should return 1 because there is only one bulb is on.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def bulbSwitch(self, n: int) -> int:
        return int(n ** (1 / 2))
```

```java
class Solution {
    public int bulbSwitch(int n) {
        return (int) Math.sqrt(n);
    }
}
```

<!-- tabs:end -->

<!-- end -->
