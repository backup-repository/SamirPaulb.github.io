---
title: 2319 Check if Matrix Is X Matrix
summary: 2319 Check if Matrix Is X Matrix LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2319 Check if Matrix Is X Matrix LeetCode Solution Explained in all languages", "2319 Check if Matrix Is X Matrix", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2319 Check if Matrix Is X Matrix - Solution Explained/problem-solving.webp
    alt: 2319 Check if Matrix Is X Matrix
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2319. Check if Matrix Is X-Matrix](https://leetcode.com/problems/check-if-matrix-is-x-matrix)


## Description

<p>A square matrix is said to be an <strong>X-Matrix</strong> if <strong>both</strong> of the following conditions hold:</p>

<ol>
	<li>All the elements in the diagonals of the matrix are <strong>non-zero</strong>.</li>
	<li>All other elements are 0.</li>
</ol>

<p>Given a 2D integer array <code>grid</code> of size <code>n x n</code> representing a square matrix, return <code>true</code><em> if </em><code>grid</code><em> is an X-Matrix</em>. Otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/2319.Check%20if%20Matrix%20Is%20X-Matrix/images/ex1.jpg" style="width: 311px; height: 320px;" />
<pre>
<strong>Input:</strong> grid = [[2,0,0,1],[0,3,1,0],[0,5,2,0],[4,0,0,2]]
<strong>Output:</strong> true
<strong>Explanation:</strong> Refer to the diagram above. 
An X-Matrix should have the green elements (diagonals) be non-zero and the red elements be 0.
Thus, grid is an X-Matrix.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/2319.Check%20if%20Matrix%20Is%20X-Matrix/images/ex2.jpg" style="width: 238px; height: 246px;" />
<pre>
<strong>Input:</strong> grid = [[5,7,0],[0,3,1],[0,5,0]]
<strong>Output:</strong> false
<strong>Explanation:</strong> Refer to the diagram above.
An X-Matrix should have the green elements (diagonals) be non-zero and the red elements be 0.
Thus, grid is not an X-Matrix.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length == grid[i].length</code></li>
	<li><code>3 &lt;= n &lt;= 100</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 10<sup>5</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def checkXMatrix(self, grid: List[List[int]]) -> bool:
        for i, row in enumerate(grid):
            for j, v in enumerate(row):
                if i == j or i + j == len(grid) - 1:
                    if v == 0:
                        return False
                elif v:
                    return False
        return True
```

```java
class Solution {
    public boolean checkXMatrix(int[][] grid) {
        int n = grid.length;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (i == j || i + j == n - 1) {
                    if (grid[i][j] == 0) {
                        return false;
                    }
                } else if (grid[i][j] != 0) {
                    return false;
                }
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool checkXMatrix(vector<vector<int>>& grid) {
        int n = grid.size();
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (i == j || i + j == n - 1) {
                    if (!grid[i][j]) {
                        return false;
                    }
                } else if (grid[i][j]) {
                    return false;
                }
            }
        }
        return true;
    }
};
```

```go
func checkXMatrix(grid [][]int) bool {
	for i, row := range grid {
		for j, v := range row {
			if i == j || i+j == len(row)-1 {
				if v == 0 {
					return false
				}
			} else if v != 0 {
				return false
			}
		}
	}
	return true
}
```

```ts
function checkXMatrix(grid: number[][]): boolean {
    const n = grid.length;
    for (let i = 0; i < n; ++i) {
        for (let j = 0; j < n; ++j) {
            if (i == j || i + j == n - 1) {
                if (!grid[i][j]) {
                    return false;
                }
            } else if (grid[i][j]) {
                return false;
            }
        }
    }
    return true;
}
```

```rust
impl Solution {
    pub fn check_x_matrix(grid: Vec<Vec<i32>>) -> bool {
        let n = grid.len();
        for i in 0..n {
            for j in 0..n {
                if i == j || i + j == n - 1 {
                    if grid[i][j] == 0 {
                        return false;
                    }
                } else if grid[i][j] != 0 {
                    return false;
                }
            }
        }
        true
    }
}
```

```cs
public class Solution {
    public bool CheckXMatrix(int[][] grid) {
        int n = grid.Length;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (i == j || i + j == n - 1) {
                    if (grid[i][j] == 0) {
                        return false;
                    }
                } else if (grid[i][j] != 0) {
                    return false;
                }
            }
        }
        return true;
    }
}
```

```c
bool checkXMatrix(int** grid, int gridSize, int* gridColSize) {
    for (int i = 0; i < gridSize; i++) {
        for (int j = 0; j < gridSize; j++) {
            if (i == j || i + j == gridSize - 1) {
                if (grid[i][j] == 0) {
                    return false;
                }
            } else if (grid[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
```

<!-- tabs:end -->

<!-- end -->
