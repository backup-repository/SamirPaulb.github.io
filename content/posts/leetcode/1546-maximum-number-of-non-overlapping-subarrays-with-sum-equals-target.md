---
title: 1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target
summary: 1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target LeetCode Solution Explained in all languages", "1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target - Solution Explained/problem-solving.webp
    alt: 1546 Maximum Number of Non Overlapping Subarrays With Sum Equals Target
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1546. Maximum Number of Non-Overlapping Subarrays With Sum Equals Target](https://leetcode.com/problems/maximum-number-of-non-overlapping-subarrays-with-sum-equals-target)


## Description

<p>Given an array <code>nums</code> and an integer <code>target</code>, return <em>the maximum number of <strong>non-empty</strong> <strong>non-overlapping</strong> subarrays such that the sum of values in each subarray is equal to</em> <code>target</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,1,1,1], target = 2
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are 2 non-overlapping subarrays [<strong>1,1</strong>,1,<strong>1,1</strong>] with sum equals to target(2).
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,3,5,1,4,2,-9], target = 6
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are 3 subarrays with sum equal to 6.
([5,1], [4,2], [3,5,1,4,2,-9]) but only the first 2 are non-overlapping.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= target &lt;= 10<sup>6</sup></code></li>
</ul>

## Solutions

### Solution 1: Greedy + Prefix Sum + Hash Table

We traverse the array $nums$, using the method of prefix sum + hash table, to find subarrays with a sum of $target$. If found, we increment the answer by one, then we set the prefix sum to $0$ and continue to traverse the array $nums$ until the entire array is traversed.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array $nums$.

<!-- tabs:start -->

```python
class Solution:
    def maxNonOverlapping(self, nums: List[int], target: int) -> int:
        ans = 0
        i, n = 0, len(nums)
        while i < n:
            s = 0
            vis = {0}
            while i < n:
                s += nums[i]
                if s - target in vis:
                    ans += 1
                    break
                i += 1
                vis.add(s)
            i += 1
        return ans
```

```java
class Solution {
    public int maxNonOverlapping(int[] nums, int target) {
        int ans = 0, n = nums.length;
        for (int i = 0; i < n; ++i) {
            Set<Integer> vis = new HashSet<>();
            int s = 0;
            vis.add(0);
            while (i < n) {
                s += nums[i];
                if (vis.contains(s - target)) {
                    ++ans;
                    break;
                }
                ++i;
                vis.add(s);
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int maxNonOverlapping(vector<int>& nums, int target) {
        int ans = 0, n = nums.size();
        for (int i = 0; i < n; ++i) {
            unordered_set<int> vis{{0}};
            int s = 0;
            while (i < n) {
                s += nums[i];
                if (vis.count(s - target)) {
                    ++ans;
                    break;
                }
                ++i;
                vis.insert(s);
            }
        }
        return ans;
    }
};
```

```go
func maxNonOverlapping(nums []int, target int) (ans int) {
	n := len(nums)
	for i := 0; i < n; i++ {
		s := 0
		vis := map[int]bool{0: true}
		for ; i < n; i++ {
			s += nums[i]
			if vis[s-target] {
				ans++
				break
			}
			vis[s] = true
		}
	}
	return
}
```

```ts
function maxNonOverlapping(nums: number[], target: number): number {
    const n = nums.length;
    let ans = 0;
    for (let i = 0; i < n; ++i) {
        let s = 0;
        const vis: Set<number> = new Set();
        vis.add(0);
        for (; i < n; ++i) {
            s += nums[i];
            if (vis.has(s - target)) {
                ++ans;
                break;
            }
            vis.add(s);
        }
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
