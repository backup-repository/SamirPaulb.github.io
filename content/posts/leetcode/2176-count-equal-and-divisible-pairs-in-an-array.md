---
title: 2176 Count Equal and Divisible Pairs in an Array
summary: 2176 Count Equal and Divisible Pairs in an Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2176 Count Equal and Divisible Pairs in an Array LeetCode Solution Explained in all languages", "2176 Count Equal and Divisible Pairs in an Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2176 Count Equal and Divisible Pairs in an Array - Solution Explained/problem-solving.webp
    alt: 2176 Count Equal and Divisible Pairs in an Array
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2176. Count Equal and Divisible Pairs in an Array](https://leetcode.com/problems/count-equal-and-divisible-pairs-in-an-array)


## Description

Given a <strong>0-indexed</strong> integer array <code>nums</code> of length <code>n</code> and an integer <code>k</code>, return <em>the <strong>number of pairs</strong></em> <code>(i, j)</code> <em>where</em> <code>0 &lt;= i &lt; j &lt; n</code>, <em>such that</em> <code>nums[i] == nums[j]</code> <em>and</em> <code>(i \* j)</code> <em>is divisible by</em> <code>k</code>.

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,1,2,2,2,1,3], k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong>
There are 4 pairs that meet all the requirements:
- nums[0] == nums[6], and 0 * 6 == 0, which is divisible by 2.
- nums[2] == nums[3], and 2 * 3 == 6, which is divisible by 2.
- nums[2] == nums[4], and 2 * 4 == 8, which is divisible by 2.
- nums[3] == nums[4], and 3 * 4 == 12, which is divisible by 2.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4], k = 1
<strong>Output:</strong> 0
<strong>Explanation:</strong> Since no value in nums is repeated, there are no pairs (i,j) that meet all the requirements.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i], k &lt;= 100</code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def countPairs(self, nums: List[int], k: int) -> int:
        n = len(nums)
        return sum(
            nums[i] == nums[j] and (i * j) % k == 0
            for i in range(n)
            for j in range(i + 1, n)
        )
```

```java
class Solution {
    public int countPairs(int[] nums, int k) {
        int n = nums.length;
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                if (nums[i] == nums[j] && (i * j) % k == 0) {
                    ++ans;
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
    int countPairs(vector<int>& nums, int k) {
        int n = nums.size();
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                if (nums[i] == nums[j] && (i * j) % k == 0) ++ans;
            }
        }
        return ans;
    }
};
```

```go
func countPairs(nums []int, k int) int {
	n := len(nums)
	ans := 0
	for i, v := range nums {
		for j := i + 1; j < n; j++ {
			if v == nums[j] && (i*j)%k == 0 {
				ans++
			}
		}
	}
	return ans
}
```

```ts
function countPairs(nums: number[], k: number): number {
    const n = nums.length;
    let ans = 0;
    for (let i = 0; i < n - 1; i++) {
        for (let j = i + 1; j < n; j++) {
            if (nums[i] === nums[j] && (i * j) % k === 0) {
                ans++;
            }
        }
    }
    return ans;
}
```

```rust
impl Solution {
    pub fn count_pairs(nums: Vec<i32>, k: i32) -> i32 {
        let k = k as usize;
        let n = nums.len();
        let mut ans = 0;
        for i in 0..n - 1 {
            for j in i + 1..n {
                if nums[i] == nums[j] && (i * j) % k == 0 {
                    ans += 1;
                }
            }
        }
        ans
    }
}
```

```c
int countPairs(int* nums, int numsSize, int k) {
    int ans = 0;
    for (int i = 0; i < numsSize - 1; i++) {
        for (int j = i + 1; j < numsSize; j++) {
            if (nums[i] == nums[j] && i * j % k == 0) {
                ans++;
            }
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
