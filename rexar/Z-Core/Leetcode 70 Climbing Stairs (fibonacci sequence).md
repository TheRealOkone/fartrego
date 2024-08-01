2024-05-30 22:16
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]] && Space Optimization
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Решаются как и числа Фибоначчи.
#### Код
```java
class Solution {
    public int climbStairs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        int prev = 1, curr = 1;
        for (int i = 2; i <= n; i++) {
            int temp = curr;
            curr = prev + curr;
            prev = temp;
        }
        return curr;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()