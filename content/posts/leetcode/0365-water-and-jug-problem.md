---
title: 0365 Water and Jug Problem
summary: 0365 Water and Jug Problem LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0365 Water and Jug Problem LeetCode Solution Explained in all languages", "0365 Water and Jug Problem", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0365 Water and Jug Problem - Solution Explained/problem-solving.webp
    alt: 0365 Water and Jug Problem
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [365. Water and Jug Problem](https://leetcode.com/problems/water-and-jug-problem)


## Description

<p>You are given two jugs with capacities <code>jug1Capacity</code> and <code>jug2Capacity</code> liters. There is an infinite amount of water supply available. Determine whether it is possible to measure exactly <code>targetCapacity</code> liters using these two jugs.</p>

<p>If <code>targetCapacity</code> liters of water are measurable, you must have <code>targetCapacity</code> liters of water contained <strong>within one or both buckets</strong> by the end.</p>

<p>Operations allowed:</p>

<ul>
	<li>Fill any of the jugs with water.</li>
	<li>Empty any of the jugs.</li>
	<li>Pour water from one jug into another till the other jug is completely full, or the first jug itself is empty.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> jug1Capacity = 3, jug2Capacity = 5, targetCapacity = 4
<strong>Output:</strong> true
<strong>Explanation:</strong> The famous <a href="https://www.youtube.com/watch?v=BVtQNK_ZUJg&amp;ab_channel=notnek01" target="_blank">Die Hard</a> example 
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> jug1Capacity = 2, jug2Capacity = 6, targetCapacity = 5
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> jug1Capacity = 1, jug2Capacity = 2, targetCapacity = 3
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= jug1Capacity, jug2Capacity, targetCapacity &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def canMeasureWater(
        self, jug1Capacity: int, jug2Capacity: int, targetCapacity: int
    ) -> bool:
        stk, seen = [], set()
        stk.append([0, 0])

        def get_hash(nums):
            return nums[0] * 10000006 + nums[1]

        while stk:
            if get_hash(stk[-1]) in seen:
                stk.pop()
                continue
            seen.add(get_hash(stk[-1]))
            cur = stk.pop()
            cur1, cur2 = cur[0], cur[1]
            if (
                cur1 == targetCapacity
                or cur2 == targetCapacity
                or cur1 + cur2 == targetCapacity
            ):
                return True
            stk.append([jug1Capacity, cur2])
            stk.append([0, cur2])
            stk.append([cur1, jug2Capacity])
            stk.append([cur1, 0])
            if cur1 + cur2 > jug1Capacity:
                stk.append([jug1Capacity, cur2 - jug1Capacity + cur1])
            else:
                stk.append([cur1 + cur2, 0])
            if cur1 + cur2 > jug2Capacity:
                stk.append([cur1 - jug2Capacity + cur2, jug2Capacity])
            else:
                stk.append([0, cur1 + cur2])
        return False
```

```java
class Solution {
    public boolean canMeasureWater(int jug1Capacity, int jug2Capacity, int targetCapacity) {
        Deque<int[]> stk = new ArrayDeque<>();
        stk.add(new int[] {0, 0});
        Set<Long> seen = new HashSet<>();
        while (!stk.isEmpty()) {
            if (seen.contains(hash(stk.peek()))) {
                stk.pop();
                continue;
            }
            int[] cur = stk.pop();
            seen.add(hash(cur));
            int cur1 = cur[0], cur2 = cur[1];
            if (cur1 == targetCapacity || cur2 == targetCapacity || cur1 + cur2 == targetCapacity) {
                return true;
            }
            stk.offer(new int[] {jug1Capacity, cur2});
            stk.offer(new int[] {0, cur2});
            stk.offer(new int[] {cur1, jug1Capacity});
            stk.offer(new int[] {cur2, 0});
            if (cur1 + cur2 > jug1Capacity) {
                stk.offer(new int[] {jug1Capacity, cur2 - jug1Capacity + cur1});
            } else {
                stk.offer(new int[] {cur1 + cur2, 0});
            }
            if (cur1 + cur2 > jug2Capacity) {
                stk.offer(new int[] {cur1 - jug2Capacity + cur2, jug2Capacity});
            } else {
                stk.offer(new int[] {0, cur1 + cur2});
            }
        }
        return false;
    }

    public long hash(int[] nums) {
        return nums[0] * 10000006L + nums[1];
    }
}
```

```cpp
class Solution {
public:
    bool canMeasureWater(int jug1Capacity, int jug2Capacity, int targetCapacity) {
        if (jug1Capacity + jug2Capacity < targetCapacity) return false;
        if (jug1Capacity == 0 || jug2Capacity == 0)
            return targetCapacity == 0 || jug1Capacity + jug2Capacity == targetCapacity;
        return targetCapacity % gcd(jug1Capacity, jug2Capacity) == 0;
    }

    int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }
};
```

```go
func canMeasureWater(jug1Capacity int, jug2Capacity int, targetCapacity int) bool {
	if jug1Capacity+jug2Capacity < targetCapacity {
		return false
	}
	if jug1Capacity == 0 || jug2Capacity == 0 {
		return targetCapacity == 0 || jug1Capacity+jug2Capacity == targetCapacity
	}

	var gcd func(a, b int) int
	gcd = func(a, b int) int {
		if b == 0 {
			return a
		}
		return gcd(b, a%b)
	}
	return targetCapacity%gcd(jug1Capacity, jug2Capacity) == 0
}
```

```cs
using System;

public class Solution {
    public bool CanMeasureWater(int x, int y, int z) {
        if (x == 0 || y == 0) return z == x || z == y;
        var gcd = GetGcd(x, y);
        return z >= 0 && z <= x + y && z % gcd == 0;
    }

    private int GetGcd(int x, int y)
    {
        while (x > 0)
        {
            var quotient = x / y;
            var reminder = x % y;
            if (reminder == 0)
            {
                return y;
            }
            x = y;
            y = reminder;
        }
        throw new Exception("Invalid x or y");
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def canMeasureWater(
        self, jug1Capacity: int, jug2Capacity: int, targetCapacity: int
    ) -> bool:
        if jug1Capacity + jug2Capacity < targetCapacity:
            return False
        if jug1Capacity == 0 or jug2Capacity == 0:
            return targetCapacity == 0 or jug1Capacity + jug2Capacity == targetCapacity
        return targetCapacity % gcd(jug1Capacity, jug2Capacity) == 0
```

```java
class Solution {
    public boolean canMeasureWater(int jug1Capacity, int jug2Capacity, int targetCapacity) {
        if (jug1Capacity + jug2Capacity < targetCapacity) {
            return false;
        }
        if (jug1Capacity == 0 || jug2Capacity == 0) {
            return targetCapacity == 0 || jug1Capacity + jug2Capacity == targetCapacity;
        }
        return targetCapacity % gcd(jug1Capacity, jug2Capacity) == 0;
    }

    private int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }
}
```

<!-- tabs:end -->

<!-- end -->
