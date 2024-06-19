2024-06-10 13:02
Tags: #z

___
# Решение
### 1) [[Heap OR Priority Queue]]
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение
Создается очередь с приоритетом, где компаратором служит расстояние от центра до точки (Формула Пифагора без корня - для оптимизации). Далее просто пихаем все точки в очередь. В конце просто достаем `k` элементов из очереди и возвращаем как результат.
#### Код
```java
class Solution {
  public int[][] kClosest(int[][] points, int k) {
    PriorityQueue < int[] > q = new PriorityQueue < > (
      (a, b) ->
      (a[0] * a[0] + a[1] * a[1]) -
      (b[0] * b[0] + b[1] * b[1])
    );
    for (int[] pair: points) {
      q.offer(pair);
    }
    int[][] res = new int[k][2];
    for (int i = 0; i < k; i++) {
      res[i] = q.poll();

    }
    return res;
  }
}
```
### 2) [[Heap OR Priority Queue]]
Сложность: `O(n log k)`
Память: `O(k)`
#### Объяснение
То же самое что и [[#1) Heap OR Priority Queue|1 решение]], только очередь "отсортирована" в другом порядке, и если происходит переполнение очереди, то достается самый большой элемент. Очередь также не раздувается до `O(n)`.
#### Код
```java
class Solution {
  public int[][] kClosest(int[][] points, int k) {
    PriorityQueue < int[] > q = new PriorityQueue < > (
      (b, a) ->
      (a[0] * a[0] + a[1] * a[1]) -
      (b[0] * b[0] + b[1] * b[1])
    );
    for (int[] pair: points) {
      q.offer(pair);
      if (q.size() > k) q.remove();
    }
    int[][] res = new int[k][2];
    for (int i = 0; i < k; i++) {
      res[i] = q.poll();
    }
    return res;
  }
}
```

### 3) There are also some O(N) solutions using quicks select and binary search https://leetcode.com/problems/k-closest-points-to-origin/solution/

Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/k-closest-points-to-origin/description/)
- [neetcode видео решения](https://youtu.be/rI2EBUEMfTk)