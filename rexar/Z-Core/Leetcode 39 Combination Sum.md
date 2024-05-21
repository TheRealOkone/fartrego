2024-05-21 12:19
Tags: #z

___
# Решение
### 1) [[Backtracking]] && [[Recursion]]
Сложность: `O(2^k)`
Память: `O(k)`
#### Объяснение
Используя рекурсию, каждый раз принимается 2 решения:
1) Левая ветка - добавляем выбранный элемент в комбинацию.
2) Не добавляем ничего и меняем выбираемый элемент (больше мы к нему не вернемся).
Если `target` равняется 0, то записываем комбинацию в ответ. Если же `target` меньше 0 (сумма переполнена), или индекс вышел за пределы массива, то ветка отбраковывается.
![[Leetcode 39 neetcode.png]]
#### Код
```java
class Solution {

    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        List<Integer> cur = new ArrayList();
        backtrack(candidates, target, ans, cur, 0);
        return ans;
    }

    public void backtrack(
        int[] candidates,
        int target,
        List<List<Integer>> ans,
        List<Integer> cur,
        int index
    ) {
        if (target == 0) {
            ans.add(new ArrayList(cur));
        } else if (target < 0 || index >= candidates.length) {
            return;
        } else {
            cur.add(candidates[index]);
            backtrack(candidates, target - candidates[index], ans, cur, index);

            cur.remove(cur.get(cur.size() - 1));
            backtrack(candidates, target, ans, cur, index + 1);
        }
    }
}
```
### 2) [[Backtracking]] && [[Recursion]] наше
Сложность: `O(n^k)` вообще не понятно
Память: `O(k)` 
#### Объяснение
Используя рекурсию, перебираем кандидатов, пропуская "пройденную часть (левую часть)" и спускаемся на новый уровень рекурсии обновляя `border` - индекс границы "пройденной части", `target` - сумма которую надо добрать, и `cur` - комбинация данной ветки. Если передаваемый `target` будет меньше 0, то сумма переполнилась и ветка отбраковывается. Если `target` равен 0, то записываем комбинацию в результат. Иначе повторяем рекурсию.

#### Код
```java
class Solution {

  Set < List < Integer >> res = null;
  int[] can;

  public List < List < Integer >> combinationSum(int[] candidates, int target) {
    res = new HashSet < > ();
    can = candidates;
    rec(0, target, new ArrayList < Integer > ());
    return new ArrayList < > (res);
  }

  public void rec(int border, int target, List < Integer > cur) {
    if (target < 0) return;
    if (target == 0) {
      res.add(new ArrayList < > (cur));
      return;
    }
    for (int i = border; i < can.length; i++) {
      int dig = can[i];
      cur.add(dig);
      rec(i, target - dig, cur);
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
- [leetcode задача](https://leetcode.com/problems/combination-sum/submissions/1110868889/)
- [neetcode видео решения](https://www.youtube.com/watch?v=GBKI9VSKdGg)