---
title: 0138 Copy List with Random Pointer
summary: 0138 Copy List with Random Pointer LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0138 Copy List with Random Pointer LeetCode Solution Explained in all languages", "0138 Copy List with Random Pointer", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0138 Copy List with Random Pointer - Solution Explained/problem-solving.webp
    alt: 0138 Copy List with Random Pointer
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer)


## Description

<p>A linked list of length <code>n</code> is given such that each node contains an additional random pointer, which could point to any node in the list, or <code>null</code>.</p>

<p>Construct a <a href="https://en.wikipedia.org/wiki/Object_copying#Deep_copy" target="_blank"><strong>deep copy</strong></a> of the list. The deep copy should consist of exactly <code>n</code> <strong>brand new</strong> nodes, where each new node has its value set to the value of its corresponding original node. Both the <code>next</code> and <code>random</code> pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. <strong>None of the pointers in the new list should point to nodes in the original list</strong>.</p>

<p>For example, if there are two nodes <code>X</code> and <code>Y</code> in the original list, where <code>X.random --&gt; Y</code>, then for the corresponding two nodes <code>x</code> and <code>y</code> in the copied list, <code>x.random --&gt; y</code>.</p>

<p>Return <em>the head of the copied linked list</em>.</p>

<p>The linked list is represented in the input/output as a list of <code>n</code> nodes. Each node is represented as a pair of <code>[val, random_index]</code> where:</p>

<ul>
	<li><code>val</code>: an integer representing <code>Node.val</code></li>
	<li><code>random_index</code>: the index of the node (range from <code>0</code> to <code>n-1</code>) that the <code>random</code> pointer points to, or <code>null</code> if it does not point to any node.</li>
</ul>

<p>Your code will <strong>only</strong> be given the <code>head</code> of the original linked list.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0138.Copy%20List%20with%20Random%20Pointer/images/e1.png" style="width: 700px; height: 142px;" />
<pre>
<strong>Input:</strong> head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
<strong>Output:</strong> [[7,null],[13,0],[11,4],[10,2],[1,0]]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://spcdn.pages.dev/leetcode/problems/0138.Copy%20List%20with%20Random%20Pointer/images/e2.png" style="width: 700px; height: 114px;" />
<pre>
<strong>Input:</strong> head = [[1,1],[2,1]]
<strong>Output:</strong> [[1,1],[2,1]]
</pre>

<p><strong class="example">Example 3:</strong></p>

<p><strong><img alt="" src="https://spcdn.pages.dev/leetcode/problems/0138.Copy%20List%20with%20Random%20Pointer/images/e3.png" style="width: 700px; height: 122px;" /></strong></p>

<pre>
<strong>Input:</strong> head = [[3,null],[3,0],[3,null]]
<strong>Output:</strong> [[3,null],[3,0],[3,null]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 1000</code></li>
	<li><code>-10<sup>4</sup> &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
	<li><code>Node.random</code> is <code>null</code> or is pointing to some node in the linked list.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""


class Solution:
    def copyRandomList(self, head: "Node") -> "Node":
        d = {}
        dummy = tail = Node(0)
        cur = head
        while cur:
            tail.next = Node(cur.val)
            tail = tail.next
            d[cur] = tail
            cur = cur.next
        tail = dummy.next
        cur = head
        while cur:
            tail.random = d.get(cur.random)
            tail = tail.next
            cur = cur.next
        return dummy.next
```

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/
class Solution {
    public Node copyRandomList(Node head) {
        Map<Node, Node> d = new HashMap<>();
        Node dummy = new Node(0);
        Node tail = dummy;
        for (Node cur = head; cur != null; cur = cur.next) {
            tail.next = new Node(cur.val);
            tail = tail.next;
            d.put(cur, tail);
        }
        tail = dummy.next;
        for (Node cur = head; cur != null; cur = cur.next) {
            tail.random = d.get(cur.random);
            tail = tail.next;
        }
        return dummy.next;
    }
}
```

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;

    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/
class Solution {
public:
    Node* copyRandomList(Node* head) {
        unordered_map<Node*, Node*> d;
        Node* dummy = new Node(0);
        Node* tail = dummy;
        for (auto cur = head; cur; cur = cur->next) {
            tail->next = new Node(cur->val);
            tail = tail->next;
            d[cur] = tail;
        }
        tail = dummy->next;
        for (auto cur = head; cur; cur = cur->next) {
            tail->random = d[cur->random];
            tail = tail->next;
        }
        return dummy->next;
    }
};
```

```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Next *Node
 *     Random *Node
 * }
 */

func copyRandomList(head *Node) *Node {
	d := map[*Node]*Node{}
	dummy := &Node{}
	tail := dummy
	for cur := head; cur != nil; cur = cur.Next {
		tail.Next = &Node{Val: cur.Val}
		tail = tail.Next
		d[cur] = tail
	}
	tail = dummy.Next
	for cur := head; cur != nil; cur = cur.Next {
		tail.Random = d[cur.Random]
		tail = tail.Next
	}
	return dummy.Next
}
```

```ts
/**
 * Definition for Node.
 * class Node {
 *     val: number
 *     next: Node | null
 *     random: Node | null
 *     constructor(val?: number, next?: Node, random?: Node) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *         this.random = (random===undefined ? null : random)
 *     }
 * }
 */

function copyRandomList(head: Node | null): Node | null {
    const map = new Map<Node, Node>();
    let cur = head;
    while (cur != null) {
        map.set(cur, new Node(cur.val));
        cur = cur.next;
    }
    cur = head;
    while (cur != null) {
        map.get(cur).next = map.get(cur.next) ?? null;
        map.get(cur).random = map.get(cur.random) ?? null;
        cur = cur.next;
    }
    return map.get(head);
}
```

```js
/**
 * // Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

/**
 * @param {Node} head
 * @return {Node}
 */
var copyRandomList = function (head) {
    const d = new Map();
    const dummy = new Node(0);
    let tail = dummy;
    for (let cur = head; cur; cur = cur.next) {
        tail.next = new Node(cur.val);
        tail = tail.next;
        d.set(cur, tail);
    }
    tail = dummy.next;
    for (let cur = head; cur; cur = cur.next) {
        tail.random = d.get(cur.random);
        tail = tail.next;
    }
    return dummy.next;
};
```

```cs
/*
// Definition for a Node.
public class Node {
    public int val;
    public Node next;
    public Node random;

    public Node(int _val) {
        val = _val;
        next = null;
        random = null;
    }
}
*/

public class Solution {
    public Node CopyRandomList(Node head) {
        Dictionary<Node, Node> d = new Dictionary<Node, Node>();
        Node dummy = new Node(0);
        Node tail = dummy;
        for (Node cur = head; cur != null; cur = cur.next) {
            tail.next = new Node(cur.val);
            tail = tail.next;
            d[cur] = tail;
        }
        tail = dummy.next;
        for (Node cur = head; cur != null; cur = cur.next) {
            tail.random = cur.random == null ? null : d[cur.random];
            tail = tail.next;
        }
        return dummy.next;
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""


class Solution:
    def copyRandomList(self, head: "Node") -> "Node":
        if head is None:
            return None
        cur = head
        while cur:
            node = Node(cur.val, cur.next)
            cur.next = node
            cur = node.next

        cur = head
        while cur:
            if cur.random:
                cur.next.random = cur.random.next
            cur = cur.next.next

        ans = head.next
        cur = head
        while cur:
            nxt = cur.next
            if nxt:
                cur.next = nxt.next
            cur = nxt
        return ans
```

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/
class Solution {
    public Node copyRandomList(Node head) {
        if (head == null) {
            return null;
        }
        for (Node cur = head; cur != null;) {
            Node node = new Node(cur.val, cur.next);
            cur.next = node;
            cur = node.next;
        }
        for (Node cur = head; cur != null; cur = cur.next.next) {
            if (cur.random != null) {
                cur.next.random = cur.random.next;
            }
        }
        Node ans = head.next;
        for (Node cur = head; cur != null;) {
            Node nxt = cur.next;
            if (nxt != null) {
                cur.next = nxt.next;
            }
            cur = nxt;
        }
        return ans;
    }
}
```

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;

    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if (!head) {
            return nullptr;
        }
        for (Node* cur = head; cur;) {
            Node* node = new Node(cur->val);
            node->next = cur->next;
            cur->next = node;
            cur = node->next;
        }
        for (Node* cur = head; cur; cur = cur->next->next) {
            if (cur->random) {
                cur->next->random = cur->random->next;
            }
        }
        Node* ans = head->next;
        for (Node* cur = head; cur;) {
            Node* nxt = cur->next;
            if (nxt) {
                cur->next = nxt->next;
            }
            cur = nxt;
        }
        return ans;
    }
};
```

```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Next *Node
 *     Random *Node
 * }
 */

func copyRandomList(head *Node) *Node {
	if head == nil {
		return nil
	}
	for cur := head; cur != nil; {
		node := &Node{cur.Val, cur.Next, nil}
		cur.Next = node
		cur = node.Next
	}
	for cur := head; cur != nil; cur = cur.Next.Next {
		if cur.Random != nil {
			cur.Next.Random = cur.Random.Next
		}
	}
	ans := head.Next
	for cur := head; cur != nil; {
		nxt := cur.Next
		if nxt != nil {
			cur.Next = nxt.Next
		}
		cur = nxt
	}
	return ans
}
```

```js
/**
 * // Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

/**
 * @param {Node} head
 * @return {Node}
 */
var copyRandomList = function (head) {
    if (!head) {
        return null;
    }
    for (let cur = head; cur; ) {
        const node = new Node(cur.val, cur.next, null);
        cur.next = node;
        cur = node.next;
    }
    for (let cur = head; cur; cur = cur.next.next) {
        if (cur.random) {
            cur.next.random = cur.random.next;
        }
    }
    const ans = head.next;
    for (let cur = head; cur; ) {
        const nxt = cur.next;
        if (nxt) {
            cur.next = nxt.next;
        }
        cur = nxt;
    }
    return ans;
};
```

```cs
/*
// Definition for a Node.
public class Node {
    public int val;
    public Node next;
    public Node random;

    public Node(int _val) {
        val = _val;
        next = null;
        random = null;
    }
}
*/

public class Solution {
    public Node CopyRandomList(Node head) {
        if (head == null) {
            return null;
        }
        for (Node cur = head; cur != null; ) {
            Node node = new Node(cur.val, cur.next);
            cur.next = node;
            cur = node.next;
        }
        for (Node cur = head; cur != null; cur = cur.next.next) {
            if (cur.random != null) {
                cur.next.random = cur.random.next;
            }
        }
        Node ans = head.next;
        for (Node cur = head; cur != null; ) {
            Node nxt = cur.next;
            if (nxt != null) {
                cur.next = nxt.next;
            }
            cur = nxt;
        }
        return ans;
    }
}
```

<!-- tabs:end -->

<!-- end -->
