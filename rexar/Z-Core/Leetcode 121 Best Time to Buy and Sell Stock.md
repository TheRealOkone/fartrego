2024-07-30 02:19
Tags: #z

___
# Решение
### 1) [[Kadane's algorythm]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение

#### Код
```java
class Solution {
    public int maxProfit(int[] prices) {
        int max = 0;
        int min = prices[0];
        int n = prices.length;
        for (int i = 1; i < n; i++) {
            int diff = prices[i]-min;
            if (diff < 0) {
                min = prices[i];
            } else {
                max = Math.max(max, diff);
            }
        }
        return max;
    }
}
```
### 2)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код
```java

```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()