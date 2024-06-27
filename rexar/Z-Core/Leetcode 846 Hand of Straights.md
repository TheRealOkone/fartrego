2024-06-23 19:24
Tags: #z

___
# Решение
### 1) [[HashMap]] Хорошее
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
[3 решение](https://leetcode.com/problems/hand-of-straights/editorial/#approach-3-reverse-decrement-most-optimal)
#### Код

### 2) [[HashMap]] (плохое)
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение
Если рука не разбивается на колоды нормально, то сразу возвращается `false`.
Если все ок, то считает количество карта по их значению. После берется множество ключей и сортируется. По нему проходимся и собираем каждую колоду, чтобы значения были последовательны (1,2,3 и т.д), иначе возвращается `false`. Если все окей, возвращаем `true`.
#### Код
```java
class Solution {
  public boolean isNStraightHand(int[] hand, int groupSize) {
    int n = hand.length;
    if (n % groupSize != 0) return false;
    int k = n / groupSize;
    Map < Integer, Integer > map = new HashMap < > ();
    for (int h: hand) {
      map.merge(h, 1, Integer::sum);
    }

    LinkedList < Integer > keys = new LinkedList < Integer > (map.keySet());
    keys.sort(Comparator.naturalOrder());
    for (int i = 0; i < k; i++) {
      int prev = 0;
      Iterator < Integer > it = keys.iterator();
      for (int j = 0; j < groupSize; j++) {
        if (!it.hasNext()) return false;
        Integer cur = it.next();
        int amount = map.get(cur);
        if (j > 0 && cur > prev + 1) return false;
        prev = cur;
        if (amount == 1) {
          it.remove();
          map.remove(cur);
        } else map.merge(cur, -1, Integer::sum);
      }
    }

    return true;
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