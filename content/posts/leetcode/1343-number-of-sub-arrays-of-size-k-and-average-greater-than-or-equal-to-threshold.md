---
title: 1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold
summary: 1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold LeetCode Solution Explained in all languages", "1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold - Solution Explained/problem-solving.webp
    alt: 1343 Number of Sub arrays of Size K and Average Greater than or Equal to Threshold
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1343. Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold)


## Description

<p>Given an array of integers <code>arr</code> and two integers <code>k</code> and <code>threshold</code>, return <em>the number of sub-arrays of size </em><code>k</code><em> and average greater than or equal to </em><code>threshold</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [2,2,2,2,5,5,5,8], k = 3, threshold = 4
<strong>Output:</strong> 3
<strong>Explanation:</strong> Sub-arrays [2,5,5],[5,5,5] and [5,5,8] have averages 4, 5 and 6 respectively. All other sub-arrays of size 3 have averages less than 4 (the threshold).
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [11,13,17,23,29,31,7,5,2,3], k = 3, threshold = 5
<strong>Output:</strong> 6
<strong>Explanation:</strong> The first 6 sub-arrays of size 3 have averages greater than 5. Note that averages are not integers.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= arr[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= arr.length</code></li>
	<li><code>0 &lt;= threshold &lt;= 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def numOfSubarrays(self, arr: List[int], k: int, threshold: int) -> int:
        s = sum(arr[:k])
        ans = int(s / k >= threshold)
        for i in range(k, len(arr)):
            s += arr[i]
            s -= arr[i - k]
            ans += int(s / k >= threshold)
        return ans
```

```java
class Solution {
    public int numOfSubarrays(int[] arr, int k, int threshold) {
        int s = 0;
        for (int i = 0; i < k; ++i) {
            s += arr[i];
        }
        int ans = s / k >= threshold ? 1 : 0;
        for (int i = k; i < arr.length; ++i) {
            s += arr[i] - arr[i - k];
            ans += s / k >= threshold ? 1 : 0;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    int numOfSubarrays(vector<int>& arr, int k, int threshold) {
        int s = accumulate(arr.begin(), arr.begin() + k, 0);
        int ans = s >= k * threshold;
        for (int i = k; i < arr.size(); ++i) {
            s += arr[i] - arr[i - k];
            ans += s >= k * threshold;
        }
        return ans;
    }
};
```

```go
func numOfSubarrays(arr []int, k int, threshold int) (ans int) {
	s := 0
	for _, x := range arr[:k] {
		s += x
	}
	if s/k >= threshold {
		ans++
	}
	for i := k; i < len(arr); i++ {
		s += arr[i] - arr[i-k]
		if s/k >= threshold {
			ans++
		}
	}
	return
}
```

```ts
function numOfSubarrays(arr: number[], k: number, threshold: number): number {
    let s = arr.slice(0, k).reduce((acc, cur) => acc + cur, 0);
    let ans = s >= k * threshold ? 1 : 0;
    for (let i = k; i < arr.length; ++i) {
        s += arr[i] - arr[i - k];
        ans += s >= k * threshold ? 1 : 0;
    }
    return ans;
}
```

<!-- tabs:end -->

<!-- end -->
