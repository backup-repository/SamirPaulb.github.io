---
title: 0063 Unique Paths II
summary: 0063 Unique Paths II LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0063 Unique Paths II LeetCode Solution Explained in all languages", "0063 Unique Paths II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0063 Unique Paths II - Solution Explained/problem-solving.webp
    alt: 0063 Unique Paths II
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii)


## Description

<p>You are given an <code>m x n</code> integer array <code>grid</code>. There is a robot initially located at the <b>top-left corner</b> (i.e., <code>grid[0][0]</code>). The robot tries to move to the <strong>bottom-right corner</strong> (i.e., <code>grid[m - 1][n - 1]</code>). The robot can only move either down or right at any point in time.</p>

<p>An obstacle and space are marked as <code>1</code> or <code>0</code> respectively in <code>grid</code>. A path that the robot takes cannot include <strong>any</strong> square that is an obstacle.</p>

<p>Return <em>the number of possible unique paths that the robot can take to reach the bottom-right corner</em>.</p>

<p>The testcases are generated so that the answer will be less than or equal to <code>2 * 10<sup>9</sup></code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0063.Unique%20Paths%20II/images/robot1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -&gt; Right -&gt; Down -&gt; Down
2. Down -&gt; Down -&gt; Right -&gt; Right
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0063.Unique%20Paths%20II/images/robot2.jpg" style="width: 162px; height: 162px;" />
<pre>
<strong>Input:</strong> obstacleGrid = [[0,1],[0,0]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == obstacleGrid.length</code></li>
	<li><code>n == obstacleGrid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>obstacleGrid[i][j]</code> is <code>0</code> or <code>1</code>.</li>
</ul>

## Solutions

### Solution 1: Dynamic Programming

We define $dp[i][j]$ to represent the number of paths to reach the grid $(i,j)$.

First, initialize all values in the first column and first row of $dp$, then traverse other rows and columns, there are two cases:

-   If $obstacleGrid[i][j] = 1$, it means the number of paths is $0$, so $dp[i][j] = 0$;
-   If $obstacleGrid[i][j] = 0$, then $dp[i][j] = dp[i - 1][j] + dp[i][j - 1]$.

Finally, return $dp[m - 1][n - 1]$.

The time complexity is $O(m \times n)$, and the space complexity is $O(m \times n)$. Here, $m$ and $n$ are the number of rows and columns of the grid, respectively.

<!-- tabs:start -->

```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        for i in range(m):
            if obstacleGrid[i][0] == 1:
                break
            dp[i][0] = 1
        for j in range(n):
            if obstacleGrid[0][j] == 1:
                break
            dp[0][j] = 1
        for i in range(1, m):
            for j in range(1, n):
                if obstacleGrid[i][j] == 0:
                    dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        return dp[-1][-1]
```

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length, n = obstacleGrid[0].length;
        int[][] dp = new int[m][n];
        for (int i = 0; i < m && obstacleGrid[i][0] == 0; ++i) {
            dp[i][0] = 1;
        }
        for (int j = 0; j < n && obstacleGrid[0][j] == 0; ++j) {
            dp[0][j] = 1;
        }
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (obstacleGrid[i][j] == 0) {
                    dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
                }
            }
        }
        return dp[m - 1][n - 1];
    }
}
```

```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size(), n = obstacleGrid[0].size();
        vector<vector<int>> dp(m, vector<int>(n));
        for (int i = 0; i < m && obstacleGrid[i][0] == 0; ++i) {
            dp[i][0] = 1;
        }
        for (int j = 0; j < n && obstacleGrid[0][j] == 0; ++j) {
            dp[0][j] = 1;
        }
        for (int i = 1; i < m; ++i) {
            for (int j = 1; j < n; ++j) {
                if (obstacleGrid[i][j] == 0) {
                    dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
                }
            }
        }
        return dp[m - 1][n - 1];
    }
};
```

```go
func uniquePathsWithObstacles(obstacleGrid [][]int) int {
	m, n := len(obstacleGrid), len(obstacleGrid[0])
	dp := make([][]int, m)
	for i := 0; i < m; i++ {
		dp[i] = make([]int, n)
	}
	for i := 0; i < m && obstacleGrid[i][0] == 0; i++ {
		dp[i][0] = 1
	}
	for j := 0; j < n && obstacleGrid[0][j] == 0; j++ {
		dp[0][j] = 1
	}
	for i := 1; i < m; i++ {
		for j := 1; j < n; j++ {
			if obstacleGrid[i][j] == 0 {
				dp[i][j] = dp[i-1][j] + dp[i][j-1]
			}
		}
	}
	return dp[m-1][n-1]
}
```

```ts
function uniquePathsWithObstacles(obstacleGrid: number[][]): number {
    const m = obstacleGrid.length;
    const n = obstacleGrid[0].length;
    const dp = Array.from({ length: m }, () => new Array(n).fill(0));
    for (let i = 0; i < m; i++) {
        if (obstacleGrid[i][0] === 1) {
            break;
        }
        dp[i][0] = 1;
    }
    for (let i = 0; i < n; i++) {
        if (obstacleGrid[0][i] === 1) {
            break;
        }
        dp[0][i] = 1;
    }
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            if (obstacleGrid[i][j] === 1) {
                continue;
            }
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
        }
    }
    return dp[m - 1][n - 1];
}
```

```rust
impl Solution {
    pub fn unique_paths_with_obstacles(obstacle_grid: Vec<Vec<i32>>) -> i32 {
        let m = obstacle_grid.len();
        let n = obstacle_grid[0].len();
        if obstacle_grid[0][0] == 1 || obstacle_grid[m - 1][n - 1] == 1 {
            return 0;
        }
        let mut dp = vec![vec![0; n]; m];
        for i in 0..n {
            if obstacle_grid[0][i] == 1 {
                break;
            }
            dp[0][i] = 1;
        }
        for i in 0..m {
            if obstacle_grid[i][0] == 1 {
                break;
            }
            dp[i][0] = 1;
        }
        for i in 1..m {
            for j in 1..n {
                if obstacle_grid[i][j] == 1 {
                    continue;
                }
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        dp[m - 1][n - 1]
    }
}
```

<!-- tabs:end -->

<!-- end -->
