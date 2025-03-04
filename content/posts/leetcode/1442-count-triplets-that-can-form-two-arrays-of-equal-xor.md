---
title: 1442 Count Triplets That Can Form Two Arrays of Equal XOR
summary: 1442 Count Triplets That Can Form Two Arrays of Equal XOR LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1442 Count Triplets That Can Form Two Arrays of Equal XOR LeetCode Solution Explained in all languages", "1442 Count Triplets That Can Form Two Arrays of Equal XOR", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1442 Count Triplets That Can Form Two Arrays of Equal XOR - Solution Explained/problem-solving.webp
    alt: 1442 Count Triplets That Can Form Two Arrays of Equal XOR
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1442. Count Triplets That Can Form Two Arrays of Equal XOR](https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor)


## Description

<p>Given an array of integers <code>arr</code>.</p>

<p>We want to select three indices <code>i</code>, <code>j</code> and <code>k</code> where <code>(0 &lt;= i &lt; j &lt;= k &lt; arr.length)</code>.</p>

<p>Let&#39;s define <code>a</code> and <code>b</code> as follows:</p>

<ul>
	<li><code>a = arr[i] ^ arr[i + 1] ^ ... ^ arr[j - 1]</code></li>
	<li><code>b = arr[j] ^ arr[j + 1] ^ ... ^ arr[k]</code></li>
</ul>

<p>Note that <strong>^</strong> denotes the <strong>bitwise-xor</strong> operation.</p>

<p>Return <em>the number of triplets</em> (<code>i</code>, <code>j</code> and <code>k</code>) Where <code>a == b</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,3,1,6,7]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The triplets are (0,1,2), (0,2,2), (2,3,4) and (2,4,4)
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,1,1,1,1]
<strong>Output:</strong> 10
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 300</code></li>
	<li><code>1 &lt;= arr[i] &lt;= 10<sup>8</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def countTriplets(self, arr: List[int]) -> int:
        n = len(arr)
        pre = [0] * (n + 1)
        for i in range(n):
            pre[i + 1] = pre[i] ^ arr[i]
        ans = 0
        for i in range(n - 1):
            for j in range(i + 1, n):
                for k in range(j, n):
                    a, b = pre[j] ^ pre[i], pre[k + 1] ^ pre[j]
                    if a == b:
                        ans += 1
        return ans
```

```java
class Solution {
    public int countTriplets(int[] arr) {
        int n = arr.length;
        int[] pre = new int[n + 1];
        for (int i = 0; i < n; ++i) {
            pre[i + 1] = pre[i] ^ arr[i];
        }
        int ans = 0;
        for (int i = 0; i < n - 1; ++i) {
            for (int j = i + 1; j < n; ++j) {
                for (int k = j; k < n; ++k) {
                    int a = pre[j] ^ pre[i];
                    int b = pre[k + 1] ^ pre[j];
                    if (a == b) {
                        ++ans;
                    }
                }
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int countTriplets(vector<int>& arr) {
        int n = arr.size();
        vector<int> pre(n + 1);
        for (int i = 0; i < n; ++i) pre[i + 1] = pre[i] ^ arr[i];
        int ans = 0;
        for (int i = 0; i < n - 1; ++i) {
            for (int j = i + 1; j < n; ++j) {
                for (int k = j; k < n; ++k) {
                    int a = pre[j] ^ pre[i], b = pre[k + 1] ^ pre[j];
                    if (a == b) ++ans;
                }
            }
        }
        return ans;
    }
};
```

```go
func countTriplets(arr []int) int {
	n := len(arr)
	pre := make([]int, n+1)
	for i := 0; i < n; i++ {
		pre[i+1] = pre[i] ^ arr[i]
	}
	ans := 0
	for i := 0; i < n-1; i++ {
		for j := i + 1; j < n; j++ {
			for k := j; k < n; k++ {
				a, b := pre[j]^pre[i], pre[k+1]^pre[j]
				if a == b {
					ans++
				}
			}
		}
	}
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
