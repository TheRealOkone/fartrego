2024-04-07 16:29 
Tags: #z

___
## Решение
### 1) [[PrefixSum]] & PostfixSum
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Для того чтобы посчитать произведение всей чисел кроме самого числа можно перемножить префиксное произведение (суммирующие умножение слева-направо) с постфиксным произведением (суммирующие умножение справа-налево).
- Инициализируется результирующий массив, в его `i` ячейку записывается результат префиксного умножения `i-1` (слева). Префикс за границей массива равен 1, потому что не влияет на произведение.
- Далее считаем результат. Так как в ячейке `i` хранится префикс `i-1`, то перемножаем значение с постфиксом и получается верный результат. После обновляем значение постфикса.
#### Код
```java
class Solution {
  public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] res = new int[n];

    // calc prefix in res array
    res[0] = 1;
    for (int i = 1; i < n; i++) {
      res[i] = res[i - 1] * nums[i - 1];
    }

    int postfix = nums[n - 1];
    // calc res array -> product of array except self in [i] = prefix[i-1] * postfix[i+1]
    for (int i = n - 2; i >= 0; i--) {
      res[i] *= postfix;
      postfix *= nums[i];
    }

    return res;
  }
}
```
### 2) Мое (быстрое но непонятное)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
- Работает как решение выше только (с префиксами и постфиксами), но немного с запоминанием переменных.
#### Код
```java
class Solution {
  public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    //copy array
    int[] res = new int[nums.length];
    for (int i = 0; i < nums.length; i++) res[i] = nums[i];

    //left to right
    int l = 1;
    int r = 1;
    l = res[0];
    res[0] = 1;
    for (int i = 1; i < n; i++) {
      r = res[i];
      res[i] = res[i - 1] * l;
      l = r;
    }

    //right to left
    l = 1;
    r = nums[n - 1];
    nums[n - 1] = 1;
    for (int i = n - 2; i >= 0; i--) {
      l = nums[i];
      nums[i] = nums[i + 1] * r;
      r = l;
    }

    //product
    for (int i = 0; i < nums.length; i++) res[i] *= nums[i];
    return res;
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/product-of-array-except-self/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=bNvIQI2wAjk)
- [[Arrays & Hashing]]