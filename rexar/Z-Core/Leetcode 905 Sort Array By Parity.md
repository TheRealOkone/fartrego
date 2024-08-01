 2024-07-30 02:45
Tags: #z

___
# Решение
### 1) [[Two Pointers]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Проходимся с двух сторон и ищем подходящие условиям цифры, потом меняем их местами, пока индексы не столкнутся.
#### Код
```java
public class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int i = 0, j = nums.length - 1;
        
        while (i < j) {
            while (i < j && nums[i] % 2 == 0)
                i++;
            while (i < j && nums[j] % 2 == 1)
                j--;
            
            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
        }
        
        return nums;
    }
}
```
### 2)
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В обоях циклах ищем подходящие условиям переменные и потом свапаем их.

#### Код
```java
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int oddIdx = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            while (oddIdx < i && nums[oddIdx] % 2 == 0) oddIdx++;
            if (nums[i] % 2 == 0) swap(nums,i,oddIdx);
        }   
        return nums;
    }

    public void swap(int[] arr, int l, int r) {
        int tmp = arr[l];
        arr[l] = arr[r];
        arr[r] = tmp;
    }
}

```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()