---
title: 1424 Diagonal Traverse II
summary: 1424 Diagonal Traverse II LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1424 Diagonal Traverse II LeetCode Solution Explained in all languages", "1424 Diagonal Traverse II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1424 Diagonal Traverse II - Solution Explained/problem-solving.webp
    alt: 1424 Diagonal Traverse II
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1424. Diagonal Traverse II](https://leetcode.com/problems/diagonal-traverse-ii)


## Description

<p>Given a 2D integer array <code>nums</code>, return <em>all elements of </em><code>nums</code><em> in diagonal order as shown in the below images</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1424.Diagonal%20Traverse%20II/images/sample_1_1784.png" style="width: 158px; height: 143px;" />
<pre>
<strong>Input:</strong> nums = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [1,4,2,7,5,3,8,6,9]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1424.Diagonal%20Traverse%20II/images/sample_2_1784.png" style="width: 230px; height: 177px;" />
<pre>
<strong>Input:</strong> nums = [[1,2,3,4,5],[6,7],[8],[9,10,11],[12,13,14,15,16]]
<strong>Output:</strong> [1,6,2,8,7,3,9,4,12,10,5,13,11,14,15,16]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i].length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= sum(nums[i].length) &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i][j] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findDiagonalOrder(self, nums: List[List[int]]) -> List[int]:
        arr = []
        for i, row in enumerate(nums):
            for j, v in enumerate(row):
                arr.append((i + j, j, v))
        arr.sort()
        return [v[2] for v in arr]
```

```java
class Solution {
    public int[] findDiagonalOrder(List<List<Integer>> nums) {
        List<int[]> arr = new ArrayList<>();
        for (int i = 0; i < nums.size(); ++i) {
            for (int j = 0; j < nums.get(i).size(); ++j) {
                arr.add(new int[] {i + j, j, nums.get(i).get(j)});
            }
        }
        arr.sort((a, b) -> a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]);
        int[] ans = new int[arr.size()];
        for (int i = 0; i < arr.size(); ++i) {
            ans[i] = arr.get(i)[2];
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& nums) {
        vector<tuple<int, int, int>> arr;
        for (int i = 0; i < nums.size(); ++i) {
            for (int j = 0; j < nums[i].size(); ++j) {
                arr.push_back({i + j, j, nums[i][j]});
            }
        }
        sort(arr.begin(), arr.end());
        vector<int> ans;
        for (auto& e : arr) {
            ans.push_back(get<2>(e));
        }
        return ans;
    }
};
```

```go
func findDiagonalOrder(nums [][]int) []int {
	arr := [][]int{}
	for i, row := range nums {
		for j, v := range row {
			arr = append(arr, []int{i + j, j, v})
		}
	}
	sort.Slice(arr, func(i, j int) bool {
		if arr[i][0] == arr[j][0] {
			return arr[i][1] < arr[j][1]
		}
		return arr[i][0] < arr[j][0]
	})
	ans := []int{}
	for _, v := range arr {
		ans = append(ans, v[2])
	}
	return ans
}
```

```cs
public class Solution {
    public int[] FindDiagonalOrder(IList<IList<int>> nums) {
        List<int[]> arr = new List<int[]>();
        for (int i = 0; i < nums.Count; ++i) {
            for (int j = 0; j < nums[i].Count; ++j) {
                arr.Add(new int[] { i + j, j, nums[i][j] });
            }
        }
        arr.Sort((a, b) => a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]);
        int[] ans = new int[arr.Count];
        for (int i = 0; i < arr.Count; ++i) {
            ans[i] = arr[i][2];
        }
        return ans;
    }
}
```

<!-- tabs:end -->

<!-- end -->
