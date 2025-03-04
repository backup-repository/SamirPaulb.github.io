---
title: 1118 Number of Days in a Month
summary: 1118 Number of Days in a Month LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1118 Number of Days in a Month LeetCode Solution Explained in all languages", "1118 Number of Days in a Month", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1118 Number of Days in a Month - Solution Explained/problem-solving.webp
    alt: 1118 Number of Days in a Month
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1118. Number of Days in a Month](https://leetcode.com/problems/number-of-days-in-a-month)


## Description

<p>Given a year <code>year</code> and a month <code>month</code>, return <em>the number of days of that month</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> year = 1992, month = 7
<strong>Output:</strong> 31
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> year = 2000, month = 2
<strong>Output:</strong> 29
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> year = 1900, month = 2
<strong>Output:</strong> 28
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1583 &lt;= year &lt;= 2100</code></li>
	<li><code>1 &lt;= month &lt;= 12</code></li>
</ul>

## Solutions

### Solution 1: Determine Leap Year

We can first determine whether the given year is a leap year. If the year can be divided by $4$ but not by $100$, or can be divided by $400$, then this year is a leap year.

February has $29$ days in a leap year and $28$ days in a common year.

We can use an array $days$ to store the number of days in each month of the current year, where $days[0]=0$, $days[i]$ represents the number of days in the $i$th month of the current year. Then the answer is $days[month]$.

The time complexity is $O(1)$, and the space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def numberOfDays(self, year: int, month: int) -> int:
        leap = (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0)
        days = [0, 31, 29 if leap else 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
        return days[month]
```

```java
class Solution {
    public int numberOfDays(int year, int month) {
        boolean leap = (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
        int[] days = new int[] {0, 31, leap ? 29 : 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
        return days[month];
    }
}
```

```cpp
class Solution {
public:
    int numberOfDays(int year, int month) {
        bool leap = (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
        vector<int> days = {0, 31, leap ? 29 : 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
        return days[month];
    }
};
```

```go
func numberOfDays(year int, month int) int {
	leap := (year%4 == 0 && year%100 != 0) || (year%400 == 0)
	x := 28
	if leap {
		x = 29
	}
	days := []int{0, 31, x, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}
	return days[month]
}
```

```ts
function numberOfDays(year: number, month: number): number {
    const leap = (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0;
    const days = [0, 31, leap ? 29 : 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
    return days[month];
}
```

<!-- tabs:end -->

<!-- end -->
