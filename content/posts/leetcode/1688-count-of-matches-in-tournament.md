---
title: 1688 Count of Matches in Tournament
summary: 1688 Count of Matches in Tournament LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1688 Count of Matches in Tournament LeetCode Solution Explained in all languages", "1688 Count of Matches in Tournament", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1688 Count of Matches in Tournament - Solution Explained/problem-solving.webp
    alt: 1688 Count of Matches in Tournament
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1688. Count of Matches in Tournament](https://leetcode.com/problems/count-of-matches-in-tournament)


## Description

<p>You are given an integer <code>n</code>, the number of teams in a tournament that has strange rules:</p>

<ul>
	<li>If the current number of teams is <strong>even</strong>, each team gets paired with another team. A total of <code>n / 2</code> matches are played, and <code>n / 2</code> teams advance to the next round.</li>
	<li>If the current number of teams is <strong>odd</strong>, one team randomly advances in the tournament, and the rest gets paired. A total of <code>(n - 1) / 2</code> matches are played, and <code>(n - 1) / 2 + 1</code> teams advance to the next round.</li>
</ul>

<p>Return <em>the number of matches played in the tournament until a winner is decided.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> 6
<strong>Explanation:</strong> Details of the tournament: 
- 1st Round: Teams = 7, Matches = 3, and 4 teams advance.
- 2nd Round: Teams = 4, Matches = 2, and 2 teams advance.
- 3rd Round: Teams = 2, Matches = 1, and 1 team is declared the winner.
Total number of matches = 3 + 2 + 1 = 6.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 14
<strong>Output:</strong> 13
<strong>Explanation:</strong> Details of the tournament:
- 1st Round: Teams = 14, Matches = 7, and 7 teams advance.
- 2nd Round: Teams = 7, Matches = 3, and 4 teams advance.
- 3rd Round: Teams = 4, Matches = 2, and 2 teams advance.
- 4th Round: Teams = 2, Matches = 1, and 1 team is declared the winner.
Total number of matches = 7 + 3 + 2 + 1 = 13.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 200</code></li>
</ul>

## Solutions

### Solution 1: Quick Thinking

From the problem description, we know that there are $n$ teams in total. Each pairing will eliminate one team. Therefore, the number of pairings is equal to the number of teams eliminated, which is $n - 1$.

The time complexity is $O(1)$, and the space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def numberOfMatches(self, n: int) -> int:
        return n - 1
```

```java
class Solution {
    public int numberOfMatches(int n) {
        return n - 1;
    }
}
```

```cpp
class Solution {
public:
    int numberOfMatches(int n) {
        return n - 1;
    }
};
```

```go
func numberOfMatches(n int) int {
	return n - 1
}
```

```ts
function numberOfMatches(n: number): number {
    return n - 1;
}
```

```js
/**
 * @param {number} n
 * @return {number}
 */
var numberOfMatches = function (n) {
    return n - 1;
};
```

<!-- tabs:end -->

<!-- end -->
