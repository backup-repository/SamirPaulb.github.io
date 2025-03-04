---
title: 1832 Check if the Sentence Is Pangram
summary: 1832 Check if the Sentence Is Pangram LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["1832 Check if the Sentence Is Pangram LeetCode Solution Explained in all languages", "1832 Check if the Sentence Is Pangram", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:1832 Check if the Sentence Is Pangram - Solution Explained/problem-solving.webp
    alt: 1832 Check if the Sentence Is Pangram
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1832. Check if the Sentence Is Pangram](https://leetcode.com/problems/check-if-the-sentence-is-pangram)


## Description

<p>A <strong>pangram</strong> is a sentence where every letter of the English alphabet appears at least once.</p>

<p>Given a string <code>sentence</code> containing only lowercase English letters, return<em> </em><code>true</code><em> if </em><code>sentence</code><em> is a <strong>pangram</strong>, or </em><code>false</code><em> otherwise.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> sentence = &quot;thequickbrownfoxjumpsoverthelazydog&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> sentence contains at least one of every letter of the English alphabet.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> sentence = &quot;leetcode&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= sentence.length &lt;= 1000</code></li>
	<li><code>sentence</code> consists of lowercase English letters.</li>
</ul>

## Solutions

### Solution 1: Array or Hash Table

Traverse the string `sentence`, use an array or hash table to record the letters that have appeared, and finally check whether there are $26$ letters in the array or hash table.

The time complexity is $O(n)$, and the space complexity is $O(C)$. Where $n$ is the length of the string `sentence`, and $C$ is the size of the character set. In this problem, $C = 26$.

<!-- tabs:start -->

```python
class Solution:
    def checkIfPangram(self, sentence: str) -> bool:
        return len(set(sentence)) == 26
```

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        boolean[] vis = new boolean[26];
        for (int i = 0; i < sentence.length(); ++i) {
            vis[sentence.charAt(i) - 'a'] = true;
        }
        for (boolean v : vis) {
            if (!v) {
                return false;
            }
        }
        return true;
    }
}
```

```cpp
class Solution {
public:
    bool checkIfPangram(string sentence) {
        int vis[26] = {0};
        for (char& c : sentence) vis[c - 'a'] = 1;
        for (int& v : vis)
            if (!v) return false;
        return true;
    }
};
```

```go
func checkIfPangram(sentence string) bool {
	vis := [26]bool{}
	for _, c := range sentence {
		vis[c-'a'] = true
	}
	for _, v := range vis {
		if !v {
			return false
		}
	}
	return true
}
```

```ts
function checkIfPangram(sentence: string): boolean {
    const vis = new Array(26).fill(false);
    for (const c of sentence) {
        vis[c.charCodeAt(0) - 'a'.charCodeAt(0)] = true;
    }
    return vis.every(v => v);
}
```

```rust
impl Solution {
    pub fn check_if_pangram(sentence: String) -> bool {
        let mut vis = [false; 26];
        for c in sentence.as_bytes() {
            vis[(*c - b'a') as usize] = true;
        }
        vis.iter().all(|v| *v)
    }
}
```

```c
bool checkIfPangram(char* sentence) {
    int vis[26] = {0};
    for (int i = 0; sentence[i]; i++) {
        vis[sentence[i] - 'a'] = 1;
    }
    for (int i = 0; i < 26; i++) {
        if (!vis[i]) {
            return 0;
        }
    }
    return 1;
}
```

<!-- tabs:end -->

### Solution 2: Bit Manipulation

We can also use an integer $mask$ to record the letters that have appeared, where the $i$-th bit of $mask$ indicates whether the $i$-th letter has appeared.

Finally, check whether there are $26$ $1$s in the binary representation of $mask$, that is, check whether $mask$ is equal to $2^{26} - 1$. If so, return `true`, otherwise return `false`.

The time complexity is $O(n)$, where $n$ is the length of the string `sentence`. The space complexity is $O(1)$.

<!-- tabs:start -->

```python
class Solution:
    def checkIfPangram(self, sentence: str) -> bool:
        mask = 0
        for c in sentence:
            mask |= 1 << (ord(c) - ord('a'))
        return mask == (1 << 26) - 1
```

```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        int mask = 0;
        for (int i = 0; i < sentence.length(); ++i) {
            mask |= 1 << (sentence.charAt(i) - 'a');
        }
        return mask == (1 << 26) - 1;
    }
}
```

```cpp
class Solution {
public:
    bool checkIfPangram(string sentence) {
        int mask = 0;
        for (char& c : sentence) mask |= 1 << (c - 'a');
        return mask == (1 << 26) - 1;
    }
};
```

```go
func checkIfPangram(sentence string) bool {
	mask := 0
	for _, c := range sentence {
		mask |= 1 << int(c-'a')
	}
	return mask == 1<<26-1
}
```

```ts
function checkIfPangram(sentence: string): boolean {
    let mark = 0;
    for (const c of sentence) {
        mark |= 1 << (c.charCodeAt(0) - 'a'.charCodeAt(0));
    }
    return mark === (1 << 26) - 1;
}
```

```rust
impl Solution {
    pub fn check_if_pangram(sentence: String) -> bool {
        let mut mark = 0;
        for c in sentence.as_bytes() {
            mark |= 1 << (*c - b'a');
        }
        mark == (1 << 26) - 1
    }
}
```

```c
bool checkIfPangram(char* sentence) {
    int mark = 0;
    for (int i = 0; sentence[i]; i++) {
        mark |= 1 << (sentence[i] - 'a');
    }
    return mark == (1 << 26) - 1;
}
```

<!-- tabs:end -->

<!-- end -->
