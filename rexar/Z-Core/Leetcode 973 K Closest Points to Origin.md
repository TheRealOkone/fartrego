2024-06-10 13:02
Tags: #z

___
# Решение
### 1)
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение

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
### 2)
Сложность: `O(n log k)`
Память: `O(n)`
#### Объяснение

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