2024-06-19 23:39
Tags: #z

___
# Решение
### 1) [[Greedy]] && [[Sliding window]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Запоминается максимальная сумма. Если на текущем шаге, левый "хвостик"/часть является отрицательной - она только уменьшает сумму и она отбрасывается.
#### Код
```java
class Solution {
  public int maxSubArray(int[] nums) {
    int max = Integer.MIN_VALUE;
    int c = 0;
    for (int n: nums) {
      if (c < 0) c = 0;
      c += n;
      max = Math.max(max, c);

    }
    return max;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/maximum-subarray/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=5WZl3MMT0Eg)