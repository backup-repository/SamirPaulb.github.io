---
title: 1886 Determine Whether Matrix Can Be Obtained By Rotation
summary: 1886 Determine Whether Matrix Can Be Obtained By Rotation LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1886 Determine Whether Matrix Can Be Obtained By Rotation LeetCode Solution Explained in all languages", "1886 Determine Whether Matrix Can Be Obtained By Rotation", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1886 Determine Whether Matrix Can Be Obtained By Rotation - Solution Explained/problem-solving.webp
    alt: 1886 Determine Whether Matrix Can Be Obtained By Rotation
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1886. Determine Whether Matrix Can Be Obtained By Rotation](https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation)


## Description

<p>Given two <code>n x n</code> binary matrices <code>mat</code> and <code>target</code>, return <code>true</code><em> if it is possible to make </em><code>mat</code><em> equal to </em><code>target</code><em> by <strong>rotating</strong> </em><code>mat</code><em> in <strong>90-degree increments</strong>, or </em><code>false</code><em> otherwise.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1886.Determine%20Whether%20Matrix%20Can%20Be%20Obtained%20By%20Rotation/images/grid3.png" style="width: 301px; height: 121px;" />
<pre>
<strong>Input:</strong> mat = [[0,1],[1,0]], target = [[1,0],[0,1]]
<strong>Output:</strong> true
<strong>Explanation: </strong>We can rotate mat 90 degrees clockwise to make mat equal target.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1886.Determine%20Whether%20Matrix%20Can%20Be%20Obtained%20By%20Rotation/images/grid4.png" style="width: 301px; height: 121px;" />
<pre>
<strong>Input:</strong> mat = [[0,1],[1,1]], target = [[1,0],[0,1]]
<strong>Output:</strong> false
<strong>Explanation:</strong> It is impossible to make mat equal to target by rotating mat.
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1886.Determine%20Whether%20Matrix%20Can%20Be%20Obtained%20By%20Rotation/images/grid4.png" style="width: 661px; height: 184px;" />
<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,0],[1,1,1]], target = [[1,1,1],[0,1,0],[0,0,0]]
<strong>Output:</strong> true
<strong>Explanation: </strong>We can rotate mat 90 degrees clockwise two times to make mat equal target.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == mat.length == target.length</code></li>
	<li><code>n == mat[i].length == target[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 10</code></li>
	<li><code>mat[i][j]</code> and <code>target[i][j]</code> are either <code>0</code> or <code>1</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def findRotation(self, mat: List[List[int]], target: List[List[int]]) -> bool:
        def rotate(matrix):
            n = len(matrix)
            for i in range(n // 2):
                for j in range(i, n - 1 - i):
                    t = matrix[i][j]
                    matrix[i][j] = matrix[n - j - 1][i]
                    matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1]
                    matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1]
                    matrix[j][n - i - 1] = t

        for _ in range(4):
            if mat == target:
                return True
            rotate(mat)
        return False
```

```java
class Solution {
    public boolean findRotation(int[][] mat, int[][] target) {
        int times = 4;
        while (times-- > 0) {
            if (equals(mat, target)) {
                return true;
            }
            rotate(mat);
        }
        return false;
    }

    private void rotate(int[][] matrix) {
        int n = matrix.length;
        for (int i = 0; i < n / 2; ++i) {
            for (int j = i; j < n - 1 - i; ++j) {
                int t = matrix[i][j];
                matrix[i][j] = matrix[n - j - 1][i];
                matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1];
                matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1];
                matrix[j][n - i - 1] = t;
            }
        }
    }

    private boolean equals(int[][] nums1, int[][] nums2) {
        int n = nums1.length;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (nums1[i][j] != nums2[i][j]) {
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
    bool findRotation(vector<vector<int>>& mat, vector<vector<int>>& target) {
        int n = mat.size();
        for (int k = 0; k < 4; ++k) {
            vector<vector<int>> g(n, vector<int>(n));
            for (int i = 0; i < n; ++i)
                for (int j = 0; j < n; ++j)
                    g[i][j] = mat[j][n - i - 1];
            if (g == target) return true;
            mat = g;
        }
        return false;
    }
};
```

```go
func findRotation(mat [][]int, target [][]int) bool {
	n := len(mat)
	for k := 0; k < 4; k++ {
		g := make([][]int, n)
		for i := range g {
			g[i] = make([]int, n)
		}
		for i := 0; i < n; i++ {
			for j := 0; j < n; j++ {
				g[i][j] = mat[j][n-i-1]
			}
		}
		if equals(g, target) {
			return true
		}
		mat = g
	}
	return false
}

func equals(a, b [][]int) bool {
	for i, row := range a {
		for j, v := range row {
			if v != b[i][j] {
				return false
			}
		}
	}
	return true
}
```

```ts
function findRotation(mat: number[][], target: number[][]): boolean {
    for (let k = 0; k < 4; k++) {
        rotate(mat);
        if (isEqual(mat, target)) {
            return true;
        }
    }
    return false;
}

function isEqual(A: number[][], B: number[][]) {
    const n = A.length;
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < n; j++) {
            if (A[i][j] !== B[i][j]) {
                return false;
            }
        }
    }
    return true;
}

function rotate(matrix: number[][]): void {
    const n = matrix.length;
    for (let i = 0; i < n >> 1; i++) {
        for (let j = 0; j < (n + 1) >> 1; j++) {
            [
                matrix[i][j],
                matrix[n - 1 - j][i],
                matrix[n - 1 - i][n - 1 - j],
                matrix[j][n - 1 - i],
            ] = [
                matrix[n - 1 - j][i],
                matrix[n - 1 - i][n - 1 - j],
                matrix[j][n - 1 - i],
                matrix[i][j],
            ];
        }
    }
}
```

```rust
impl Solution {
    pub fn find_rotation(mat: Vec<Vec<i32>>, target: Vec<Vec<i32>>) -> bool {
        let n = mat.len();
        let mut is_equal = [true; 4];
        for i in 0..n {
            for j in 0..n {
                if is_equal[0] && mat[i][j] != target[i][j] {
                    is_equal[0] = false;
                }
                if is_equal[1] && mat[i][j] != target[j][n - 1 - i] {
                    is_equal[1] = false;
                }
                if is_equal[2] && mat[i][j] != target[n - 1 - i][n - 1 - j] {
                    is_equal[2] = false;
                }
                if is_equal[3] && mat[i][j] != target[n - 1 - j][i] {
                    is_equal[3] = false;
                }
            }
        }
        is_equal.into_iter().any(|&v| v)
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
class Solution:
    def findRotation(self, mat: List[List[int]], target: List[List[int]]) -> bool:
        for _ in range(4):
            mat = [list(col) for col in zip(*mat[::-1])]
            if mat == target:
                return True
        return False
```

```java
class Solution {
    public boolean findRotation(int[][] mat, int[][] target) {
        int n = mat.length;
        for (int k = 0; k < 4; ++k) {
            int[][] g = new int[n][n];
            for (int i = 0; i < n; ++i) {
                for (int j = 0; j < n; ++j) {
                    g[i][j] = mat[j][n - i - 1];
                }
            }
            if (equals(g, target)) {
                return true;
            }
            mat = g;
        }
        return false;
    }

    private boolean equals(int[][] a, int[][] b) {
        int n = a.length;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (a[i][j] != b[i][j]) {
                    return false;
                }
            }
        }
        return true;
    }
}
```

<!-- tabs:end -->

<!-- end -->
