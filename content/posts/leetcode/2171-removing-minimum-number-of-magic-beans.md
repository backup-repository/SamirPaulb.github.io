---
title: 2171 Removing Minimum Number of Magic Beans
summary: 2171 Removing Minimum Number of Magic Beans LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2171 Removing Minimum Number of Magic Beans LeetCode Solution Explained in all languages", "2171 Removing Minimum Number of Magic Beans", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2171 Removing Minimum Number of Magic Beans - Solution Explained/problem-solving.webp
    alt: 2171 Removing Minimum Number of Magic Beans
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2171. Removing Minimum Number of Magic Beans](https://leetcode.com/problems/removing-minimum-number-of-magic-beans)


## Description

<p>You are given an array of <strong>positive</strong> integers <code>beans</code>, where each integer represents the number of magic beans found in a particular magic bag.</p>

<p><strong>Remove</strong> any number of beans (<strong>possibly none</strong>) from each bag such that the number of beans in each remaining <strong>non-empty</strong> bag (still containing <strong>at least one</strong> bean) is <strong>equal</strong>. Once a bean has been removed from a bag, you are <strong>not</strong> allowed to return it to any of the bags.</p>

<p>Return <em>the <strong>minimum</strong> number of magic beans that you have to remove</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> beans = [4,1,6,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> 
- We remove 1 bean from the bag with only 1 bean.
  This results in the remaining bags: [4,<strong><u>0</u></strong>,6,5]
- Then we remove 2 beans from the bag with 6 beans.
  This results in the remaining bags: [4,0,<strong><u>4</u></strong>,5]
- Then we remove 1 bean from the bag with 5 beans.
  This results in the remaining bags: [4,0,4,<strong><u>4</u></strong>]
We removed a total of 1 + 2 + 1 = 4 beans to make the remaining non-empty bags have an equal number of beans.
There are no other solutions that remove 4 beans or fewer.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> beans = [2,10,3,2]
<strong>Output:</strong> 7
<strong>Explanation:</strong>
- We remove 2 beans from one of the bags with 2 beans.
  This results in the remaining bags: [<u><strong>0</strong></u>,10,3,2]
- Then we remove 2 beans from the other bag with 2 beans.
  This results in the remaining bags: [0,10,3,<u><strong>0</strong></u>]
- Then we remove 3 beans from the bag with 3 beans. 
  This results in the remaining bags: [0,10,<u><strong>0</strong></u>,0]
We removed a total of 2 + 2 + 3 = 7 beans to make the remaining non-empty bags have an equal number of beans.
There are no other solutions that removes 7 beans or fewer.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= beans.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= beans[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1: Sorting + Enumeration

We can sort all the beans in the bags in ascending order, and then enumerate the number of beans $beans[i]$ in each bag as the final number of beans in the bag. The total remaining number of beans is $beans[i] \times (n - i)$, so the number of beans that need to be taken out is $s - beans[i] \times (n - i)$, where $s$ is the total number of beans in all bags. We need to find the minimum number of beans that need to be taken out among all schemes.

The time complexity is $O(n \times \log n)$, and the space complexity is $O(\log n)$. Here, $n$ is the number of bags.

<!-- tabs:start -->

```python
class Solution:
    def minimumRemoval(self, beans: List[int]) -> int:
        beans.sort()
        s, n = sum(beans), len(beans)
        return min(s - x * (n - i) for i, x in enumerate(beans))
```

```java
class Solution {
    public long minimumRemoval(int[] beans) {
        Arrays.sort(beans);
        long s = 0;
        for (int x : beans) {
            s += x;
        }
        long ans = s;
        int n = beans.length;
        for (int i = 0; i < n; ++i) {
            ans = Math.min(ans, s - (long) beans[i] * (n - i));
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    long long minimumRemoval(vector<int>& beans) {
        sort(beans.begin(), beans.end());
        long long s = accumulate(beans.begin(), beans.end(), 0ll);
        long long ans = s;
        int n = beans.size();
        for (int i = 0; i < n; ++i) {
            ans = min(ans, s - 1ll * beans[i] * (n - i));
        }
        return ans;
    }
};
```

```go
func minimumRemoval(beans []int) int64 {
	sort.Ints(beans)
	s := 0
	for _, x := range beans {
		s += x
	}
	ans := s
	n := len(beans)
	for i, x := range beans {
		ans = min(ans, s-x*(n-i))
	}
	return int64(ans)
}
```

```ts
function minimumRemoval(beans: number[]): number {
    beans.sort((a, b) => a - b);
    const s = beans.reduce((a, b) => a + b, 0);
    const n = beans.length;
    let ans = s;
    for (let i = 0; i < n; ++i) {
        ans = Math.min(ans, s - beans[i] * (n - i));
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
