2024-04-01 23:33
Tags: #z

___
# Решение
### 1) BruteForce
Сложность: `O(n^2)`
Память: `O(1)`
#### Объяснение
Один из подходов BruteForce - рассматривать каждую пару элементов и проверять, равна ли их сумма целевому значению. Это можно сделать с помощью вложенных циклов, где внешний цикл выполняет итерацию от первого элемента до предпоследнего, а внутренний - от следующего элемента до последнего. Однако такой подход имеет временную сложность `O(n^2)`.
#### Код
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{}; // No solution found
    }
}
```
### 2) HashMap
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Более эффективный подход - использовать [[HashMap]]. Мы можем пройтись по массиву один раз и для каждого элемента проверить, существует ли в хэш-таблице целевой элемент минус текущий. Если да, то мы нашли корректную пару чисел. Если нет, то мы добавляем текущий элемент в хэш-таблицу.
#### Код (HashMap в два прохода)
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numMap = new HashMap<>();
        int n = nums.length;

        // Build the hash table
        for (int i = 0; i < n; i++) {
            numMap.put(nums[i], i);
        }

        // Find the complement
        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement) 
            && numMap.get(complement) != i) {
                return new int[]{i, numMap.get(complement)};
            }
        }

        return new int[]{}; // No solution found
    }
}
```
#### Код (HashMap в один проход)
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numMap = new HashMap<>();
        int n = nums.length;

        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement)) {
                return new int[]{numMap.get(complement), i};
            }
            numMap.put(nums[i], i);
        }

        return new int[]{}; // No solution found
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/two-sum/description/)
- [neetcode видео решения](https://youtu.be/KLlXCFG5TnA)
- [[Arrays & Hashing]]