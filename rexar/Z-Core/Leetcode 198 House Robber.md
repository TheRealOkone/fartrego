2024-05-31 19:04
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Для того, чтобы написать алгоритм с "оглядкой назад", сразу прописываем, через if'ы ответы на размеры от 1 до 3 включительно. Далее мы перезаписываем ячейки входного массива на самые выгодные сборы монеток на этот `i`. Для этого мы добавляем на этот `i` максимальное значение из `i-2` и `i-3`.
В конце возвращаем максимум из последнего и предпоследнего элемента.
#### Код
```java
class Solution {
  public int rob(int[] nums) {
    int n = nums.length;
    if (n == 1) return nums[0];
    if (n == 2) return Math.max(nums[0], nums[1]);
    if (n == 3) return Math.max(nums[1], nums[0] + nums[2]);

    nums[2] += nums[0];
    for (int i = 3; i < n; i++) {
      nums[i] += Math.max(nums[i - 2], nums[i - 3]);
    }
    return Math.max(nums[n - 1], nums[n - 2]);
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/house-robber/description/)
- [neetcode видео решения](https://youtu.be/73r3KWiEvyk)