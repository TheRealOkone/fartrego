2024-06-06 19:54
Tags: #z

___
# Решение
### 1) [[Kadane's algorythm]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
- Случай1 :- Все элементы положительные : Тогда ответом будет произведение всех элементов массива.
- Случай2 :- В массиве есть как положительные, так и отрицательные элементы:
	1) Если количество отрицательных элементов четное, то ответом будет полный массив, так как при перемножении всех отрицательных чисел он станет положительным.
	2) Если количество отрицательных элементов нечетное, то необходимо удалить только один отрицательный элемент, а для этого нужно проверить подмассивы, чтобы получить максимальное произведение.
- Случай 3 :- Массив также содержит 0: Тогда особой разницы не будет... просто массив будет разбит на подмассивы вокруг 0. Как только произведение станет 0, сделать его 1 для следующей итерации, теперь нужно искать новый подмассив, а предыдущий `max` уже будет обновлен.

Подход к этому вопросу точно такой же, как и в Kadane's Algo, с той лишь разницей, что мы будем обходить массив с двух сторон. Постоянно умножаем числа и запоминаем максимальное произведение. Если встречается ноль, то сбрасываем `prod` до 1, чтобы продолжить цикл.
#### Код
```java
class Solution {
  public int maxProduct(int[] nums) {

    int maxi = Integer.MIN_VALUE;
    int prod = 1;
    for (int i = 0; i < nums.length; i++) {
      prod *= nums[i];
      maxi = Math.max(prod, maxi);
      if (prod == 0) prod = 1;
    }
    prod = 1;

    for (int i = nums.length - 1; i >= 0; i--) {
      prod *= nums[i];
      maxi = Math.max(prod, maxi);
      if (prod == 0) prod = 1;
    }

    return maxi;
  }
}
```
### 2) 
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В этом подходе мы проходимся по массиву в цикле запоминая максимальное и минимальное произведение, т.к. как только попадаем на отрицательное число, они меняются местами. Если попадаем на ноль, то `max` и `min` обнуляются, но на следующем шаге они обновляются. Также постоянно обновляется ответ.
#### Код
```java
class Solution {
    public int maxProduct(int[] nums) {
        
        int max = nums[0], min = nums[0], ans = nums[0];
        int n = nums.length;
        
        for (int i = 1; i < n; i++) {
        
			// Swapping min and max
            if (nums[i] < 0){
                int temp = max;
                max = min;
                min = temp;
            }             
            max = Math.max(nums[i], max * nums[i]);
            min = Math.min(nums[i], min * nums[i]);
            
            ans = Math.max(ans, max);
        }
        
        return ans;

    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/maximum-product-subarray/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=lXVy6YWFcRM)
- [leetcode 3 решения](https://leetcode.com/problems/maximum-product-subarray/solutions/1608862/java-3-solutions-detailed-explanation-using-image/)
- [leetcode решение Кадане](https://leetcode.com/problems/maximum-product-subarray/solutions/3321410/c-kadane-s-algo-full-explanation/)