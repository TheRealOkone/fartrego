2024-04-01 22:11
Tags: #z

___
# Решение
### 1) [[HashSet]]
Сложность: `O(n)`
#### Объяснение
Подход с использованием HashSet использует структуру данных HashSet для хранения встречающихся элементов. Итерация проходит через массив, проверяя, не находится ли элемент уже в наборе. Если да, то возвращается `true`. В противном случае элемент добавляется в набор. Этот подход имеет временную сложность `O(n)` и обеспечивает эффективный способ проверки на наличие дубликатов.
#### Код
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> seen = new HashSet<>();
        for (int num : nums) {
            if (seen.contains(num))
                return true;
            seen.add(num);
        }
        return false;
    }
}
```

### 2) Sorting
Сложность: `O(n log n)`
#### Объяснение
Метод сортировки сортирует массив в порядке возрастания, а затем проверяет, нет ли в соседних элементах одинаковых. Если дубликаты найдены, возвращается `true`. Сортировка помогает собрать дубликаты вместе, упрощая проверку. Однако сортировка имеет временную сложность `O(n log n)`.
#### Код
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        for (int i = 1; i < n; i++) {
            if (nums[i] == nums[i - 1])
                return true;
        }
        return false;
    }
}
```
___
### Zero-Links
- [[00 Sorting]]

___
### Links
- [leetcode задача](https://leetcode.com/problems/contains-duplicate/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=3OamzN90kPg)
- [[Arrays & Hashing]]