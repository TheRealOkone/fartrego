2024-04-18 19:37
Tags: #z

___
# Решение
### 1)
Сложность: `O(n log n)`
Память: `O(1)`
#### Объяснение
1. Инициализировать левый и правый указатели: `left = 1` и `right = maximum number of bananas in any pile`. P.S. можно сделать `right = 1000000000`, т.к. размер кучки по условию ограничен `10^9`
2. Пока левый указатель меньше правого, повторите следующие действия:
	1.  Вычислите средний указатель, используя `mid = (left + right) / 2`
	2. Проверьте, может ли Коко съесть все бананы на текущей скорости (средний указатель) в пределах `h` часов, используя метод `canEatAll`
	3. Если Коко может съесть все бананы с текущей скоростью, обновите правый указатель на средний, используя `right = mid`
	4. Если Коко не может съесть все бананы с текущей скоростью, переместите левый указатель на `mid+1`
3. Когда левый указатель сравняется с правым, верните левый указатель в качестве минимальной скорости, с которой Коко сможет съесть все бананы в течение часа. Метод `canEatAll` вычисляет общее время, необходимое для поедания всех куч с заданной скоростью. Если общее время больше `h`, метод возвращает `false`, в противном случае он возвращает `true`.
#### Код
```java
class Solution {
  public int minEatingSpeed(int[] piles, int h) {
    int n = piles.length;
    int left = 1, right = IntStream.of(piles).max().getAsInt();
    while (left < right) {
      int mid = (left + right) / 2;
      if (canEatAll(piles, mid, h)) right = mid;
      else left = mid + 1;
    }
    return left;
  }

  private boolean canEatAll(int[] piles, int speed, int h) {
    int time = 0;
    for (int pile: piles) {
      time += Math.ceilDiv(pile, speed); // calculate the time required to eat this pile
      if (time > h) {
        return false; // if the total time is greater than h, return false
      }
    }
    return true; // if all piles can be eaten within h hours, return true
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