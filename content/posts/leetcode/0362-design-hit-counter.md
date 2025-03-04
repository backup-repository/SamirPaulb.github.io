---
title: 0362 Design Hit Counter
summary: 0362 Design Hit Counter LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["0362 Design Hit Counter LeetCode Solution Explained in all languages", "0362 Design Hit Counter", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:0362 Design Hit Counter - Solution Explained/problem-solving.webp
    alt: 0362 Design Hit Counter
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [362. Design Hit Counter](https://leetcode.com/problems/design-hit-counter)


## Description

<p>Design a hit counter which counts the number of hits received in the past <code>5</code> minutes (i.e., the past <code>300</code> seconds).</p>

<p>Your system should accept a <code>timestamp</code> parameter (<strong>in seconds</strong> granularity), and you may assume that calls are being made to the system in chronological order (i.e., <code>timestamp</code> is monotonically increasing). Several hits may arrive roughly at the same time.</p>

<p>Implement the <code>HitCounter</code> class:</p>

<ul>
	<li><code>HitCounter()</code> Initializes the object of the hit counter system.</li>
	<li><code>void hit(int timestamp)</code> Records a hit that happened at <code>timestamp</code> (<strong>in seconds</strong>). Several hits may happen at the same <code>timestamp</code>.</li>
	<li><code>int getHits(int timestamp)</code> Returns the number of hits in the past 5 minutes from <code>timestamp</code> (i.e., the past <code>300</code> seconds).</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input</strong>
[&quot;HitCounter&quot;, &quot;hit&quot;, &quot;hit&quot;, &quot;hit&quot;, &quot;getHits&quot;, &quot;hit&quot;, &quot;getHits&quot;, &quot;getHits&quot;]
[[], [1], [2], [3], [4], [300], [300], [301]]
<strong>Output</strong>
[null, null, null, null, 3, null, 4, 3]

<strong>Explanation</strong>
HitCounter hitCounter = new HitCounter();
hitCounter.hit(1);       // hit at timestamp 1.
hitCounter.hit(2);       // hit at timestamp 2.
hitCounter.hit(3);       // hit at timestamp 3.
hitCounter.getHits(4);   // get hits at timestamp 4, return 3.
hitCounter.hit(300);     // hit at timestamp 300.
hitCounter.getHits(300); // get hits at timestamp 300, return 4.
hitCounter.getHits(301); // get hits at timestamp 301, return 3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= timestamp &lt;= 2 * 10<sup>9</sup></code></li>
	<li>All the calls are being made to the system in chronological order (i.e., <code>timestamp</code> is monotonically increasing).</li>
	<li>At most <code>300</code> calls will be made to <code>hit</code> and <code>getHits</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> What if the number of hits per second could be huge? Does your design scale?</p>

## Solutions

### Solution 1

<!-- tabs:start -->

```python
class HitCounter:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.counter = Counter()

    def hit(self, timestamp: int) -> None:
        """
        Record a hit.
        @param timestamp - The current timestamp (in seconds granularity).
        """
        self.counter[timestamp] += 1

    def getHits(self, timestamp: int) -> int:
        """
        Return the number of hits in the past 5 minutes.
        @param timestamp - The current timestamp (in seconds granularity).
        """
        return sum([v for t, v in self.counter.items() if t + 300 > timestamp])


# Your HitCounter object will be instantiated and called as such:
# obj = HitCounter()
# obj.hit(timestamp)
# param_2 = obj.getHits(timestamp)
```

```java
class HitCounter {

    private Map<Integer, Integer> counter;

    /** Initialize your data structure here. */
    public HitCounter() {
        counter = new HashMap<>();
    }

    /**
       Record a hit.
        @param timestamp - The current timestamp (in seconds granularity).
     */
    public void hit(int timestamp) {
        counter.put(timestamp, counter.getOrDefault(timestamp, 0) + 1);
    }

    /**
       Return the number of hits in the past 5 minutes.
        @param timestamp - The current timestamp (in seconds granularity).
     */
    public int getHits(int timestamp) {
        int hits = 0;
        for (Map.Entry<Integer, Integer> entry : counter.entrySet()) {
            if (entry.getKey() + 300 > timestamp) {
                hits += entry.getValue();
            }
        }
        return hits;
    }
}

/**
 * Your HitCounter object will be instantiated and called as such:
 * HitCounter obj = new HitCounter();
 * obj.hit(timestamp);
 * int param_2 = obj.getHits(timestamp);
 */
```

```rust
use std::{ collections::BinaryHeap, cmp::Reverse };

struct HitCounter {
    /// A min heap
    pq: BinaryHeap<Reverse<i32>>,
}

impl HitCounter {
    fn new() -> Self {
        Self {
            pq: BinaryHeap::new(),
        }
    }

    fn hit(&mut self, timestamp: i32) {
        self.pq.push(Reverse(timestamp));
    }

    fn get_hits(&mut self, timestamp: i32) -> i32 {
        while let Some(Reverse(min_elem)) = self.pq.peek() {
            if *min_elem <= timestamp - 300 {
                self.pq.pop();
            } else {
                break;
            }
        }

        self.pq.len() as i32
    }
}
```

<!-- tabs:end -->

<!-- end -->
