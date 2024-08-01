2024-04-09 19:30 
Tags: #

___
#
Сложность: `O(log n)`
Память: `O(1)`

## Алгоритм 

Массив должен быть предварительно отсортирован.

1. Определение значения элемента в середине структуры данных. Полученное значение сравнивается с ключом.
2. Если ключ меньше значения середины, то поиск осуществляется в первой половине элементов, иначе — во второй.
3. Поиск сводится к тому, что вновь определяется значение серединного элемента в выбранной половине и сравнивается с ключом.
4. Процесс продолжается до тех пор, пока не будет найден элемент со значением ключа или не станет пустым интервал для поиска.

### Модификации
```java
private int findFirst(int[] nums, int target){
    int idx = -1;
    int l = 0;
    int r = nums.length - 1;
    while(l <= r){
        int mid = l + (r-l) / 2;
        if(nums[mid] >= target){
            r = mid - 1;
        }else{
            l = mid + 1;
        }
        if(nums[mid] == target) idx = mid;
    }
    return idx;
}

private int findLast(int[] nums, int target){
    int idx = -1;
    int l = 0;
    int r = nums.length - 1;
    while(l <= r){
        int mid = l + (r-l) / 2;
        if(nums[mid] <= target){
            l = mid + 1;
        }else{
            r = mid - 1;
        }
        if(nums[mid] == target) idx = mid;
    }
    return idx;
}
```
___
### Zero-Links
- [[00 Sorting]]

___
### Links
- [Википедия](https://ru.wikipedia.org/wiki/%D0%94%D0%B2%D0%BE%D0%B8%D1%87%D0%BD%D1%8B%D0%B9_%D0%BF%D0%BE%D0%B8%D1%81%D0%BA)