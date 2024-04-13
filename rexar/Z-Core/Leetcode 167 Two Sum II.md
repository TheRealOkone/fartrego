2024-04-09 18:57 
Tags: #z

___
# Решение
### 1) [[Two Pointers]]
Сложность: `O(n)`
Память `O(1)`
#### Объяснение
Подход к этому вопросу отличается от классической задачи о двух суммах тем, что у нас есть определенное направление, в котором мы хотим искать нашу цель.  
  
Поскольку массив отсортирован, мы можем сделать несколько общих наблюдений:  
  
Меньшие суммы будут находиться в левой половине массива  
Большие суммы будут находиться в правой половине массива.  
Поэтому, используя два указателя, начинающиеся в конечных точках массива, мы можем увеличить или уменьшить нашу текущую сумму, как нам захочется.
#### Код
```java
class Solution {
  public int[] twoSum(int[] numbers, int target) {
    int start = 0;
    int end = numbers.length - 1;
    while (start < end) {
      int curr = numbers[start] + numbers[end];
      if (curr > target) {
        end--;
        continue;
      }
      if (curr < target) {
        start++;
        continue;
      }
      if (curr == target) return new int[] {
        start + 1, end + 1
      };
    }
    return new int[] {};
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
- [neetcode видео решения](https://youtu.be/cQ1Oz4ckceM)
- [leetcode решение](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/solutions/2128501/two-pointers-visual-explanation-java/)
- [[Two Pointers]]