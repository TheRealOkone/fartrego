2024-07-25 18:13
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код
```java
class Solution {
    public int search(int[] nums, int target) {
        int n = nums.length;
        int r = n-1;
        int l = 0;
        while (l<=r) {
            int ind = l+(r-l)/2;
            int curr = nums[ind];
            if (curr == target) return ind;
            if (target > curr) {
                l = ind + 1;
            }
            else if (target < curr) {
                r = ind - 1;
            }
            
        } 
        return -1;
    }
}
```
### 2) Хе-хе-хе
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Слова излишни
#### Код
```java
class Solution {
    public int search(int[] nums, int target) {
        int res = Arrays.binarySearch(nums, target);
        return res < 0 ? -1 : res;
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/binary-search/description/)
- [neetcode видео решения]()