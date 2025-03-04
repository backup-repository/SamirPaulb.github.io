---
title: 0377 Combination Sum IV
summary: 0377 Combination Sum IV LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0377 Combination Sum IV LeetCode Solution Explained in all languages", "0377 Combination Sum IV", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0377 Combination Sum IV - Solution Explained/problem-solving.webp
    alt: 0377 Combination Sum IV
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [377. Combination Sum IV](https://leetcode.com/problems/combination-sum-iv)


## Description

<p>Given an array of <strong>distinct</strong> integers <code>nums</code> and a target integer <code>target</code>, return <em>the number of possible combinations that add up to</em>&nbsp;<code>target</code>.</p>

<p>The test cases are generated so that the answer can fit in a <strong>32-bit</strong> integer.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3], target = 4
<strong>Output:</strong> 7
<strong>Explanation:</strong>
The possible combination ways are:
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)
Note that different sequences are counted as different combinations.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [9], target = 3
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 200</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li>All the elements of <code>nums</code> are <strong>unique</strong>.</li>
	<li><code>1 &lt;= target &lt;= 1000</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> What if negative numbers are allowed in the given array? How does it change the problem? What limitation we need to add to the question to allow negative numbers?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        f = [1] + [0] * target
        for i in range(1, target + 1):
            for x in nums:
                if i >= x:
                    f[i] += f[i - x]
        return f[target]
```

```java
class Solution {
    public int combinationSum4(int[] nums, int target) {
        int[] f = new int[target + 1];
        f[0] = 1;
        for (int i = 1; i <= target; ++i) {
            for (int x : nums) {
                if (i >= x) {
                    f[i] += f[i - x];
                }
            }
        }
        return f[target];
    }
}
```

```cpp
class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        int f[target + 1];
        memset(f, 0, sizeof(f));
        f[0] = 1;
        for (int i = 1; i <= target; ++i) {
            for (int x : nums) {
                if (i >= x && f[i - x] < INT_MAX - f[i]) {
                    f[i] += f[i - x];
                }
            }
        }
        return f[target];
    }
};
```

```go
func combinationSum4(nums []int, target int) int {
	f := make([]int, target+1)
	f[0] = 1
	for i := 1; i <= target; i++ {
		for _, x := range nums {
			if i >= x {
				f[i] += f[i-x]
			}
		}
	}
	return f[target]
}
```

```ts
function combinationSum4(nums: number[], target: number): number {
    const f: number[] = new Array(target + 1).fill(0);
    f[0] = 1;
    for (let i = 1; i <= target; ++i) {
        for (const x of nums) {
            if (i >= x) {
                f[i] += f[i - x];
            }
        }
    }
    return f[target];
}
```

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var combinationSum4 = function (nums, target) {
    const f = new Array(target + 1).fill(0);
    f[0] = 1;
    for (let i = 1; i <= target; ++i) {
        for (const x of nums) {
            if (i >= x) {
                f[i] += f[i - x];
            }
        }
    }
    return f[target];
};
```

```cs
public class Solution {
    public int CombinationSum4(int[] nums, int target) {
        int[] f = new int[target + 1];
        f[0] = 1;
        for (int i = 1; i <= target; ++i) {
            foreach (int x in nums) {
                if (i >= x) {
                    f[i] += f[i - x];
                }
            }
        }
        return f[target];
    }
}
```

<!-- tabs:end -->

<!-- end -->
