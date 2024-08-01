2024-07-29 18:19
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение
С помощью бинарного поиска ищем индекс `i`, чтобы количество недостающих чисел перед `i` было равно `k`. 
- Если количество недостающих чисел перед  `i` меньше `k`, то нужно искать в правой половине массива.
- Если количество отсутствующих чисел перед `i` больше или равно `k`, то нужно искать в левой половине массива.

Чтобы найти количество недостающих чисел до `i`, используем формулу `arr[i] - i - 1`, которая представляет собой разность между фактическим значением элемента в индексе `i` и ожидаемым значением элемента в индексе `i` в полном массиве всех положительных целых чисел.
#### Код
```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] - mid - 1 < k) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return left + k;
    }
}
```
### 2)
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Считаем недостающие числа между элементами множества, если `k` меньше "пробела", то возвращаем предыдущий + k. 
#### Код
```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int n = arr.length;
        int prev = 0;
        for (int i = 0; i < n; i++) {
            int gap = arr[i]-prev-1;
            if (k-gap > 0) k-=gap;
            else return prev+k;
            prev = arr[i];
        }
        return prev+k;
    }
}
```

### 3)
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Если текущий элемент меньше чем "сдвиг", то увеличиваем сдвиг на 1, иначе возвращаем сдвиг.
#### Код
```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        for(int i : arr){
			if(i <= k) k++; else break;
		}
        return k;
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