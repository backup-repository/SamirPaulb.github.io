---
title: 0744 Find Smallest Letter Greater Than Target
summary: 0744 Find Smallest Letter Greater Than Target LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0744 Find Smallest Letter Greater Than Target LeetCode Solution Explained in all languages", "0744 Find Smallest Letter Greater Than Target", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0744 Find Smallest Letter Greater Than Target - Solution Explained/problem-solving.webp
    alt: 0744 Find Smallest Letter Greater Than Target
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target)


## Description

<p>You are given an array of characters <code>letters</code> that is sorted in <strong>non-decreasing order</strong>, and a character <code>target</code>. There are <strong>at least two different</strong> characters in <code>letters</code>.</p>

<p>Return <em>the smallest character in </em><code>letters</code><em> that is lexicographically greater than </em><code>target</code>. If such a character does not exist, return the first character in <code>letters</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;c&quot;,&quot;f&quot;,&quot;j&quot;], target = &quot;a&quot;
<strong>Output:</strong> &quot;c&quot;
<strong>Explanation:</strong> The smallest character that is lexicographically greater than &#39;a&#39; in letters is &#39;c&#39;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;c&quot;,&quot;f&quot;,&quot;j&quot;], target = &quot;c&quot;
<strong>Output:</strong> &quot;f&quot;
<strong>Explanation:</strong> The smallest character that is lexicographically greater than &#39;c&#39; in letters is &#39;f&#39;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> letters = [&quot;x&quot;,&quot;x&quot;,&quot;y&quot;,&quot;y&quot;], target = &quot;z&quot;
<strong>Output:</strong> &quot;x&quot;
<strong>Explanation:</strong> There are no characters in letters that is lexicographically greater than &#39;z&#39; so we return letters[0].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= letters.length &lt;= 10<sup>4</sup></code></li>
	<li><code>letters[i]</code> is a lowercase English letter.</li>
	<li><code>letters</code> is sorted in <strong>non-decreasing</strong> order.</li>
	<li><code>letters</code> contains at least two different characters.</li>
	<li><code>target</code> is a lowercase English letter.</li>
</ul>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        left, right = 0, len(letters)
        while left < right:
            mid = (left + right) >> 1
            if ord(letters[mid]) > ord(target):
                right = mid
            else:
                left = mid + 1
        return letters[left % len(letters)]
```

```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int left = 0, right = letters.length;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (letters[mid] > target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return letters[left % letters.length];
    }
}
```

```cpp
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        int left = 0, right = letters.size();
        while (left < right) {
            int mid = left + right >> 1;
            if (letters[mid] > target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return letters[left % letters.size()];
    }
};
```

```go
func nextGreatestLetter(letters []byte, target byte) byte {
	left, right := 0, len(letters)
	for left < right {
		mid := (left + right) >> 1
		if letters[mid] > target {
			right = mid
		} else {
			left = mid + 1
		}
	}
	return letters[left%len(letters)]
}
```

```ts
function nextGreatestLetter(letters: string[], target: string): string {
    const n = letters.length;
    let left = 0;
    let right = letters.length;
    while (left < right) {
        let mid = (left + right) >>> 1;
        if (letters[mid] > target) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return letters[left % n];
}
```

```rust
impl Solution {
    pub fn next_greatest_letter(letters: Vec<char>, target: char) -> char {
        *letters
            .iter()
            .find(|&&c| c > target)
            .unwrap_or(&letters[0])
    }
}
```

```php
class Solution {
    /**
     * @param String[] $letters
     * @param String $target
     * @return String
     */
    function nextGreatestLetter($letters, $target) {
        $left = 0;
        $right = count($letters);
        while ($left <= $right) {
            $mid = floor($left + ($right - $left) / 2);
            if ($letters[$mid] > $target) {
                $right = $mid - 1;
            } else {
                $left = $mid + 1;
            }
        }
        if ($left >= count($letters)) {
            return $letters[0];
        } else {
            return $letters[$left];
        }
    }
}
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```rust
impl Solution {
    pub fn next_greatest_letter(letters: Vec<char>, target: char) -> char {
        let n = letters.len();
        let mut left = 0;
        let mut right = n;
        while left < right {
            let mid = left + (right - left) / 2;
            if letters[mid] > target {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        letters[left % n]
    }
}
```

<!-- tabs:end -->

<!-- end -->
