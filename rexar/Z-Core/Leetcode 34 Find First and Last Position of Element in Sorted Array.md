2024-07-26 18:10
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Используется модифицированный [[Binary Search]], так что он ищет крайние элементы, сначала ищем правый элемент, потом проверяем, что найденный элемент соответствует `target` (существует в массиве), потом ищем левый элемент.
#### Код
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int n = nums.length;
        
        // find rightest num
        int l = 0, r = n-1;
        while (l<=r) {
            int mid = l+(r-l)/2;
            if (target < nums[mid]) r=mid-1;
            else l=mid+1;
        }
        int rIdx = r;

        // if out of bounds or wrong number then target not present in array
        if (r < 0 || nums[rIdx] != target) return new int[]{-1,-1};


        // find leftest num
        l = 0;
        r = n-1;
        while (l<=r) {
            int mid = l+(r-l)/2;
            if (target > nums[mid]) l=mid+1;
            else r=mid-1;
        }
        int lIdx = l;

        return new int[]{lIdx,rIdx};
    }
}
```

### 2)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)
- [neetcode видео решения]()