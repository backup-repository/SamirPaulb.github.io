---
title: 1695 Maximum Erasure Value
summary: 1695 Maximum Erasure Value LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1695 Maximum Erasure Value LeetCode Solution Explained in all languages", "1695 Maximum Erasure Value", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1695 Maximum Erasure Value - Solution Explained/problem-solving.webp
    alt: 1695 Maximum Erasure Value
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1695. Maximum Erasure Value](https://leetcode.com/problems/maximum-erasure-value)


## Description

<p>You are given an array of positive integers <code>nums</code> and want to erase a subarray containing&nbsp;<strong>unique elements</strong>. The <strong>score</strong> you get by erasing the subarray is equal to the <strong>sum</strong> of its elements.</p>

<p>Return <em>the <strong>maximum score</strong> you can get by erasing <strong>exactly one</strong> subarray.</em></p>

<p>An array <code>b</code> is called to be a <span class="tex-font-style-it">subarray</span> of <code>a</code> if it forms a contiguous subsequence of <code>a</code>, that is, if it is equal to <code>a[l],a[l+1],...,a[r]</code> for some <code>(l,r)</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,2,4,5,6]
<strong>Output:</strong> 17
<strong>Explanation:</strong> The optimal subarray here is [2,4,5,6].
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,2,1,2,5,2,1,2,5]
<strong>Output:</strong> 8
<strong>Explanation:</strong> The optimal subarray here is [5,2,1] or [1,2,5].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1: Array or Hash Table + Prefix Sum

We use an array or hash table $d$ to record the last occurrence of each number, use $s$ to record the prefix sum, and use $j$ to record the left endpoint of the current non-repeating subarray.

We traverse the array, for each number $v$, if $d[v]$ exists, then we update $j$ to $max(j, d[v])$, which ensures that the current non-repeating subarray does not contain $v$. Then we update the answer to $max(ans, s[i] - s[j])$, and finally update $d[v]$ to $i$.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array $nums$.

<!-- tabs:start -->

```python
class Solution:
    def maximumUniqueSubarray(self, nums: List[int]) -> int:
        d = defaultdict(int)
        s = list(accumulate(nums, initial=0))
        ans = j = 0
        for i, v in enumerate(nums, 1):
            j = max(j, d[v])
            ans = max(ans, s[i] - s[j])
            d[v] = i
        return ans
```

```java
class Solution {
    public int maximumUniqueSubarray(int[] nums) {
        int[] d = new int[10001];
        int n = nums.length;
        int[] s = new int[n + 1];
        for (int i = 0; i < n; ++i) {
            s[i + 1] = s[i] + nums[i];
        }
        int ans = 0, j = 0;
        for (int i = 1; i <= n; ++i) {
            int v = nums[i - 1];
            j = Math.max(j, d[v]);
            ans = Math.max(ans, s[i] - s[j]);
            d[v] = i;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maximumUniqueSubarray(vector<int>& nums) {
        int d[10001]{};
        int n = nums.size();
        int s[n + 1];
        s[0] = 0;
        for (int i = 0; i < n; ++i) {
            s[i + 1] = s[i] + nums[i];
        }
        int ans = 0, j = 0;
        for (int i = 1; i <= n; ++i) {
            int v = nums[i - 1];
            j = max(j, d[v]);
            ans = max(ans, s[i] - s[j]);
            d[v] = i;
        }
        return ans;
    }
};
```

```go
func maximumUniqueSubarray(nums []int) (ans int) {
	d := [10001]int{}
	n := len(nums)
	s := make([]int, n+1)
	for i, v := range nums {
		s[i+1] = s[i] + v
	}
	for i, j := 1, 0; i <= n; i++ {
		v := nums[i-1]
		j = max(j, d[v])
		ans = max(ans, s[i]-s[j])
		d[v] = i
	}
	return
}
```

```ts
function maximumUniqueSubarray(nums: number[]): number {
    const m = Math.max(...nums);
    const n = nums.length;
    const s: number[] = Array.from({ length: n + 1 }, () => 0);
    for (let i = 1; i <= n; ++i) {
        s[i] = s[i - 1] + nums[i - 1];
    }
    const d = Array.from({ length: m + 1 }, () => 0);
    let [ans, j] = [0, 0];
    for (let i = 1; i <= n; ++i) {
        j = Math.max(j, d[nums[i - 1]]);
        ans = Math.max(ans, s[i] - s[j]);
        d[nums[i - 1]] = i;
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
