---
title: 2012 Sum of Beauty in the Array
summary: 2012 Sum of Beauty in the Array LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2012 Sum of Beauty in the Array LeetCode Solution Explained in all languages", "2012 Sum of Beauty in the Array", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2012 Sum of Beauty in the Array - Solution Explained/problem-solving.webp
    alt: 2012 Sum of Beauty in the Array
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2012. Sum of Beauty in the Array](https://leetcode.com/problems/sum-of-beauty-in-the-array)


## Description

<p>You are given a <strong>0-indexed</strong> integer array <code>nums</code>. For each index <code>i</code> (<code>1 &lt;= i &lt;= nums.length - 2</code>) the <strong>beauty</strong> of <code>nums[i]</code> equals:</p>

<ul>
	<li><code>2</code>, if <code>nums[j] &lt; nums[i] &lt; nums[k]</code>, for <strong>all</strong> <code>0 &lt;= j &lt; i</code> and for <strong>all</strong> <code>i &lt; k &lt;= nums.length - 1</code>.</li>
	<li><code>1</code>, if <code>nums[i - 1] &lt; nums[i] &lt; nums[i + 1]</code>, and the previous condition is not satisfied.</li>
	<li><code>0</code>, if none of the previous conditions holds.</li>
</ul>

<p>Return<em> the <strong>sum of beauty</strong> of all </em><code>nums[i]</code><em> where </em><code>1 &lt;= i &lt;= nums.length - 2</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 1:
- The beauty of nums[1] equals 2.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,4,6,4]
<strong>Output:</strong> 1
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 2:
- The beauty of nums[1] equals 1.
- The beauty of nums[2] equals 0.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> For each index i in the range 1 &lt;= i &lt;= 1:
- The beauty of nums[1] equals 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1: Preprocessing Right Minimum + Traversing to Maintain Left Maximum

We can preprocess the right minimum array $right$, where $right[i]$ represents the minimum value in $nums[i..n-1]$.

Then we traverse the array $nums$ from left to right, while maintaining the maximum value $l$ on the left. For each position $i$, we judge whether $l < nums[i] < right[i + 1]$ holds. If it does, we add $2$ to the answer. Otherwise, we judge whether $nums[i - 1] < nums[i] < nums[i + 1]$ holds. If it does, we add $1$ to the answer.

After the traversal, we can get the answer.

The time complexity is $O(n)$, and the space complexity is $O(n)$. Here, $n$ is the length of the array $nums$.

<!-- tabs:start -->

```python
class Solution:
    def sumOfBeauties(self, nums: List[int]) -> int:
        n = len(nums)
        right = [nums[-1]] * n
        for i in range(n - 2, -1, -1):
            right[i] = min(right[i + 1], nums[i])
        ans = 0
        l = nums[0]
        for i in range(1, n - 1):
            r = right[i + 1]
            if l < nums[i] < r:
                ans += 2
            elif nums[i - 1] < nums[i] < nums[i + 1]:
                ans += 1
            l = max(l, nums[i])
        return ans
```

```java
class Solution {
    public int sumOfBeauties(int[] nums) {
        int n = nums.length;
        int[] right = new int[n];
        right[n - 1] = nums[n - 1];
        for (int i = n - 2; i > 0; --i) {
            right[i] = Math.min(right[i + 1], nums[i]);
        }
        int ans = 0;
        int l = nums[0];
        for (int i = 1; i < n - 1; ++i) {
            int r = right[i + 1];
            if (l < nums[i] && nums[i] < r) {
                ans += 2;
            } else if (nums[i - 1] < nums[i] && nums[i] < nums[i + 1]) {
                ans += 1;
            }
            l = Math.max(l, nums[i]);
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int sumOfBeauties(vector<int>& nums) {
        int n = nums.size();
        vector<int> right(n, nums[n - 1]);
        for (int i = n - 2; i; --i) {
            right[i] = min(right[i + 1], nums[i]);
        }
        int ans = 0;
        for (int i = 1, l = nums[0]; i < n - 1; ++i) {
            int r = right[i + 1];
            if (l < nums[i] && nums[i] < r) {
                ans += 2;
            } else if (nums[i - 1] < nums[i] && nums[i] < nums[i + 1]) {
                ans += 1;
            }
            l = max(l, nums[i]);
        }
        return ans;
    }
};
```

```go
func sumOfBeauties(nums []int) (ans int) {
	n := len(nums)
	right := make([]int, n)
	right[n-1] = nums[n-1]
	for i := n - 2; i > 0; i-- {
		right[i] = min(right[i+1], nums[i])
	}
	for i, l := 1, nums[0]; i < n-1; i++ {
		r := right[i+1]
		if l < nums[i] && nums[i] < r {
			ans += 2
		} else if nums[i-1] < nums[i] && nums[i] < nums[i+1] {
			ans++
		}
		l = max(l, nums[i])
	}
	return
}
```

```ts
function sumOfBeauties(nums: number[]): number {
    const n = nums.length;
    const right: number[] = Array(n).fill(nums[n - 1]);
    for (let i = n - 2; i; --i) {
        right[i] = Math.min(right[i + 1], nums[i]);
    }
    let ans = 0;
    for (let i = 1, l = nums[0]; i < n - 1; ++i) {
        const r = right[i + 1];
        if (l < nums[i] && nums[i] < r) {
            ans += 2;
        } else if (nums[i - 1] < nums[i] && nums[i] < nums[i + 1]) {
            ans += 1;
        }
        l = Math.max(l, nums[i]);
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
