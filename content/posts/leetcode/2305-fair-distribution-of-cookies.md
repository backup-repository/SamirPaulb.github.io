---
title: 2305 Fair Distribution of Cookies
summary: 2305 Fair Distribution of Cookies LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2305 Fair Distribution of Cookies LeetCode Solution Explained in all languages", "2305 Fair Distribution of Cookies", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2305 Fair Distribution of Cookies - Solution Explained/problem-solving.webp
    alt: 2305 Fair Distribution of Cookies
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2305. Fair Distribution of Cookies](https://leetcode.com/problems/fair-distribution-of-cookies)


## Description

<p>You are given an integer array <code>cookies</code>, where <code>cookies[i]</code> denotes the number of cookies in the <code>i<sup>th</sup></code> bag. You are also given an integer <code>k</code> that denotes the number of children to distribute <strong>all</strong> the bags of cookies to. All the cookies in the same bag must go to the same child and cannot be split up.</p>

<p>The <strong>unfairness</strong> of a distribution is defined as the <strong>maximum</strong> <strong>total</strong> cookies obtained by a single child in the distribution.</p>

<p>Return <em>the <strong>minimum</strong> unfairness of all distributions</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> cookies = [8,15,10,20,8], k = 2
<strong>Output:</strong> 31
<strong>Explanation:</strong> One optimal distribution is [8,15,8] and [10,20]
- The 1<sup>st</sup> child receives [8,15,8] which has a total of 8 + 15 + 8 = 31 cookies.
- The 2<sup>nd</sup> child receives [10,20] which has a total of 10 + 20 = 30 cookies.
The unfairness of the distribution is max(31,30) = 31.
It can be shown that there is no distribution with an unfairness less than 31.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> cookies = [6,1,3,2,2,4,1,2], k = 3
<strong>Output:</strong> 7
<strong>Explanation:</strong> One optimal distribution is [6,1], [3,2,2], and [4,1,2]
- The 1<sup>st</sup> child receives [6,1] which has a total of 6 + 1 = 7 cookies.
- The 2<sup>nd</sup> child receives [3,2,2] which has a total of 3 + 2 + 2 = 7 cookies.
- The 3<sup>rd</sup> child receives [4,1,2] which has a total of 4 + 1 + 2 = 7 cookies.
The unfairness of the distribution is max(7,7,7) = 7.
It can be shown that there is no distribution with an unfairness less than 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= cookies.length &lt;= 8</code></li>
	<li><code>1 &lt;= cookies[i] &lt;= 10<sup>5</sup></code></li>
	<li><code>2 &lt;= k &lt;= cookies.length</code></li>
</ul>

## Solutions

### Solution 1: Backtracking + Pruning

First, we sort the array $cookies$ in descending order (to reduce the number of searches), and then create an array $cnt$ of length $k$ to store the number of cookies each child gets. Also, we use a variable $ans$ to maintain the current minimum degree of unfairness, initialized to a very large value.

Next, we start from the first snack pack. For the current snack pack $i$, we enumerate each child $j$. If the cookies $cookies[i]$ in the current snack pack are given to child $j$, making the degree of unfairness greater than or equal to $ans$, or the number of cookies the current child already has is the same as the previous child, then we don't need to consider giving the cookies in the current snack pack to child $j$, just skip it (pruning). Otherwise, we give the cookies $cookies[i]$ in the current snack pack to child $j$, and then continue to consider the next snack pack. When we have considered all the snack packs, we update the value of $ans$, then backtrack to the previous snack pack, and continue to enumerate which child to give the cookies in the current snack pack to.

Finally, we return $ans$.

<!-- tabs:start -->

```python
class Solution:
    def distributeCookies(self, cookies: List[int], k: int) -> int:
        def dfs(i):
            if i >= len(cookies):
                nonlocal ans
                ans = max(cnt)
                return
            for j in range(k):
                if cnt[j] + cookies[i] >= ans or (j and cnt[j] == cnt[j - 1]):
                    continue
                cnt[j] += cookies[i]
                dfs(i + 1)
                cnt[j] -= cookies[i]

        ans = inf
        cnt = [0] * k
        cookies.sort(reverse=True)
        dfs(0)
        return ans
```

```java
class Solution {
    private int[] cookies;
    private int[] cnt;
    private int k;
    private int n;
    private int ans = 1 << 30;

    public int distributeCookies(int[] cookies, int k) {
        n = cookies.length;
        cnt = new int[k];
        // 升序排列
        Arrays.sort(cookies);
        this.cookies = cookies;
        this.k = k;
        // 这里搜索顺序是 n-1, n-2,...0
        dfs(n - 1);
        return ans;
    }

    private void dfs(int i) {
        if (i < 0) {
            // ans = Arrays.stream(cnt).max().getAsInt();
            ans = 0;
            for (int v : cnt) {
                ans = Math.max(ans, v);
            }
            return;
        }
        for (int j = 0; j < k; ++j) {
            if (cnt[j] + cookies[i] >= ans || (j > 0 && cnt[j] == cnt[j - 1])) {
                continue;
            }
            cnt[j] += cookies[i];
            dfs(i - 1);
            cnt[j] -= cookies[i];
        }
    }
}
```

```cpp
class Solution {
public:
    int distributeCookies(vector<int>& cookies, int k) {
        sort(cookies.rbegin(), cookies.rend());
        int cnt[k];
        memset(cnt, 0, sizeof cnt);
        int n = cookies.size();
        int ans = 1 << 30;
        function<void(int)> dfs = [&](int i) {
            if (i >= n) {
                ans = *max_element(cnt, cnt + k);
                return;
            }
            for (int j = 0; j < k; ++j) {
                if (cnt[j] + cookies[i] >= ans || (j && cnt[j] == cnt[j - 1])) {
                    continue;
                }
                cnt[j] += cookies[i];
                dfs(i + 1);
                cnt[j] -= cookies[i];
            }
        };
        dfs(0);
        return ans;
    }
};
```

```go
func distributeCookies(cookies []int, k int) int {
	sort.Sort(sort.Reverse(sort.IntSlice(cookies)))
	cnt := make([]int, k)
	ans := 1 << 30
	var dfs func(int)
	dfs = func(i int) {
		if i >= len(cookies) {
			ans = slices.Max(cnt)
			return
		}
		for j := 0; j < k; j++ {
			if cnt[j]+cookies[i] >= ans || (j > 0 && cnt[j] == cnt[j-1]) {
				continue
			}
			cnt[j] += cookies[i]
			dfs(i + 1)
			cnt[j] -= cookies[i]
		}
	}
	dfs(0)
	return ans
}
```

```ts
function distributeCookies(cookies: number[], k: number): number {
    const cnt = new Array(k).fill(0);
    let ans = 1 << 30;
    const dfs = (i: number) => {
        if (i >= cookies.length) {
            ans = Math.max(...cnt);
            return;
        }
        for (let j = 0; j < k; ++j) {
            if (cnt[j] + cookies[i] >= ans || (j && cnt[j] == cnt[j - 1])) {
                continue;
            }
            cnt[j] += cookies[i];
            dfs(i + 1);
            cnt[j] -= cookies[i];
        }
    };
    dfs(0);
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
