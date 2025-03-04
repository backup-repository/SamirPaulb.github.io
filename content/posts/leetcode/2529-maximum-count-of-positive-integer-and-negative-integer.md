---
title: 2529 Maximum Count of Positive Integer and Negative Integer
summary: 2529 Maximum Count of Positive Integer and Negative Integer LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2529 Maximum Count of Positive Integer and Negative Integer LeetCode Solution Explained in all languages", "2529 Maximum Count of Positive Integer and Negative Integer", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2529 Maximum Count of Positive Integer and Negative Integer - Solution Explained/problem-solving.webp
    alt: 2529 Maximum Count of Positive Integer and Negative Integer
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2529. Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer)


## Description

<p>Given an array <code>nums</code> sorted in <strong>non-decreasing</strong> order, return <em>the maximum between the number of positive integers and the number of negative integers.</em></p>

<ul>
	<li>In other words, if the number of positive integers in <code>nums</code> is <code>pos</code> and the number of negative integers is <code>neg</code>, then return the maximum of <code>pos</code> and <code>neg</code>.</li>
</ul>

<p><strong>Note</strong> that <code>0</code> is neither positive nor negative.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [-2,-1,-1,1,2,3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are 3 positive integers and 3 negative integers. The maximum count among them is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-3,-2,-1,0,0,1,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are 2 positive integers and 3 negative integers. The maximum count among them is 3.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,20,66,1314]
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 positive integers and 0 negative integers. The maximum count among them is 4.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2000</code></li>
	<li><code>-2000 &lt;= nums[i] &lt;= 2000</code></li>
	<li><code>nums</code> is sorted in a <strong>non-decreasing order</strong>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Can you solve the problem in <code>O(log(n))</code> time complexity?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def maximumCount(self, nums: List[int]) -> int:
        a = sum(v > 0 for v in nums)
        b = sum(v < 0 for v in nums)
        return max(a, b)
```

```java
class Solution {
    public int maximumCount(int[] nums) {
        int a = 0, b = 0;
        for (int v : nums) {
            if (v > 0) {
                ++a;
            }
            if (v < 0) {
                ++b;
            }
        }
        return Math.max(a, b);
    }
}
```

```cpp
class Solution {
public:
    int maximumCount(vector<int>& nums) {
        int a = 0, b = 0;
        for (int& v : nums) {
            if (v > 0) {
                ++a;
            }
            if (v < 0) {
                ++b;
            }
        }
        return max(a, b);
    }
};
```

```go
func maximumCount(nums []int) int {
	a, b := 0, 0
	for _, v := range nums {
		if v > 0 {
			a++
		}
		if v < 0 {
			b++
		}
	}
	return max(a, b)
}
```

```ts
function maximumCount(nums: number[]): number {
    const count = [0, 0];
    for (const num of nums) {
        if (num < 0) {
            count[0]++;
        } else if (num > 0) {
            count[1]++;
        }
    }
    return Math.max(...count);
}
```

```rust
impl Solution {
    pub fn maximum_count(nums: Vec<i32>) -> i32 {
        let mut count = [0, 0];
        for &num in nums.iter() {
            if num < 0 {
                count[0] += 1;
            } else if num > 0 {
                count[1] += 1;
            }
        }
        *count.iter().max().unwrap()
    }
}
```

```c
#define max(a, b) (((a) > (b)) ? (a) : (b))

int maximumCount(int* nums, int numsSize) {
    int count[2] = {0};
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] < 0) {
            count[0]++;
        } else if (nums[i] > 0) {
            count[1]++;
        }
    }
    return max(count[0], count[1]);
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def maximumCount(self, nums: List[int]) -> int:
        a = len(nums) - bisect_left(nums, 1)
        b = bisect_left(nums, 0)
        return max(a, b)
```

```java
class Solution {
    public int maximumCount(int[] nums) {
        int a = nums.length - search(nums, 1);
        int b = search(nums, 0);
        return Math.max(a, b);
    }

    private int search(int[] nums, int x) {
        int left = 0, right = nums.length;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (nums[mid] >= x) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

```cpp
class Solution {
public:
    int maximumCount(vector<int>& nums) {
        int a = nums.end() - lower_bound(nums.begin(), nums.end(), 1);
        int b = lower_bound(nums.begin(), nums.end(), 0) - nums.begin();
        return max(a, b);
    }
};
```

```go
func maximumCount(nums []int) int {
	a := len(nums) - sort.SearchInts(nums, 1)
	b := sort.SearchInts(nums, 0)
	return max(a, b)
}
```

```ts
function maximumCount(nums: number[]): number {
    const search = (target: number) => {
        let left = 0;
        let right = n;
        while (left < right) {
            const mid = (left + right) >>> 1;
            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return left;
    };
    const n = nums.length;
    const i = search(0);
    const j = search(1);
    return Math.max(i, n - j);
}
```

```rust
impl Solution {
    fn search(nums: &Vec<i32>, target: i32) -> usize {
        let mut left = 0;
        let mut right = nums.len();
        while left < right {
            let mid = (left + right) >> 1;
            if nums[mid] < target {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        left
    }

    pub fn maximum_count(nums: Vec<i32>) -> i32 {
        let n = nums.len();
        let i = Self::search(&nums, 0);
        let j = Self::search(&nums, 1);
        i.max(n - j) as i32
    }
}
```

```c
#define max(a, b) (((a) > (b)) ? (a) : (b))

int search(int* nums, int numsSize, int target) {
    int left = 0;
    int right = numsSize;
    while (left < right) {
        int mid = (left + right) >> 1;
        if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return left;
}

int maximumCount(int* nums, int numsSize) {
    int i = search(nums, numsSize, 0);
    int j = search(nums, numsSize, 1);
    return max(i, numsSize - j);
}
```

<!-- tabs:end -->

### Solution 3

<!-- tabs:start -->

```rust
impl Solution {
    pub fn maximum_count(nums: Vec<i32>) -> i32 {
        let mut a = 0;
        let mut b = 0;

        for n in nums {
            if n > 0 {
                a += 1;
            } else if n < 0 {
                b += 1;
            }
        }

        std::cmp::max(a, b)
    }
}
```

<!-- tabs:end -->

<!-- end -->
