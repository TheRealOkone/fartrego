2024-06-20 22:43
Tags: #z

___
# Решение
### 1) [[Greedy]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
![[Leetcode 45 img.png]]
На каждом шаге, определяется максимальный дальный элемент до которого можно допрыгнуть с предыдущего прыжка, таким образом мысленно массив делится на отрезки, куда за какое число прыжков можно допрыгнуть.
#### Код
```java
class Solution {
  public int jump(int[] nums) {
    int res = 0, r = 0, l = 0, farthest = 0;

    while (r < nums.length - 1) {
      farthest = 0;
      for (int i = l; i <= r; i++) farthest = Math.max(farthest, i + nums[i]);
      l = r + 1;
      r = farthest;
      res++;
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
- [leetcode задача](https://leetcode.com/problems/jump-game-ii/submissions/)
- [neetcode видео решения](https://www.youtube.com/watch?v=dJ7sWiOoK7g)