---
title: 0946 Validate Stack Sequences
summary: 0946 Validate Stack Sequences LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0946 Validate Stack Sequences LeetCode Solution Explained in all languages", "0946 Validate Stack Sequences", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0946 Validate Stack Sequences - Solution Explained/problem-solving.webp
    alt: 0946 Validate Stack Sequences
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [946. Validate Stack Sequences](https://leetcode.com/problems/validate-stack-sequences)


## Description

<p>Given two integer arrays <code>pushed</code> and <code>popped</code> each with distinct values, return <code>true</code><em> if this could have been the result of a sequence of push and pop operations on an initially empty stack, or </em><code>false</code><em> otherwise.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
<strong>Output:</strong> true
<strong>Explanation:</strong> We might do the following sequence:
push(1), push(2), push(3), push(4),
pop() -&gt; 4,
push(5),
pop() -&gt; 5, pop() -&gt; 3, pop() -&gt; 2, pop() -&gt; 1
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
<strong>Output:</strong> false
<strong>Explanation:</strong> 1 cannot be popped before 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= pushed.length &lt;= 1000</code></li>
	<li><code>0 &lt;= pushed[i] &lt;= 1000</code></li>
	<li>All the elements of <code>pushed</code> are <strong>unique</strong>.</li>
	<li><code>popped.length == pushed.length</code></li>
	<li><code>popped</code> is a permutation of <code>pushed</code>.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def validateStackSequences(self, pushed: List[int], popped: List[int]) -> bool:
        j, stk = 0, []
        for v in pushed:
            stk.append(v)
            while stk and stk[-1] == popped[j]:
                stk.pop()
                j += 1
        return j == len(pushed)
```

```java
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
        Deque<Integer> stk = new ArrayDeque<>();
        int j = 0;
        for (int v : pushed) {
            stk.push(v);
            while (!stk.isEmpty() && stk.peek() == popped[j]) {
                stk.pop();
                ++j;
            }
        }
        return j == pushed.length;
    }
}
```

```cpp
class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        stack<int> stk;
        int j = 0;
        for (int v : pushed) {
            stk.push(v);
            while (!stk.empty() && stk.top() == popped[j]) {
                stk.pop();
                ++j;
            }
        }
        return j == pushed.size();
    }
};
```

```go
func validateStackSequences(pushed []int, popped []int) bool {
	stk := []int{}
	j := 0
	for _, v := range pushed {
		stk = append(stk, v)
		for len(stk) > 0 && stk[len(stk)-1] == popped[j] {
			stk = stk[:len(stk)-1]
			j++
		}
	}
	return j == len(pushed)
}
```

```ts
function validateStackSequences(pushed: number[], popped: number[]): boolean {
    const stk = [];
    let j = 0;
    for (const v of pushed) {
        stk.push(v);
        while (stk.length && stk[stk.length - 1] == popped[j]) {
            stk.pop();
            ++j;
        }
    }
    return j == pushed.length;
}
```

```rust
impl Solution {
    pub fn validate_stack_sequences(pushed: Vec<i32>, popped: Vec<i32>) -> bool {
        let mut stack = Vec::new();
        let mut i = 0;
        for &num in pushed.iter() {
            stack.push(num);
            while !stack.is_empty() && *stack.last().unwrap() == popped[i] {
                stack.pop();
                i += 1;
            }
        }
        stack.len() == 0
    }
}
```

```js
/**
 * @param {number[]} pushed
 * @param {number[]} popped
 * @return {boolean}
 */
var validateStackSequences = function (pushed, popped) {
    let stk = [];
    let j = 0;
    for (const v of pushed) {
        stk.push(v);
        while (stk.length && stk[stk.length - 1] == popped[j]) {
            stk.pop();
            ++j;
        }
    }
    return j == pushed.length;
};
```

```cs
public class Solution {
    public bool ValidateStackSequences(int[] pushed, int[] popped) {
        Stack<int> stk = new Stack<int>();
        int j = 0;
        foreach (int x in pushed)
        {
            stk.Push(x);
            while (stk.Count != 0 && stk.Peek() == popped[j]) {
                stk.Pop();
                ++j;
            }
        }
        return stk.Count == 0;
    }
}
```

<!-- tabs:end -->

<!-- end -->
