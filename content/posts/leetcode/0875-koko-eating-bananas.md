---
title: 0875 Koko Eating Bananas
summary: 0875 Koko Eating Bananas LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0875 Koko Eating Bananas LeetCode Solution Explained in all languages", "0875 Koko Eating Bananas", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0875 Koko Eating Bananas - Solution Explained/problem-solving.webp
    alt: 0875 Koko Eating Bananas
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas)


## Description

<p>Koko loves to eat bananas. There are <code>n</code> piles of bananas, the <code>i<sup>th</sup></code> pile has <code>piles[i]</code> bananas. The guards have gone and will come back in <code>h</code> hours.</p>

<p>Koko can decide her bananas-per-hour eating speed of <code>k</code>. Each hour, she chooses some pile of bananas and eats <code>k</code> bananas from that pile. If the pile has less than <code>k</code> bananas, she eats all of them instead and will not eat any more bananas during this hour.</p>

<p>Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.</p>

<p>Return <em>the minimum integer</em> <code>k</code> <em>such that she can eat all the bananas within</em> <code>h</code> <em>hours</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> piles = [3,6,7,11], h = 8
<strong>Output:</strong> 4
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> piles = [30,11,23,4,20], h = 5
<strong>Output:</strong> 30
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> piles = [30,11,23,4,20], h = 6
<strong>Output:</strong> 23
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= piles.length &lt;= 10<sup>4</sup></code></li>
	<li><code>piles.length &lt;= h &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= piles[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        left, right = 1, int(1e9)
        while left < right:
            mid = (left + right) >> 1
            s = sum((x + mid - 1) // mid for x in piles)
            if s <= h:
                right = mid
            else:
                left = mid + 1
        return left
```

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int left = 1, right = (int) 1e9;
        while (left < right) {
            int mid = (left + right) >>> 1;
            int s = 0;
            for (int x : piles) {
                s += (x + mid - 1) / mid;
            }
            if (s <= h) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

```cpp
class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {
        int left = 1, right = 1e9;
        while (left < right) {
            int mid = (left + right) >> 1;
            int s = 0;
            for (int& x : piles) s += (x + mid - 1) / mid;
            if (s <= h)
                right = mid;
            else
                left = mid + 1;
        }
        return left;
    }
};
```

```go
func minEatingSpeed(piles []int, h int) int {
	return sort.Search(1e9, func(i int) bool {
		if i == 0 {
			return false
		}
		s := 0
		for _, x := range piles {
			s += (x + i - 1) / i
		}
		return s <= h
	})
}
```

```ts
function minEatingSpeed(piles: number[], h: number): number {
    let left = 1;
    let right = Math.max(...piles);
    while (left < right) {
        const mid = (left + right) >> 1;
        let s = 0;
        for (const x of piles) {
            s += Math.ceil(x / mid);
        }
        if (s <= h) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
}
```

```cs
public class Solution {
    public int MinEatingSpeed(int[] piles, int h) {
        int left = 1, right = piles.Max();
        while (left < right)
        {
            int mid = (left + right) >> 1;
            int s = 0;
            foreach (int pile in piles)
            {
                s += (pile + mid - 1) / mid;
            }
            if (s <= h)
            {
                right = mid;
            }
            else
            {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

<!-- tabs:end -->

<!-- end -->
