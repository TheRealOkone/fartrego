2024-04-10 01:07 
Tags: #

___
## Решение
### 1) [[Two Pointers|3 pointers]] без [[Set]] с проверкой
Сложность: `O(n^2)`
Память: `O(1)`
#### Объяснение
Задача сводится к решению проблемы [[Leetcode 167 Two Sum II|Two Sum II]], после сортировки входящего массива. Первым указателем проходимся по всему массиву, а остальные 2 используются как [[Two Pointers]] с началом после 1 указателя.
В начале цикла прописывается проверка на дубликат первой цифры. Далее все идентично как в [[Leetcode 167 Two Sum II|Two Sum II]], только с изменением при успешном подборе - смещаем указатели если следующая цифра будет дубликатом. После добавляем наш триплет и сдвигаем оба указателя.
#### Код
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        int n = nums.length;
        for (int i = 0; i < n-2; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue;
            int start = i+1;
            int end = n-1;
            while (start < end) {
                int curr = nums[i]+nums[start]+nums[end];
                if (curr > 0) {
                    end--;
                    continue;
                }
                if (curr < 0) {
                    start++;
                    continue;
                }
                if (curr == 0) {
                    while (start < end && nums[start] == nums[start+1]) start++;
                    while (start < end && nums[end] == nums[end-1]) end--;
                    res.add(Arrays.asList(nums[i],nums[start],nums[end]));
                    start++;
                    end--;
                }
            }
        }
        return res;
    }
}
```
### 2) [[Two Pointers|3 pointers]] c [[Set]] без проверки
Сложность: `O(n^2)`
Память: `O(1)`
#### Объяснение
Отличается от 1 решения только тем, что вместо дополнительной проверки в начале цикла, мы боремся с дубликатами, тем что кладем их в [[Set]], где они фильтруются.
#### Код
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        Set<List<Integer>> res = new HashSet<>();
        int n = nums.length;
        for (int i = 0; i < n-2; i++) {
            int start = i+1;
            int end = n-1;
            while (start < end) {
                int curr = nums[i]+nums[start]+nums[end];
                if (curr > 0) {
                    end--;
                    continue;
                }
                if (curr < 0) {
                    start++;
                    continue;
                }
                if (curr == 0) {
                    while (start < end && nums[start] == nums[start+1]) start++;
                    while (start < end && nums[end] == nums[end-1]) end--;
                    res.add(Arrays.asList(nums[i],nums[start],nums[end]));
                    start++;
                    end--;
                }
            }
        }
        return new ArrayList<>(res);
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/3sum/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=jzZsG8n2R9A)
- [[Two Pointers]]