---
title: 0520 Detect Capital
summary: 0520 Detect Capital LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0520 Detect Capital LeetCode Solution Explained in all languages", "0520 Detect Capital", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0520 Detect Capital - Solution Explained/problem-solving.webp
    alt: 0520 Detect Capital
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [520. Detect Capital](https://leetcode.com/problems/detect-capital)


## Description

<p>We define the usage of capitals in a word to be right when one of the following cases holds:</p>

<ul>
	<li>All letters in this word are capitals, like <code>&quot;USA&quot;</code>.</li>
	<li>All letters in this word are not capitals, like <code>&quot;leetcode&quot;</code>.</li>
	<li>Only the first letter in this word is capital, like <code>&quot;Google&quot;</code>.</li>
</ul>

<p>Given a string <code>word</code>, return <code>true</code> if the usage of capitals in it is right.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> word = "USA"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> word = "FlaG"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>word</code> consists of lowercase and uppercase English letters.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        cnt = 0
        for c in word:
            if c.isupper():
                cnt += 1
        return cnt == 0 or cnt == len(word) or (cnt == 1 and word[0].isupper())
```

```java
class Solution {
    public boolean detectCapitalUse(String word) {
        int cnt = 0;
        for (char c : word.toCharArray()) {
            if (Character.isUpperCase(c)) {
                ++cnt;
            }
        }
        return cnt == 0 || cnt == word.length()
            || (cnt == 1 && Character.isUpperCase(word.charAt(0)));
    }
}
```

```cpp
class Solution {
public:
    bool detectCapitalUse(string word) {
        int cnt = 0;
        for (char c : word)
            if (isupper(c)) ++cnt;
        return cnt == 0 || cnt == word.size() || (cnt == 1 && isupper(word[0]));
    }
};
```

```go
func detectCapitalUse(word string) bool {
	cnt := 0
	for _, c := range word {
		if unicode.IsUpper(c) {
			cnt++
		}
	}
	return cnt == 0 || cnt == len(word) || (cnt == 1 && unicode.IsUpper(rune(word[0])))
}
```

<!-- tabs:end -->

<!-- end -->
