2024-07-25 18:09
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
Используется модифицированный [[Binary Search]] - проверяется, что элементы слева и справа должны быть меньше текущего элемента, если с какой-то стороны элементы выше, то двигаем `mid` в эту сторону.
#### Код
```java
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        int n = arr.length;
        int l = 0, r = n-1;
        while (l<=r) {
            int mid = l + (r-l)/2;

            boolean leftOk = mid-1 < 0 || arr[mid-1] < arr[mid];
            boolean rightOk = mid+1 >= n || arr[mid+1] < arr[mid];

            if (leftOk && rightOk) return mid;
            if (!leftOk) r = mid-1;
            else if (!rightOk) l = mid+1;
        }
        return -1;
    }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/peak-index-in-a-mountain-array/description/)
- [neetcode видео решения]()