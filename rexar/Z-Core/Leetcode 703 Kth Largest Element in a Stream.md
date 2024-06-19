2024-06-10 11:31
Tags: #z

___
# Решение
### 1) [[Heap OR Priority Queue]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Создается приоритетная очередь размером с `k`, которая в данном случае позволяет хранить числа в отсортированном виде, имея дубликаты.
Пока очередь не забита до краев, элементы просто добавляются. Иначе проверяется является ли новый элемент больше минимального в очереди, если да, то минимальный выкидывается, а новый добавляется.
В итоге возвращается минимальный элемент очереди, т.к. у нас очередь размера `k`.
#### Код
```java
class KthLargest {

  final PriorityQueue < Integer > heap = new PriorityQueue < > ();
  final int k;

  public KthLargest(int k, int[] nums) {
    this.k = k;
    for (int n: nums) add(n);
  }

  public int add(int val) {
    if (heap.size() < k) heap.offer(val); //for adding the values of the array
    else if (val > heap.peek()) {
      heap.poll(); //remove the top element
      heap.add(val); //add the new element
    }
    return heap.peek();
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/kth-largest-element-in-a-stream/description/)
- [neetcode видео решения](https://youtu.be/hOjcdrqMoQ8)