---
title: 1302 Deepest Leaves Sum
summary: 1302 Deepest Leaves Sum LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1302 Deepest Leaves Sum LeetCode Solution Explained in all languages", "1302 Deepest Leaves Sum", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1302 Deepest Leaves Sum - Solution Explained/problem-solving.webp
    alt: 1302 Deepest Leaves Sum
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1302. Deepest Leaves Sum](https://leetcode.com/problems/deepest-leaves-sum)


## Description

Given the <code>root</code> of a binary tree, return <em>the sum of values of its deepest leaves</em>.

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/1302.Deepest%20Leaves%20Sum/images/1483_ex1.png" style="width: 273px; height: 265px;" />
<pre>
<strong>Input:</strong> root = [1,2,3,4,5,null,6,7,null,null,null,null,8]
<strong>Output:</strong> 15
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [6,7,8,2,7,1,3,9,null,1,4,null,null,null,5]
<strong>Output:</strong> 19
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>1 &lt;= Node.val &lt;= 100</code></li>
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
    def deepestLeavesSum(self, root: Optional[TreeNode]) -> int:
        q = deque([root])
        while q:
            ans = 0
            for _ in range(len(q)):
                root = q.popleft()
                ans += root.val
                if root.left:
                    q.append(root.left)
                if root.right:
                    q.append(root.right)
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
    public int deepestLeavesSum(TreeNode root) {
        Deque<TreeNode> q = new ArrayDeque<>();
        q.offer(root);
        int ans = 0;
        while (!q.isEmpty()) {
            ans = 0;
            for (int n = q.size(); n > 0; --n) {
                root = q.pollFirst();
                ans += root.val;
                if (root.left != null) {
                    q.offer(root.left);
                }
                if (root.right != null) {
                    q.offer(root.right);
                }
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
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int deepestLeavesSum(TreeNode* root) {
        int ans = 0;
        queue<TreeNode*> q{{root}};
        while (!q.empty()) {
            ans = 0;
            for (int n = q.size(); n; --n) {
                root = q.front();
                q.pop();
                ans += root->val;
                if (root->left) q.push(root->left);
                if (root->right) q.push(root->right);
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
func deepestLeavesSum(root *TreeNode) int {
	q := []*TreeNode{root}
	ans := 0
	for len(q) > 0 {
		ans = 0
		for n := len(q); n > 0; n-- {
			root = q[0]
			q = q[1:]
			ans += root.Val
			if root.Left != nil {
				q = append(q, root.Left)
			}
			if root.Right != nil {
				q = append(q, root.Right)
			}
		}
	}
	return ans
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

function deepestLeavesSum(root: TreeNode | null): number {
    const queue = [root];
    let res = 0;
    while (queue.length !== 0) {
        const n = queue.length;
        let sum = 0;
        for (let i = 0; i < n; i++) {
            const { val, left, right } = queue.shift();
            sum += val;
            left && queue.push(left);
            right && queue.push(right);
        }
        res = sum;
    }
    return res;
}
```

```rust
// Definition for a binary tree node.
// #[derive(Debug, PartialEq, Eq)]
// pub struct TreeNode {
//   pub val: i32,
//   pub left: Option<Rc<RefCell<TreeNode>>>,
//   pub right: Option<Rc<RefCell<TreeNode>>>,
// }
//
// impl TreeNode {
//   #[inline]
//   pub fn new(val: i32) -> Self {
//     TreeNode {
//       val,
//       left: None,
//       right: None
//     }
//   }
// }
use std::rc::Rc;
use std::cell::RefCell;
impl Solution {
    fn dfs(root: &Option<Rc<RefCell<TreeNode>>>, depth: i32, max_depth: &mut i32, res: &mut i32) {
        if let Some(node) = root {
            let node = node.borrow();
            if node.left.is_none() && node.right.is_none() {
                if depth == *max_depth {
                    *res += node.val;
                } else if depth > *max_depth {
                    *max_depth = depth;
                    *res = node.val;
                }
                return;
            }
            Self::dfs(&node.left, depth + 1, max_depth, res);
            Self::dfs(&node.right, depth + 1, max_depth, res);
        }
    }

    pub fn deepest_leaves_sum(root: Option<Rc<RefCell<TreeNode>>>) -> i32 {
        let mut res = 0;
        let mut max_depth = 0;
        Self::dfs(&root, 0, &mut max_depth, &mut res);
        res
    }
}
```

```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */

void dfs(struct TreeNode* root, int depth, int* maxDepth, int* res) {
    if (!root->left && !root->right) {
        if (depth == *maxDepth) {
            *res += root->val;
        } else if (depth > *maxDepth) {
            *maxDepth = depth;
            *res = root->val;
        }
        return;
    }
    if (root->left) {
        dfs(root->left, depth + 1, maxDepth, res);
    }
    if (root->right) {
        dfs(root->right, depth + 1, maxDepth, res);
    }
}

int deepestLeavesSum(struct TreeNode* root) {
    int res = 0;
    int maxDepth = 0;
    dfs(root, 0, &maxDepth, &res);
    return res;
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def deepestLeavesSum(self, root: Optional[TreeNode]) -> int:
        def dfs(root, i):
            nonlocal ans, mx
            if root is None:
                return
            if i == mx:
                ans += root.val
            elif i > mx:
                ans = root.val
                mx = i
            dfs(root.left, i + 1)
            dfs(root.right, i + 1)

        ans = mx = 0
        dfs(root, 1)
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
    int mx;
    int ans;

    public int deepestLeavesSum(TreeNode root) {
        dfs(root, 1);
        return ans;
    }

    private void dfs(TreeNode root, int i) {
        if (root == null) {
            return;
        }
        if (i > mx) {
            mx = i;
            ans = root.val;
        } else if (i == mx) {
            ans += root.val;
        }
        dfs(root.left, i + 1);
        dfs(root.right, i + 1);
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
    int mx = 0;
    int ans = 0;

    int deepestLeavesSum(TreeNode* root) {
        dfs(root, 1);
        return ans;
    }

    void dfs(TreeNode* root, int i) {
        if (!root) return;
        if (i == mx) {
            ans += root->val;
        } else if (i > mx) {
            mx = i;
            ans = root->val;
        }
        dfs(root->left, i + 1);
        dfs(root->right, i + 1);
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
func deepestLeavesSum(root *TreeNode) int {
	ans, mx := 0, 0
	var dfs func(*TreeNode, int)
	dfs = func(root *TreeNode, i int) {
		if root == nil {
			return
		}
		if i == mx {
			ans += root.Val
		} else if i > mx {
			mx = i
			ans = root.Val
		}
		dfs(root.Left, i+1)
		dfs(root.Right, i+1)
	}
	dfs(root, 1)
	return ans
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

function deepestLeavesSum(root: TreeNode | null): number {
    let res = 0;
    let maxDepath = 0;
    const dfs = ({ val, left, right }: TreeNode, depth: number) => {
        if (left == null && right == null) {
            if (depth === maxDepath) {
                res += val;
            } else if (depth > maxDepath) {
                maxDepath = depth;
                res = val;
            }
            return;
        }
        left && dfs(left, depth + 1);
        right && dfs(right, depth + 1);
    };
    dfs(root, 0);
    return res;
}
```

<!-- tabs:end -->

<!-- end -->
