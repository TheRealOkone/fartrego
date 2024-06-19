2024-06-11 10:57
Tags: #z

___
# Решение
### 1) [[Quick Select]] (Не работает на Leetcode)
Сложность: `O(n) - среднее` `O(n^2) - худшее`
Память: `O(1)`
#### Объяснение
Является более лучшим решением, чем [[#2) Heap OR Priority Queue|2]] т.к. не используется память вообще, и скорость в среднем лучше.
Берется случайный опорный элемент массива (в данном случае самый правый) и ставим числа меньше него - слева, а числа больше - справа, сам он таким образом становится в правильном позиции как-будто после сортировки. 
Если опорный элемент стоит на `k` - позиции, то это наш ответ (В случае если задача на поиск наименьшего, иначе `k` стоит представить как `размер массива - k`).
Иначе, тогда смотрим где находится опорный элемент относительно искомой позиции, и уже на сегмент слева или справа от него повторяем алгоритм.
#### Код
```java
class Solution {
  public int findKthLargest(int[] nums, int k) {
    k = nums.length - k;
    return quickSelect(nums, 0, nums.length - 1, k);
  }

  public int quickSelect(int[] nums, int l, int r, int k) {
    int pivot = partition(nums, l, r);
    if (pivot < k)
      return quickSelect(nums, pivot + 1, r, k);
    if (pivot > k)
      return quickSelect(nums, l, pivot - 1, k);
    else
      return nums[pivot];

  }

  public int partition(int[] nums, int l, int r) {
    int pivot = nums[r];
    int i = l;
    for (int j = i; j < r; j++) {
      if (nums[j] <= pivot) {
        swap(nums, i, j);
        i++;
      }
    }
    swap(nums, i, r);
    return i;
  }

  private void swap(int[] nums, int l, int r) {
    int tmp = nums[l];
    nums[l] = nums[r];
    nums[r] = tmp;
  }
}
```
### 2) [[Heap OR Priority Queue]]
Сложность: `O(n log n)`
Память: `O(k)`
#### Объяснение
Для того чтобы найти самый большой k-ый элемент в массиве, мы запихиваем его в приоритетную очередь, если очередь становится больше размера `k`, то элемент крайний элемент достается. После всего крайний элемент является ответом.
#### Код
```java
class Solution {
  public int findKthLargest(int[] nums, int k) {
    PriorityQueue < Integer > q = new PriorityQueue < > (Comparator.naturalOrder());
    for (int num: nums) {
      q.offer(num);
      if (q.size() > k) q.poll();
    }
    return q.poll();

  }
}
```
### 3) [[Quick Select]] (Работает на Leetcode)
Сложность: ``
Память: ``
#### Объяснение

#### Код
```java
class Solution {
  public int findKthLargest(int[] nums, int k) {
    List < Integer > list = new ArrayList();
    for (int num: nums) {
      list.add(num);
    }
    return quickSelect(list, k);
  }

  public int quickSelect(List < Integer > nums, int k) {
    int pivotIndex = new Random().nextInt(nums.size());
    int pivot = nums.get(pivotIndex);

    List < Integer > left = new ArrayList();
    List < Integer > mid = new ArrayList();
    List < Integer > right = new ArrayList();

    for (int num: nums) {
      if (num > pivot) {
        left.add(num);
      } else if (num < pivot) {
        right.add(num);
      } else {
        mid.add(num);
      }
    }
    if (k <= left.size()) return quickSelect(left, k);
    if (left.size() + mid.size() < k) return quickSelect(right, k - left.size() - mid.size());
    return pivot;
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [neetcode видео решения](https://youtu.be/XEmy13g1Qxc)