---
title: 1561 Maximum Number of Coins You Can Get
summary: 1561 Maximum Number of Coins You Can Get LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1561 Maximum Number of Coins You Can Get LeetCode Solution Explained in all languages", "1561 Maximum Number of Coins You Can Get", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1561 Maximum Number of Coins You Can Get - Solution Explained/problem-solving.webp
    alt: 1561 Maximum Number of Coins You Can Get
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1561. Maximum Number of Coins You Can Get](https://leetcode.com/problems/maximum-number-of-coins-you-can-get)


## Description

<p>There are <code>3n</code> piles of coins of varying size, you and your friends will take piles of coins as follows:</p>

<ul>
	<li>In each step, you will choose <strong>any </strong><code>3</code> piles of coins (not necessarily consecutive).</li>
	<li>Of your choice, Alice will pick the pile with the maximum number of coins.</li>
	<li>You will pick the next pile with the maximum number of coins.</li>
	<li>Your friend Bob will pick the last pile.</li>
	<li>Repeat until there are no more piles of coins.</li>
</ul>

<p>Given an array of integers <code>piles</code> where <code>piles[i]</code> is the number of coins in the <code>i<sup>th</sup></code> pile.</p>

<p>Return the maximum number of coins that you can have.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> piles = [2,4,1,2,7,8]
<strong>Output:</strong> 9
<strong>Explanation: </strong>Choose the triplet (2, 7, 8), Alice Pick the pile with 8 coins, you the pile with <strong>7</strong> coins and Bob the last one.
Choose the triplet (1, 2, 4), Alice Pick the pile with 4 coins, you the pile with <strong>2</strong> coins and Bob the last one.
The maximum number of coins which you can have are: 7 + 2 = 9.
On the other hand if we choose this arrangement (1, <strong>2</strong>, 8), (2, <strong>4</strong>, 7) you only get 2 + 4 = 6 coins which is not optimal.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> piles = [2,4,5]
<strong>Output:</strong> 4
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> piles = [9,8,7,6,5,1,2,3,4]
<strong>Output:</strong> 18
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= piles.length &lt;= 10<sup>5</sup></code></li>
	<li><code>piles.length % 3 == 0</code></li>
	<li><code>1 &lt;= piles[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maxCoins(self, piles: List[int]) -> int:
        piles.sort()
        return sum(piles[-2 : len(piles) // 3 - 1 : -2])
```

```java
class Solution {

    public int maxCoins(int[] piles) {
        Arrays.sort(piles);
        int ans = 0;
        for (int i = piles.length - 2; i >= piles.length / 3; i -= 2) {
            ans += piles[i];
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxCoins(vector<int>& piles) {
        sort(piles.begin(), piles.end());
        int ans = 0;
        for (int i = piles.size() - 2; i >= (int) piles.size() / 3; i -= 2) ans += piles[i];
        return ans;
    }
};
```

```go
func maxCoins(piles []int) int {
	sort.Ints(piles)
	ans, n := 0, len(piles)
	for i := n - 2; i >= n/3; i -= 2 {
		ans += piles[i]
	}
	return ans
}
```

```ts
function maxCoins(piles: number[]): number {
    piles.sort((a, b) => a - b);
    const n = piles.length;
    let ans = 0;
    for (let i = 1; i <= Math.floor(n / 3); i++) {
        ans += piles[n - 2 * i];
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn max_coins(mut piles: Vec<i32>) -> i32 {
        piles.sort();
        let n = piles.len();
        let mut ans = 0;
        for i in 1..=n / 3 {
            ans += piles[n - 2 * i];
        }
        ans
    }
}
```

```c
int cmp(const void* a, const void* b) {
    return *(int*) a - *(int*) b;
}

int maxCoins(int* piles, int pilesSize) {
    qsort(piles, pilesSize, sizeof(int), cmp);
    int ans = 0;
    for (int i = 1; i <= pilesSize / 3; i++) {
        ans += piles[pilesSize - 2 * i];
    };
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
