2024-06-19 23:01
Tags: #z

___
# Решение
### 1) [[Greedy]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Идем с конца в начало, двигая целевой индекс, если с этого индекса возможно достичь конца.
#### Код
```java
class Solution {
  public boolean canJump(int[] nums) {
    int goal = nums.length - 1;
    for (int i = nums.length - 2; i >= 0; i--) {
      if (nums[i] + i >= goal) {
        goal = i;
      }
    }
    return goal == 0;
  }
}
```
### 2) [[Dynamic Programming]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Мы начинаем пробовать прыгать с самый длинных прыжков, если мы не можем таким образом достичь конца, мы уменьшаем дистанцию прыжка. Каждый прыжок является рекурсией, и мы [[Memoization|запоминаем]] уже посещенные индексы, так как их нет смысла пересчитывать.
#### Код
```java
class Solution {
  boolean res = false;
  boolean[] visited;
  public boolean canJump(int[] nums) {
    visited = new boolean[nums.length];
    rec(nums, 0);
    return res;
  }
  public void rec(int[] nums, int idx) {
    if (res) return;

    if (idx >= nums.length - 1) {
      res = true;
      return;
    }
    visited[idx] = true;
    int i = idx + nums[idx];
    if (i > nums.length - 1) i = nums.length - 1;
    for (; i > idx; i--) {
      if (visited[i]) break;
      rec(nums, i);
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
- [leetcode задача](https://leetcode.com/problems/jump-game/submissions/1293923430/)
- [neetcode видео решения](https://www.youtube.com/watch?v=Yan0cv2cLy8)