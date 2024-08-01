2024-07-25 17:44
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Слова излишни
#### Код
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int res = Arrays.binarySearch(nums, target);
        return res >= 0 ? res : (res+1)*-1;
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/search-insert-position/description/)
- [neetcode видео решения]()