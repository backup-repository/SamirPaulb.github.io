---
title: 2706 Buy Two Chocolates
summary: 2706 Buy Two Chocolates LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2706 Buy Two Chocolates LeetCode Solution Explained in all languages", "2706 Buy Two Chocolates", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2706 Buy Two Chocolates - Solution Explained/problem-solving.webp
    alt: 2706 Buy Two Chocolates
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2706. Buy Two Chocolates](https://leetcode.com/problems/buy-two-chocolates)


## Description

<p>You are given an integer array <code>prices</code> representing the prices of various chocolates in a store. You are also given a single integer <code>money</code>, which represents your initial amount of money.</p>

<p>You must buy <strong>exactly</strong> two chocolates in such a way that you still have some <strong>non-negative</strong> leftover money. You would like to minimize the sum of the prices of the two chocolates you buy.</p>

<p>Return <em>the amount of money you will have leftover after buying the two chocolates</em>. If there is no way for you to buy two chocolates without ending up in debt, return <code>money</code>. Note that the leftover must be non-negative.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> prices = [1,2,2], money = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong> Purchase the chocolates priced at 1 and 2 units respectively. You will have 3 - 3 = 0 units of money afterwards. Thus, we return 0.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> prices = [3,2,3], money = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> You cannot buy 2 chocolates without going in debt, so we return 3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= prices.length &lt;= 50</code></li>
	<li><code>1 &lt;= prices[i] &lt;= 100</code></li>
	<li><code>1 &lt;= money &lt;= 100</code></li>
</ul>

## Solutions

### Solution 1: Sorting

We can sort the prices of the chocolates in ascending order, and then add the first two prices to get the minimum cost $cost$ of buying two chocolates. If this cost is greater than the money we have, then we return `money`. Otherwise, we return `money - cost`.

The time complexity is $O(n \times \log n)$, and the space complexity is $O(\log n)$. Where $n$ is the length of the array `prices`.

<!-- tabs:start -->

```python
class Solution:
    def buyChoco(self, prices: List[int], money: int) -> int:
        prices.sort()
        cost = prices[0] + prices[1]
        return money if money < cost else money - cost
```

```java
class Solution {
    public int buyChoco(int[] prices, int money) {
        Arrays.sort(prices);
        int cost = prices[0] + prices[1];
        return money < cost ? money : money - cost;
    }
}
```

```cpp
class Solution {
public:
    int buyChoco(vector<int>& prices, int money) {
        sort(prices.begin(), prices.end());
        int cost = prices[0] + prices[1];
        return money < cost ? money : money - cost;
    }
};
```

```go
func buyChoco(prices []int, money int) int {
	sort.Ints(prices)
	cost := prices[0] + prices[1]
	if money < cost {
		return money
	}
	return money - cost
}
```

```ts
function buyChoco(prices: number[], money: number): number {
    prices.sort((a, b) => a - b);
    const cost = prices[0] + prices[1];
    return money < cost ? money : money - cost;
}
```

```rust
impl Solution {
    pub fn buy_choco(mut prices: Vec<i32>, money: i32) -> i32 {
        prices.sort();
        let cost = prices[0] + prices[1];
        if cost > money {
            return money;
        }
        money - cost
    }
}
```

<!-- tabs:end -->

### Solution 2: One-pass Traversal

We can find the two smallest prices in one pass, and then calculate the cost.

The time complexity is $O(n)$, where $n$ is the length of the array `prices`. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def buyChoco(self, prices: List[int], money: int) -> int:
        a = b = inf
        for x in prices:
            if x < a:
                a, b = x, a
            elif x < b:
                b = x
        cost = a + b
        return money if money < cost else money - cost
```

```java
class Solution {
    public int buyChoco(int[] prices, int money) {
        int a = 1000, b = 1000;
        for (int x : prices) {
            if (x < a) {
                b = a;
                a = x;
            } else if (x < b) {
                b = x;
            }
        }
        int cost = a + b;
        return money < cost ? money : money - cost;
    }
}
```

```cpp
class Solution {
public:
    int buyChoco(vector<int>& prices, int money) {
        int a = 1000, b = 1000;
        for (int x : prices) {
            if (x < a) {
                b = a;
                a = x;
            } else if (x < b) {
                b = x;
            }
        }
        int cost = a + b;
        return money < cost ? money : money - cost;
    }
};
```

```go
func buyChoco(prices []int, money int) int {
	a, b := 1001, 1001
	for _, x := range prices {
		if x < a {
			a, b = x, a
		} else if x < b {
			b = x
		}
	}
	cost := a + b
	if money < cost {
		return money
	}
	return money - cost
}
```

```ts
function buyChoco(prices: number[], money: number): number {
    let [a, b] = [1000, 1000];
    for (const x of prices) {
        if (x < a) {
            b = a;
            a = x;
        } else if (x < b) {
            b = x;
        }
    }
    const cost = a + b;
    return money < cost ? money : money - cost;
}
```

```rust
impl Solution {
    pub fn buy_choco(prices: Vec<i32>, money: i32) -> i32 {
        let mut a = 1000;
        let mut b = 1000;
        for &x in prices.iter() {
            if x < a {
                b = a;
                a = x;
            } else if x < b {
                b = x;
            }
        }
        let cost = a + b;
        if money < cost {
            money
        } else {
            money - cost
        }
    }
}
```

<!-- tabs:end -->

<!-- end -->
