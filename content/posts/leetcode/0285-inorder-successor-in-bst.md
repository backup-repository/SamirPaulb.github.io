---
title: 0285 Inorder Successor in BST
summary: 0285 Inorder Successor in BST LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0285 Inorder Successor in BST LeetCode Solution Explained in all languages", "0285 Inorder Successor in BST", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0285 Inorder Successor in BST - Solution Explained/problem-solving.webp
    alt: 0285 Inorder Successor in BST
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [285. Inorder Successor in BST](https://leetcode.com/problems/inorder-successor-in-bst)


## Description

<p>Given the <code>root</code> of a binary search tree and a node <code>p</code> in it, return <em>the in-order successor of that node in the BST</em>. If the given node has no in-order successor in the tree, return <code>null</code>.</p>

<p>The successor of a node <code>p</code> is the node with the smallest key greater than <code>p.val</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0285.Inorder%20Successor%20in%20BST/images/285_example_1.png" style="width: 122px; height: 117px;" />
<pre>
<strong>Input:</strong> root = [2,1,3], p = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong> 1&#39;s in-order successor node is 2. Note that both p and the return value is of TreeNode type.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0285.Inorder%20Successor%20in%20BST/images/285_example_2.png" style="width: 246px; height: 229px;" />
<pre>
<strong>Input:</strong> root = [5,3,6,2,4,null,null,1], p = 6
<strong>Output:</strong> null
<strong>Explanation:</strong> There is no in-order successor of the current node, so the answer is <code>null</code>.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li>All Nodes will have unique values.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


class Solution:
    def inorderSuccessor(self, root: TreeNode, p: TreeNode) -> Optional[TreeNode]:
        ans = None
        while root:
            if root.val > p.val:
                ans = root
                root = root.left
            else:
                root = root.right
        return ans
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        TreeNode ans = null;
        while (root != null) {
            if (root.val > p.val) {
                ans = root;
                root = root.left;
            } else {
                root = root.right;
            }
        }
        return ans;
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
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        TreeNode* ans = nullptr;
        while (root) {
            if (root->val > p->val) {
                ans = root;
                root = root->left;
            } else {
                root = root->right;
            }
        }
        return ans;
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
func inorderSuccessor(root *TreeNode, p *TreeNode) (ans *TreeNode) {
	for root != nil {
		if root.Val > p.Val {
			ans = root
			root = root.Left
		} else {
			root = root.Right
		}
	}
	return
}
```

```ts
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function inorderSuccessor(root: TreeNode | null, p: TreeNode | null): TreeNode | null {
    let ans: TreeNode | null = null;
    while (root) {
        if (root.val > p.val) {
            ans = root;
            root = root.left;
        } else {
            root = root.right;
        }
    }
    return ans;
}
```

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @return {TreeNode}
 */
var inorderSuccessor = function (root, p) {
    let ans = null;
    while (root) {
        if (root.val > p.val) {
            ans = root;
            root = root.left;
        } else {
            root = root.right;
        }
    }
    return ans;
};
```

<!-- tabs:end -->

<!-- end -->
