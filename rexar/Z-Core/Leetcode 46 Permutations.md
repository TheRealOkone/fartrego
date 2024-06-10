2024-05-21 17:17
Tags: #z

___
# Решение
### 1) [[Backtracking]] && [[Recursion]]
Сложность: `O(n)`
Память: `O(n!)`
#### Объяснение
Используя рекурсию, собираем комбинации перестановок. Если индекс `start` дошел до конца массива, то комбинация собрана и добавляется в результат. 
В обычном же случае, в цикле вызывается другая рекурсия, где при переходе на уровень ниже меняется местами элемент под индексом `start` (первый для своего уровня рекурсии) с каждым последующим "справа".
#### Код
```java
class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        function(ans, nums, 0);
        return ans;
    }

    public void function(List<List<Integer>> ans, int[] arr, int start) {
        if (start == arr.length) {
            List<Integer> list = new ArrayList();
            for (int i = 0; i < arr.length; i++) list.add(arr[i]);
            ans.add(list);
            return;
        }

        for (int i = start; i < arr.length; i++) {
            swap(arr, start, i);
            function(ans, arr, start + 1);
            swap(arr, start, i);
        }
    }

    public void swap(int[] arr, int a, int b) {
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
}
```
### 2) [[Backtracking]] && [[Recursion]] наше
Сложность: `O(n^3)`
Память: `O(n!)`
#### Объяснение
Используя рекурсию собираются комбинации перестановок. Если размер текущий комбинации равен размеру входного массива, то комбинация собрана и записываем в результат. Иначе вызываем рекурсию используя все оставшиеся цифры через цикл.

#### Код
```java
class Solution {

  List < List < Integer >> res = null;
  int k = 0;
  public List < List < Integer >> permute(int[] nums) {
    res = new ArrayList < > ();
    k = nums.length;
    rec(nums, new ArrayList < > ());
    return res;
  }

  public void rec(int[] nums, List < Integer > cur) {
    if (cur.size() == k) {
      res.add(new ArrayList < > (cur));
      return;
    }
    for (int i = 0; i < nums.length; i++) {
      cur.add(nums[i]);
      rec(removeElement(nums, i), cur);
      cur.remove(cur.get(cur.size() - 1));
    }
    return;
  }

  public int[] removeElement(int[] arr, int removedIdx) {
    int[] res = new int[arr.length - 1];
    for (int i = 0; i < removedIdx; i++) {
      res[i] = arr[i];
    }
    for (int i = removedIdx + 1; i < arr.length; i++) {
      res[i - 1] = arr[i];
    }
    return res;
  }

}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/permutations/)
- [neetcode видео решения](https://youtu.be/s7AvT7cGdSo)