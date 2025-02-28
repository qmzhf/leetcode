# [1189. Maximum Number of Balloons](https://leetcode.com/problems/maximum-number-of-balloons)

[中文文档](/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/README.md)

## Description

<p>Given a string <code>text</code>, you want to use the characters of <code>text</code> to form as many instances of the word <strong>&quot;balloon&quot;</strong> as possible.</p>

<p>You can use each character in <code>text</code> <strong>at most once</strong>. Return the maximum number of instances that can be formed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/images/1536_ex1_upd.jpeg" style="width: 132px; height: 35px;" /></strong></p>

<pre>
<strong>Input:</strong> text = &quot;nlaebolko&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/images/1536_ex2_upd.jpeg" style="width: 267px; height: 35px;" /></strong></p>

<pre>
<strong>Input:</strong> text = &quot;loonbalxballpoon&quot;
<strong>Output:</strong> 2
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> text = &quot;leetcode&quot;
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 10<sup>4</sup></code></li>
	<li><code>text</code> consists of lower case English letters only.</li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        ans = 0
        counter = Counter(text)
        counter['l'] >>= 1
        counter['o'] >>= 1
        return min(counter['b'], counter['a'], counter['l'], counter['o'], counter['n'])
```

### **Java**

```java
class Solution {
    public int maxNumberOfBalloons(String text) {
        int[] counter = new int[26];
        for (char c : text.toCharArray()) {
            ++counter[c - 'a'];
        }
        counter['l' - 'a'] >>= 1;
        counter['o' - 'a'] >>= 1;
        int ans = 10000;
        for (char c : "balon".toCharArray()) {
            ans = Math.min(ans, counter[c - 'a']);
        }
        return ans;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int maxNumberOfBalloons(string text) {
        vector<int> counter(26);
        for (char& c : text) ++counter[c - 'a'];
        counter['l' - 'a'] >>= 1;
        counter['o' - 'a'] >>= 1;
        int ans = 10000;
        string t = "balon";
        for (char& c : t) ans = min(ans, counter[c - 'a']);
        return ans;
    }
};
```

### **Go**

```go
func maxNumberOfBalloons(text string) int {
	counter := make([]int, 26)
	for i := range text {
		counter[text[i]-'a']++
	}
	counter['l'-'a'] >>= 1
	counter['o'-'a'] >>= 1
	ans := 10000
	t := "balon"
	for i := range t {
		ans = min(ans, counter[t[i]-'a'])
	}
	return ans
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### **...**

```

```

<!-- tabs:end -->
