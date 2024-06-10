2024-05-24 20:30
Tags: #z

___
# Решение
### 1) [[Backtracking]] && [[Recursion]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
С самого начала требуется отсортировать массив, чтобы потом пропускать дубликаты.
Используя рекурсию, каждый раз принимается 2 решения:
1) Левая ветка - добавляем выбранный элемент в комбинацию и меняем выбираем элемент на следующий.
2) Правая ветка - не добавляем ничего, пропускаем дубликаты и меняем выбираемый элемент на следующий.
Если `target` равняется 0, то записываем комбинацию в ответ. Если же `target` меньше 0 (сумма переполнена), или индекс вышел за пределы массива, то ветка отбраковывается.
#### Код
```java
class Solution {
  public List < List < Integer >> combinationSum2(int[] candidates, int target) {
    Arrays.sort(candidates);
    List < List < Integer >> ans = new ArrayList < List < Integer >> ();
    List < Integer > cur = new ArrayList();
    backtrack(candidates, target, ans, cur, 0);
    return ans;
  }

  public void backtrack(
    int[] candidates,
    int target,
    List < List < Integer >> ans,
    List < Integer > cur,
    int index) {
    if (target == 0) {
      ans.add(new ArrayList(cur));
    } else if (target < 0 || index >= candidates.length) {
      return;
    } else {
      cur.add(candidates[index]);
      backtrack(candidates, target - candidates[index], ans, cur, index + 1);

      while (index + 1 < candidates.length && candidates[index] == candidates[index + 1]) index++;
      cur.remove(cur.get(cur.size() - 1));
      backtrack(candidates, target, ans, cur, index + 1);
    }
  }
}
```
### 2) [[Backtracking]] && [[Recursion]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
То же самое, что и [[#1) Backtracking && Recursion|1]], только для пропуска дубликатов и выбора следующего элемента используется цикл с проверкой на дубликаты.
#### Код
```java
class Solution {

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        List<Integer> ls = new ArrayList<Integer>();
        comb(candidates, target, ans, ls, 0);
        return ans;
    }

    public void comb(
        int[] candidates,
        int target,
        List<List<Integer>> ans,
        List<Integer> ls,
        int index
    ) {
        if (target == 0) {
            ans.add(new ArrayList(ls));
        } else if (target < 0) return; else {
            for (int i = index; i < candidates.length; i++) {
                if (i > index && candidates[i] == candidates[i - 1]) continue;
                ls.add(candidates[i]);
                comb(candidates, target - candidates[i], ans, ls, i + 1);
                ls.remove(ls.get(ls.size() - 1));
            }
        }
    }
}

```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/combination-sum-ii/)
- [neetcode видео решения](https://youtu.be/rSA3t6BDDwg)