# [1447. Simplified Fractions](https://leetcode.com/problems/simplified-fractions)

[中文文档](/solution/1400-1499/1447.Simplified%20Fractions/README.md)

## Description

<p>Given an integer <code>n</code>, return a list of all <strong>simplified</strong> fractions between 0 and 1 (exclusive) such that the denominator is less-than-or-equal-to <code>n</code>. The fractions can be in <strong>any</strong> order.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> n = 2

<strong>Output:</strong> [&quot;1/2&quot;]

<strong>Explanation: </strong>&quot;1/2&quot; is the only unique fraction with a denominator less-than-or-equal-to 2.</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> n = 3

<strong>Output:</strong> [&quot;1/2&quot;,&quot;1/3&quot;,&quot;2/3&quot;]

</pre>

<p><strong>Example 3:</strong></p>

<pre>

<strong>Input:</strong> n = 4

<strong>Output:</strong> [&quot;1/2&quot;,&quot;1/3&quot;,&quot;1/4&quot;,&quot;2/3&quot;,&quot;3/4&quot;]

<strong>Explanation: </strong>&quot;2/4&quot; is not a simplified fraction because it can be simplified to &quot;1/2&quot;.</pre>

<p><strong>Example 4:</strong></p>

<pre>

<strong>Input:</strong> n = 1

<strong>Output:</strong> []

</pre>

<p>&nbsp;</p>

<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 100</code></li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def simplifiedFractions(self, n: int) -> List[str]:
        return [f'{i}/{j}' for i in range(1, n) for j in range(i + 1, n + 1) if gcd(i, j) == 1]
```

### **Java**

```java
class Solution {
    public List<String> simplifiedFractions(int n) {
        List<String> ans = new ArrayList<>();
        for (int i = 1; i < n; ++i) {
            for (int j = i + 1; j < n + 1; ++j) {
                if (gcd(i, j) == 1) {
                    ans.add(i + "/" + j);
                }
            }
        }
        return ans;
    }

    private int gcd(int a, int b) {
        return b > 0 ? gcd(b, a % b) : a;
    }
}
```

### **TypeScript**

```ts
function simplifiedFractions(n: number): string[] {
    let ans: Array<string> = [];
    for (let j = 2; j <= n; j++) {
        for (let i = 1; i < j; i++) {
            if (gcd(i, j) == 1) {
                ans.push(`${i}/${j}`);
            } 
        }
    }
    return ans;
};

// a < b
function gcd(a: number, b: number): number {
    if (a > b) [a, b] = [b, a];
    while (a) {
        [a, b] = [b % a, a];
    }
    return b;
}
```

### **C++**

```cpp
class Solution {
public:
    vector<string> simplifiedFractions(int n) {
        vector<string> ans;
        for (int i = 1; i < n; ++i)
            for (int j = i + 1; j < n + 1; ++j)
                if (gcd(i, j) == 1)
                    ans.push_back(to_string(i) + "/" + to_string(j));
        return ans;
    }
};
```

### **Go**

```go
func simplifiedFractions(n int) []string {
	var ans []string
	for i := 1; i < n; i++ {
		for j := i + 1; j < n+1; j++ {
			if gcd(i, j) == 1 {
				ans = append(ans, strconv.Itoa(i)+"/"+strconv.Itoa(j))
			}
		}
	}
	return ans
}

func gcd(a, b int) int {
	if b <= 0 {
		return a
	}
	return gcd(b, a%b)
}
```

### **...**

```

```

<!-- tabs:end -->
