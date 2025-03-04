---
title: 1190 Reverse Substrings Between Each Pair of Parentheses
summary: 1190 Reverse Substrings Between Each Pair of Parentheses LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1190 Reverse Substrings Between Each Pair of Parentheses LeetCode Solution Explained in all languages", "1190 Reverse Substrings Between Each Pair of Parentheses", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1190 Reverse Substrings Between Each Pair of Parentheses - Solution Explained/problem-solving.webp
    alt: 1190 Reverse Substrings Between Each Pair of Parentheses
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1190. Reverse Substrings Between Each Pair of Parentheses](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses)


## Description

<p>You are given a string <code>s</code> that consists of lower case English letters and brackets.</p>

<p>Reverse the strings in each pair of matching parentheses, starting from the innermost one.</p>

<p>Your result should <strong>not</strong> contain any brackets.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(abcd)&quot;
<strong>Output:</strong> &quot;dcba&quot;
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(u(love)i)&quot;
<strong>Output:</strong> &quot;iloveu&quot;
<strong>Explanation:</strong> The substring &quot;love&quot; is reversed first, then the whole string is reversed.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(ed(et(oc))el)&quot;
<strong>Output:</strong> &quot;leetcode&quot;
<strong>Explanation:</strong> First, we reverse the substring &quot;oc&quot;, then &quot;etco&quot;, and finally, the whole string.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> only contains lower case English characters and parentheses.</li>
	<li>It is guaranteed that all parentheses are balanced.</li>
</ul>

## Solutions

### Solution 1: Simulation

We can use a double-ended queue or stack to simulate the reversal process.

The time complexity is $O(n^2)$, where $n$ is the length of the string $s$.

<!-- tabs:start -->

```python
class Solution:
    def reverseParentheses(self, s: str) -> str:
        stk = []
        for c in s:
            if c == ')':
                t = []
                while stk[-1] != '(':
                    t.append(stk.pop())
                stk.pop()
                stk.extend(t)
            else:
                stk.append(c)
        return ''.join(stk)
```

```java
class Solution {
    public String reverseParentheses(String s) {
        int n = s.length();
        int[] d = new int[n];
        Deque<Integer> stk = new ArrayDeque<>();
        for (int i = 0; i < n; ++i) {
            if (s.charAt(i) == '(') {
                stk.push(i);
            } else if (s.charAt(i) == ')') {
                int j = stk.pop();
                d[i] = j;
                d[j] = i;
            }
        }
        StringBuilder ans = new StringBuilder();
        int i = 0, x = 1;
        while (i < n) {
            if (s.charAt(i) == '(' || s.charAt(i) == ')') {
                i = d[i];
                x = -x;
            } else {
                ans.append(s.charAt(i));
            }
            i += x;
        }
        return ans.toString();
    }
}
```

```cpp
class Solution {
public:
    string reverseParentheses(string s) {
        string stk;
        for (char& c : s) {
            if (c == ')') {
                string t;
                while (stk.back() != '(') {
                    t.push_back(stk.back());
                    stk.pop_back();
                }
                stk.pop_back();
                stk += t;
            } else {
                stk.push_back(c);
            }
        }
        return stk;
    }
};
```

```go
func reverseParentheses(s string) string {
	stk := []byte{}
	for i := range s {
		if s[i] == ')' {
			t := []byte{}
			for stk[len(stk)-1] != '(' {
				t = append(t, stk[len(stk)-1])
				stk = stk[:len(stk)-1]
			}
			stk = stk[:len(stk)-1]
			stk = append(stk, t...)
		} else {
			stk = append(stk, s[i])
		}
	}
	return string(stk)
}
```

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseParentheses = function (s) {
    const n = s.length;
    const d = new Array(n).fill(0);
    const stk = [];
    for (let i = 0; i < n; ++i) {
        if (s[i] == '(') {
            stk.push(i);
        } else if (s[i] == ')') {
            const j = stk.pop();
            d[i] = j;
            d[j] = i;
        }
    }
    let i = 0;
    let x = 1;
    const ans = [];
    while (i < n) {
        const c = s.charAt(i);
        if (c == '(' || c == ')') {
            i = d[i];
            x = -x;
        } else {
            ans.push(c);
        }
        i += x;
    }
    return ans.join('');
};
```

<!-- tabs:end -->

### Solution 2: Quick Thinking

We observe that during the traversal of the string, each time we encounter '(' or ')', we jump to the corresponding ')' or '(', then reverse the traversal direction and continue.

Therefore, we can use an array $d$ to record the position of the other bracket corresponding to each '(' or ')', i.e., $d[i]$ represents the position of the other bracket corresponding to the bracket at position $i$. We can directly use a stack to calculate the array $d$.

Then, we traverse the string from left to right. When we encounter '(' or ')', we jump to the corresponding position according to the array $d$, then reverse the direction and continue to traverse until the entire string is traversed.

The time complexity is $O(n)$, where $n$ is the length of the string $s$.

<!-- tabs:start -->

```python
class Solution:
    def reverseParentheses(self, s: str) -> str:
        n = len(s)
        d = [0] * n
        stk = []
        for i, c in enumerate(s):
            if c == '(':
                stk.append(i)
            elif c == ')':
                j = stk.pop()
                d[i], d[j] = j, i
        i, x = 0, 1
        ans = []
        while i < n:
            if s[i] in '()':
                i = d[i]
                x = -x
            else:
                ans.append(s[i])
            i += x
        return ''.join(ans)
```

```cpp
class Solution {
public:
    string reverseParentheses(string s) {
        int n = s.size();
        vector<int> d(n);
        stack<int> stk;
        for (int i = 0; i < n; ++i) {
            if (s[i] == '(') {
                stk.push(i);
            } else if (s[i] == ')') {
                int j = stk.top();
                stk.pop();
                d[i] = j;
                d[j] = i;
            }
        }
        int i = 0, x = 1;
        string ans;
        while (i < n) {
            if (s[i] == '(' || s[i] == ')') {
                i = d[i];
                x = -x;
            } else {
                ans.push_back(s[i]);
            }
            i += x;
        }
        return ans;
    }
};
```

```go
func reverseParentheses(s string) string {
	n := len(s)
	d := make([]int, n)
	stk := []int{}
	for i, c := range s {
		if c == '(' {
			stk = append(stk, i)
		} else if c == ')' {
			j := stk[len(stk)-1]
			stk = stk[:len(stk)-1]
			d[i], d[j] = j, i
		}
	}
	ans := []byte{}
	i, x := 0, 1
	for i < n {
		if s[i] == '(' || s[i] == ')' {
			i = d[i]
			x = -x
		} else {
			ans = append(ans, s[i])
		}
		i += x
	}
	return string(ans)
}
```

<!-- tabs:end -->

<!-- end -->
