2024-06-15 13:11
Tags: #z

___
# Решение
### 1) Math
Сложность:  `O(n)`
Память: `O(1)`
#### Объяснение
Получаем сумму входящего массива, а также с помощью формулы узнаем какая должна была быть сумма у массива `[0, n]`, возвращаем разницу - это искомый элемент.
#### Код
```java
class Solution {
  public int missingNumber(int[] nums) {
    int n = nums.length;
    int b = (n * (n + 1)) / 2;
    int a = Arrays.stream(nums).sum();
    return b - a;
  }
}
```
### 2) [[Bit Manipulation]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Зная, что при операции XOR два одинаковых числа "взаимоуничтожаются", используем это свойство, чтобы посчитать XOR между индексом и значением (Получается почти как в [[#1) Math|1]]).
#### Код
```java
class Solution {
  public int missingNumber(int[] nums) {
    int xor = 0, i = 0;
    for (i = 0; i < nums.length; i++) {
      xor = xor ^ i ^ nums[i];
    }

    return xor ^ i;
  }
}
```
### 3) Переворот индексов и значений
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Выделяем массив размером `n+1`, проходимся по входящему массиву и используем его значения, как индексы нашего нового массива, в них мы "помечаем", что такое число есть. После этого проходимся по новому массиву и пытаемся найти не "помеченный" элемент.
#### Код
```java
class Solution {
  public int missingNumber(int[] nums) {
    int n = nums.length;
    int[] arr = new int[n + 1];
    for (int num: nums) arr[num] = 1;
    for (int i = 0; i < n + 1; i++)
      if (arr[i] == 0) return i;
    return -1;
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/missing-number/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=WnPLSRLSANE)