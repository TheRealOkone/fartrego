2024-05-24 18:40
Tags: #z

___
# Решение
### 1) [[Backtracking]] && [[Recursion]]
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
Для того чтобы избавиться от дубликатов, предварительно отсортировывается входящих массив. Далее, используя рекурсию, мы идем по рекурсивному дереву по двум веткам.
1) Ответвление, где добавляется цифра на которую указывает индекс `start` и он сдвигается вправо
2) Ответвление, где мы в начале пропускаем все дубликаты, а также ничего не добавляем и сдвигаем индекс `start` вправо
#### Код
```java
// Similar to subsets 1. Here, we'll just take care of the duplicates.
class Solution {
  public List < List < Integer >> subsetsWithDup(int[] nums) {
    List < List < Integer >> res = new ArrayList < > ();
    Arrays.sort(nums);
    helper(nums, 0, new ArrayList < > (), res);
    return res;
  }

  public void helper(int[] nums, int start, List < Integer > cur, List < List < Integer >> res) {
    if (start == nums.length) {
      res.add(new ArrayList < > (cur));
      return;
    }

    cur.add(nums[start]);
    helper(nums, start + 1, cur, res);
    cur.remove(cur.size() - 1);

    while (start + 1 < nums.length && nums[start] == nums[start + 1]) start++;
    helper(nums, start + 1, cur, res);
    return;
  }
}
```
### 2) [[Backtracking]] && [[Recursion]]
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
Примерно то же самое что и [[#1) Backtracking && Recursion|1]]
#### Код
```java
// Similar to subsets 1. Here, we'll just take care of the duplicates.
class Solution {

    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        subSet(nums, 0, ans, list);
        return ans;
    }

    public void subSet(
        int[] nums,
        int idx,
        List<List<Integer>> ans,
        List<Integer> list
    ) {
        ans.add(new ArrayList<>(list));

        for (int i = idx; i < nums.length; i++) {
            //skip the duplicate elements
            if (i > idx && nums[i] == nums[i - 1]) continue;
            list.add(nums[i]);
            subSet(nums, i + 1, ans, list);
            list.remove(list.size() - 1);
        }
    }
}

```
### 3) [[Backtracking]] && [[Recursion]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Примерно то же самое что и [[#1) Backtracking && Recursion|1]]
#### Код
```java
class Solution {
  public List < List < Integer >> subsetsWithDup(int[] nums) {
    List < List < Integer >> res = new ArrayList < > ();
    Arrays.sort(nums);
    helper(nums, 0, new ArrayList < > (), res);
    return res;
  }

  public void helper(int[] nums, int start, List < Integer > cur, List < List < Integer >> res) {
    res.add(new ArrayList < > (cur));

    for (int i = start; i < nums.length; i++) {
      if (i > start && nums[i] == nums[i - 1]) continue;

      cur.add(nums[i]);
      helper(nums, i + 1, cur, res);
      cur.remove(cur.size() - 1);
    }
    return;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/subsets-ii/)
- [neetcode видео решения](https://www.youtube.com/watch?v=Vn2v6ajA7U0)