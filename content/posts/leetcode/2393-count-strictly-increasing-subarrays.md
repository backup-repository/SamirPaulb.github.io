---
title: 2393 Count Strictly Increasing Subarrays
summary: 2393 Count Strictly Increasing Subarrays LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2393 Count Strictly Increasing Subarrays LeetCode Solution Explained in all languages", "2393 Count Strictly Increasing Subarrays", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2393 Count Strictly Increasing Subarrays - Solution Explained/problem-solving.webp
    alt: 2393 Count Strictly Increasing Subarrays
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2393. Count Strictly Increasing Subarrays](https://leetcode.com/problems/count-strictly-increasing-subarrays)


## Description

<p>You are given an array <code>nums</code> consisting of <strong>positive</strong> integers.</p>

<p>Return <em>the number of <strong>subarrays</strong> of </em><code>nums</code><em> that are in <strong>strictly increasing</strong> order.</em></p>

<p>A <strong>subarray</strong> is a <strong>contiguous</strong> part of an array.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,5,4,4,6]
<strong>Output:</strong> 10
<strong>Explanation:</strong> The strictly increasing subarrays are the following:
- Subarrays of length 1: [1], [3], [5], [4], [4], [6].
- Subarrays of length 2: [1,3], [3,5], [4,6].
- Subarrays of length 3: [1,3,5].
The total number of subarrays is 6 + 3 + 1 = 10.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5]
<strong>Output:</strong> 15
<strong>Explanation:</strong> Every subarray is strictly increasing. There are 15 possible subarrays that we can take.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def countSubarrays(self, nums: List[int]) -> int:
        ans = i = 0
        while i < len(nums):
            j = i + 1
            while j < len(nums) and nums[j] > nums[j - 1]:
                j += 1
            cnt = j - i
            ans += (1 + cnt) * cnt // 2
            i = j
        return ans
```

```java
class Solution {
    public long countSubarrays(int[] nums) {
        long ans = 0;
        int i = 0, n = nums.length;
        while (i < n) {
            int j = i + 1;
            while (j < n && nums[j] > nums[j - 1]) {
                ++j;
            }
            long cnt = j - i;
            ans += (1 + cnt) * cnt / 2;
            i = j;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    long long countSubarrays(vector<int>& nums) {
        long long ans = 0;
        int i = 0, n = nums.size();
        while (i < n) {
            int j = i + 1;
            while (j < n && nums[j] > nums[j - 1]) {
                ++j;
            }
            int cnt = j - i;
            ans += 1ll * (1 + cnt) * cnt / 2;
            i = j;
        }
        return ans;
    }
};
```

```go
func countSubarrays(nums []int) int64 {
	ans := 0
	i, n := 0, len(nums)
	for i < n {
		j := i + 1
		for j < n && nums[j] > nums[j-1] {
			j++
		}
		cnt := j - i
		ans += (1 + cnt) * cnt / 2
		i = j
	}
	return int64(ans)
}
```

```ts
function countSubarrays(nums: number[]): number {
    let ans = 0;
    let i = 0;
    const n = nums.length;
    while (i < n) {
        let j = i + 1;
        while (j < n && nums[j] > nums[j - 1]) {
            ++j;
        }
        const cnt = j - i;
        ans += ((1 + cnt) * cnt) / 2;
        i = j;
    }
    return ans;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def countSubarrays(self, nums: List[int]) -> int:
        ans = pre = cnt = 0
        for x in nums:
            if pre < x:
                cnt += 1
            else:
                cnt = 1
            pre = x
            ans += cnt
        return ans
```

```java
class Solution {
    public long countSubarrays(int[] nums) {
        long ans = 0;
        int pre = 0, cnt = 0;
        for (int x : nums) {
            if (pre < x) {
                ++cnt;
            } else {
                cnt = 1;
            }
            pre = x;
            ans += cnt;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    long long countSubarrays(vector<int>& nums) {
        long long ans = 0;
        int pre = 0, cnt = 0;
        for (int x : nums) {
            if (pre < x) {
                ++cnt;
            } else {
                cnt = 1;
            }
            ans += cnt;
            pre = x;
        }
        return ans;
    }
};
```

```go
func countSubarrays(nums []int) (ans int64) {
	pre, cnt := 0, 0
	for _, x := range nums {
		if pre < x {
			cnt++
		} else {
			cnt = 1
		}
		ans += int64(cnt)
		pre = x
	}
	return
}
```

```ts
function countSubarrays(nums: number[]): number {
    let ans = 0;
    let pre = 0;
    let cnt = 0;
    for (const x of nums) {
        if (pre < x) {
            ++cnt;
        } else {
            cnt = 1;
        }
        ans += cnt;
        pre = x;
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
