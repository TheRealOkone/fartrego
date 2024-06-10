2024-05-30 22:46
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Используя исходный массив переписываем в каждую ячейку минимальную стоимость добраться до нее.
#### Код
```java
class Solution {
  public int minCostClimbingStairs(int[] cost) {
    int n = cost.length;
    for (int i = 2; i < n; i++) {
      cost[i] += Math.min(cost[i - 2], cost[i - 1]);
    }

    return Math.min(cost[n - 2], cost[n - 1]);
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