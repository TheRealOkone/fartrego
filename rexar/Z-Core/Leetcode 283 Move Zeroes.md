2024-07-29 15:27
Tags: #z

___
# Решение
### 1) 
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Проходимся в цикле по массиву, определяя во внутреннем цикле `while`, где находится `0` слева от индекса главного цикла, и свапаем, если таковых не имеется, то свап произойдет сам с собой = ничего не изменится.
#### Код
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int n = nums.length;
        int l = 0;
        for (int i = 0; i < n; i++) {
            while (l < i && nums[l] != 0) l++;
            if (nums[i] != 0) swap(nums,i,l);
        }
    }

    public void swap(int[] arr, int l, int r) {
        int tmp = arr[r];
        arr[r] = arr[l];
        arr[l] = tmp;
    }
}
```
### 2)
Сложность: `O(n+k)`
Память: `O(1)`
#### Объяснение
Проходимся по массиву, и все не нули двигаем вперед. Потом оставшееся пространство заполняется нулями.
#### Код
```java
class Solution {
    public void moveZeroes(int[] nums) {
        if (nums.length == 1) {
            return;
        }

        int nonZeroIndex = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[nonZeroIndex] = nums[i];
                nonZeroIndex++;
            }
        }

       
         while(nonZeroIndex<nums.length){
            nums[nonZeroIndex] = 0;
            nonZeroIndex++;
        }
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/move-zeroes/description/)
- [neetcode видео решения]()