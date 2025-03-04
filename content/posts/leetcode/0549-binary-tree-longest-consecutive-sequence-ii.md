---
title: 0549 Binary Tree Longest Consecutive Sequence II
summary: 0549 Binary Tree Longest Consecutive Sequence II LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0549 Binary Tree Longest Consecutive Sequence II LeetCode Solution Explained in all languages", "0549 Binary Tree Longest Consecutive Sequence II", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0549 Binary Tree Longest Consecutive Sequence II - Solution Explained/problem-solving.webp
    alt: 0549 Binary Tree Longest Consecutive Sequence II
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [549. Binary Tree Longest Consecutive Sequence II](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence-ii)


## Description

<p>Given the <code>root</code> of a binary tree, return <em>the length of the longest consecutive path in the tree</em>.</p>

<p>A consecutive path is a path where the values of the consecutive nodes in the path differ by one. This path can be either increasing or decreasing.</p>

<ul>
	<li>For example, <code>[1,2,3,4]</code> and <code>[4,3,2,1]</code> are both considered valid, but the path <code>[1,2,4,3]</code> is not valid.</li>
</ul>

<p>On the other hand, the path can be in the child-Parent-child order, where not necessarily be parent-child order.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0549.Binary%20Tree%20Longest%20Consecutive%20Sequence%20II/images/consec2-1-tree.jpg" style="width: 207px; height: 183px;" />
<pre>
<strong>Input:</strong> root = [1,2,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The longest consecutive path is [1, 2] or [2, 1].
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0549.Binary%20Tree%20Longest%20Consecutive%20Sequence%20II/images/consec2-2-tree.jpg" style="width: 207px; height: 183px;" />
<pre>
<strong>Input:</strong> root = [2,1,3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The longest consecutive path is [1, 2, 3] or [3, 2, 1].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 3 * 10<sup>4</sup>]</code>.</li>
	<li><code>-3 * 10<sup>4</sup> &lt;= Node.val &lt;= 3 * 10<sup>4</sup></code></li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def longestConsecutive(self, root: TreeNode) -> int:
        def dfs(root):
            if root is None:
                return [0, 0]
            nonlocal ans
            incr = decr = 1
            i1, d1 = dfs(root.left)
            i2, d2 = dfs(root.right)
            if root.left:
                if root.left.val + 1 == root.val:
                    incr = i1 + 1
                if root.left.val - 1 == root.val:
                    decr = d1 + 1
            if root.right:
                if root.right.val + 1 == root.val:
                    incr = max(incr, i2 + 1)
                if root.right.val - 1 == root.val:
                    decr = max(decr, d2 + 1)
            ans = max(ans, incr + decr - 1)
            return [incr, decr]

        ans = 0
        dfs(root)
        return ans
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    private int ans;

    public int longestConsecutive(TreeNode root) {
        ans = 0;
        dfs(root);
        return ans;
    }

    private int[] dfs(TreeNode root) {
        if (root == null) {
            return new int[] {0, 0};
        }
        int incr = 1, decr = 1;
        int[] left = dfs(root.left);
        int[] right = dfs(root.right);
        if (root.left != null) {
            if (root.left.val + 1 == root.val) {
                incr = left[0] + 1;
            }
            if (root.left.val - 1 == root.val) {
                decr = left[1] + 1;
            }
        }
        if (root.right != null) {
            if (root.right.val + 1 == root.val) {
                incr = Math.max(incr, right[0] + 1);
            }
            if (root.right.val - 1 == root.val) {
                decr = Math.max(decr, right[1] + 1);
            }
        }
        ans = Math.max(ans, incr + decr - 1);
        return new int[] {incr, decr};
    }
}
```

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int ans;

    int longestConsecutive(TreeNode* root) {
        ans = 0;
        dfs(root);
        return ans;
    }

    vector<int> dfs(TreeNode* root) {
        if (!root) return {0, 0};
        int incr = 1, decr = 1;
        auto left = dfs(root->left);
        auto right = dfs(root->right);
        if (root->left) {
            if (root->left->val + 1 == root->val) incr = left[0] + 1;
            if (root->left->val - 1 == root->val) decr = left[1] + 1;
        }
        if (root->right) {
            if (root->right->val + 1 == root->val) incr = max(incr, right[0] + 1);
            if (root->right->val - 1 == root->val) decr = max(decr, right[1] + 1);
        }
        ans = max(ans, incr + decr - 1);
        return {incr, decr};
    }
};
```

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func longestConsecutive(root *TreeNode) int {
	ans := 0
	var dfs func(root *TreeNode) []int
	dfs = func(root *TreeNode) []int {
		if root == nil {
			return []int{0, 0}
		}
		incr, decr := 1, 1
		left := dfs(root.Left)
		right := dfs(root.Right)
		if root.Left != nil {
			if root.Left.Val+1 == root.Val {
				incr = left[0] + 1
			}
			if root.Left.Val-1 == root.Val {
				decr = left[1] + 1
			}
		}
		if root.Right != nil {
			if root.Right.Val+1 == root.Val {
				incr = max(incr, right[0]+1)
			}
			if root.Right.Val-1 == root.Val {
				decr = max(decr, right[1]+1)
			}
		}
		ans = max(ans, incr+decr-1)
		return []int{incr, decr}
	}
	dfs(root)
	return ans
}
```

<!-- tabs:end -->

<!-- end -->
