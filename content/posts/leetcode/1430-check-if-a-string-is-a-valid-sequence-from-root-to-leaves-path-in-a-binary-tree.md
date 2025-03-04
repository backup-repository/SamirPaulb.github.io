---
title: 1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree
summary: 1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree LeetCode Solution Explained in all languages", "1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree - Solution Explained/problem-solving.webp
    alt: 1430 Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1430. Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree](https://leetcode.com/problems/check-if-a-string-is-a-valid-sequence-from-root-to-leaves-path-in-a-binary-tree)


## Description

<p>Given a binary tree where each path going from the root to any leaf form a <strong>valid sequence</strong>, check if a given string&nbsp;is a <strong>valid sequence</strong> in such binary tree.&nbsp;</p>

<p>We get the given string from the concatenation of an array of integers <code>arr</code> and the concatenation of all&nbsp;values of the nodes along a path results in a <strong>sequence</strong> in the given binary tree.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/1430.Check%20If%20a%20String%20Is%20a%20Valid%20Sequence%20from%20Root%20to%20Leaves%20Path%20in%20a%20Binary%20Tree/images/leetcode_testcase_1.png" style="width: 333px; height: 250px;" /></strong></p>

<pre>
<strong>Input:</strong> root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,0,1]
<strong>Output:</strong> true
<strong>Explanation: 
</strong>The path 0 -&gt; 1 -&gt; 0 -&gt; 1 is a valid sequence (green color in the figure). 
Other valid sequences are: 
0 -&gt; 1 -&gt; 1 -&gt; 0 
0 -&gt; 0 -&gt; 0
</pre>

<p><strong class="example">Example 2:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/1430.Check%20If%20a%20String%20Is%20a%20Valid%20Sequence%20from%20Root%20to%20Leaves%20Path%20in%20a%20Binary%20Tree/images/leetcode_testcase_2.png" style="width: 333px; height: 250px;" /></strong></p>

<pre>
<strong>Input:</strong> root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,0,1]
<strong>Output:</strong> false 
<strong>Explanation:</strong> The path 0 -&gt; 0 -&gt; 1 does not exist, therefore it is not even a sequence.
</pre>

<p><strong class="example">Example 3:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/1430.Check%20If%20a%20String%20Is%20a%20Valid%20Sequence%20from%20Root%20to%20Leaves%20Path%20in%20a%20Binary%20Tree/images/leetcode_testcase_3.png" style="width: 333px; height: 250px;" /></strong></p>

<pre>
<strong>Input:</strong> root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,1]
<strong>Output:</strong> false
<strong>Explanation: </strong>The path 0 -&gt; 1 -&gt; 1 is a sequence, but it is not a valid sequence.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 5000</code></li>
	<li><code>0 &lt;= arr[i] &lt;= 9</code></li>
	<li>Each node&#39;s value is between [0 - 9].</li>
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
    def isValidSequence(self, root: TreeNode, arr: List[int]) -> bool:
        def dfs(root, u):
            if root is None or root.val != arr[u]:
                return False
            if u == len(arr) - 1:
                return root.left is None and root.right is None
            return dfs(root.left, u + 1) or dfs(root.right, u + 1)

        return dfs(root, 0)
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
    private int[] arr;

    public boolean isValidSequence(TreeNode root, int[] arr) {
        this.arr = arr;
        return dfs(root, 0);
    }

    private boolean dfs(TreeNode root, int u) {
        if (root == null || root.val != arr[u]) {
            return false;
        }
        if (u == arr.length - 1) {
            return root.left == null && root.right == null;
        }
        return dfs(root.left, u + 1) || dfs(root.right, u + 1);
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
    bool isValidSequence(TreeNode* root, vector<int>& arr) {
        function<bool(TreeNode*, int)> dfs = [&](TreeNode* root, int u) -> bool {
            if (!root || root->val != arr[u]) return false;
            if (u == arr.size() - 1) return !root->left && !root->right;
            return dfs(root->left, u + 1) || dfs(root->right, u + 1);
        };
        return dfs(root, 0);
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
func isValidSequence(root *TreeNode, arr []int) bool {
	var dfs func(root *TreeNode, u int) bool
	dfs = func(root *TreeNode, u int) bool {
		if root == nil || root.Val != arr[u] {
			return false
		}
		if u == len(arr)-1 {
			return root.Left == nil && root.Right == nil
		}
		return dfs(root.Left, u+1) || dfs(root.Right, u+1)
	}
	return dfs(root, 0)
}
```

<!-- tabs:end -->

<!-- end -->
