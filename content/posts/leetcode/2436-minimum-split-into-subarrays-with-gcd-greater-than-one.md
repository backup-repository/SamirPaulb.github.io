---
title: 2436 Minimum Split Into Subarrays With GCD Greater Than One
summary: 2436 Minimum Split Into Subarrays With GCD Greater Than One LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2436 Minimum Split Into Subarrays With GCD Greater Than One LeetCode Solution Explained in all languages", "2436 Minimum Split Into Subarrays With GCD Greater Than One", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2436 Minimum Split Into Subarrays With GCD Greater Than One - Solution Explained/problem-solving.webp
    alt: 2436 Minimum Split Into Subarrays With GCD Greater Than One
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2436. Minimum Split Into Subarrays With GCD Greater Than One](https://leetcode.com/problems/minimum-split-into-subarrays-with-gcd-greater-than-one)


## Description

<p>You are given an array <code>nums</code> consisting of positive integers.</p>

<p>Split the array into <strong>one or more</strong> disjoint subarrays such that:</p>

<ul>
	<li>Each element of the array belongs to <strong>exactly one</strong> subarray, and</li>
	<li>The <strong>GCD</strong> of the elements of each subarray is strictly greater than <code>1</code>.</li>
</ul>

<p>Return <em>the minimum number of subarrays that can be obtained after the split</em>.</p>

<p><strong>Note</strong> that:</p>

<ul>
	<li>The <strong>GCD</strong> of a subarray is the largest positive integer that evenly divides all the elements of the subarray.</li>
	<li>A <strong>subarray</strong> is a contiguous part of the array.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [12,6,3,14,8]
<strong>Output:</strong> 2
<strong>Explanation:</strong> We can split the array into the subarrays: [12,6,3] and [14,8].
- The GCD of 12, 6 and 3 is 3, which is strictly greater than 1.
- The GCD of 14 and 8 is 2, which is strictly greater than 1.
It can be shown that splitting the array into one subarray will make the GCD = 1.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,12,6,14]
<strong>Output:</strong> 1
<strong>Explanation:</strong> We can split the array into only one subarray, which is the whole array.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2000</code></li>
	<li><code>2 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

### Solution 1: Greedy + Mathematics

For each element in the array, if its greatest common divisor (gcd) with the previous element is $1$, then it needs to be the first element of a new subarray. Otherwise, it can be placed in the same subarray with the previous elements.

Therefore, we first initialize a variable $g$, representing the gcd of the current subarray. Initially, $g=0$ and the answer variable $ans=1$.

Next, we traverse the array from front to back, maintaining the gcd $g$ of the current subarray. If the gcd of the current element $x$ and $g$ is $1$, then we need to make the current element the first element of a new subarray. Therefore, the answer increases by $1$, and $g$ is updated to $x$. Otherwise, the current element can be placed in the same subarray with the previous elements. Continue to traverse the array until the traversal ends.

The time complexity is $O(n \times \log m)$, where $n$ and $m$ are the length of the array and the maximum value in the array, respectively. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def minimumSplits(self, nums: List[int]) -> int:
        ans, g = 1, 0
        for x in nums:
            g = gcd(g, x)
            if g == 1:
                ans += 1
                g = x
        return ans
```

```java
class Solution {
    public int minimumSplits(int[] nums) {
        int ans = 1, g = 0;
        for (int x : nums) {
            g = gcd(g, x);
            if (g == 1) {
                ++ans;
                g = x;
            }
        }
        return ans;
    }

    private int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }
}
```

```cpp
class Solution {
public:
    int minimumSplits(vector<int>& nums) {
        int ans = 1, g = 0;
        for (int x : nums) {
            g = gcd(g, x);
            if (g == 1) {
                ++ans;
                g = x;
            }
        }
        return ans;
    }
};
```

```go
func minimumSplits(nums []int) int {
	ans, g := 1, 0
	for _, x := range nums {
		g = gcd(g, x)
		if g == 1 {
			ans++
			g = x
		}
	}
	return ans
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```

```ts
function minimumSplits(nums: number[]): number {
    let ans = 1;
    let g = 0;
    for (const x of nums) {
        g = gcd(g, x);
        if (g == 1) {
            ++ans;
            g = x;
        }
    }
    return ans;
}

function gcd(a: number, b: number): number {
    return b ? gcd(b, a % b) : a;
}
```

<!-- tabs:end -->

<!-- end -->
