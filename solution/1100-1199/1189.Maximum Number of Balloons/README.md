# [1189. “气球” 的最大数量](https://leetcode-cn.com/problems/maximum-number-of-balloons)

[English Version](/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给你一个字符串&nbsp;<code>text</code>，你需要使用 <code>text</code> 中的字母来拼凑尽可能多的单词&nbsp;<strong>&quot;balloon&quot;（气球）</strong>。</p>

<p>字符串&nbsp;<code>text</code> 中的每个字母最多只能被使用一次。请你返回最多可以拼凑出多少个单词&nbsp;<strong>&quot;balloon&quot;</strong>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/images/1536_ex1_upd.jpeg" style="height: 35px; width: 154px;"></strong></p>

<pre><strong>输入：</strong>text = &quot;nlaebolko&quot;
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/1100-1199/1189.Maximum%20Number%20of%20Balloons/images/1536_ex2_upd.jpeg" style="height: 35px; width: 233px;"></strong></p>

<pre><strong>输入：</strong>text = &quot;loonbalxballpoon&quot;
<strong>输出：</strong>2
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>text = &quot;leetcode&quot;
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 10^4</code></li>
	<li><code>text</code>&nbsp;全部由小写英文字母组成</li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

简单计数。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

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

<!-- 这里可写当前语言的特殊实现逻辑 -->

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
