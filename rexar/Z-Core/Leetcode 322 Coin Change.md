2024-06-03 22:30
Tags: #z

___
# Решение
### 1) [[Dynamic Programming]] Bottom-up
Сложность: `O(amount * len(coins))`
Память: `O(amount)`
#### Объяснение
Главная идея - в том что мы решаем более простые подзадачи, т.е. мы считаем количество монет, для суммы в 0, 1, 2 и далее. После для более крупных сумм мы ссылаемся на результаты предыдущих вычислений.
Пример по фото ниже.
![[Leetcode 322 img.png]]
Так как мы ищем минимум, нужно массив проинициализировать `amount+1`. Также в цикле мы пытаемся собрать "по монетке", ссылаясь на предыдущие решения.
#### Код
```java
class Solution {
  public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, amount + 1);
    dp[0] = 0;

    for (int i = 1; i < amount + 1; i++) {
      for (int coin: coins) {
        if (i - coin >= 0) {
          dp[i] = Math.min(dp[i], 1 + dp[i - coin]);
        }
      }
    }

    return dp[amount] != amount + 1 ? dp[amount] : -1;
  }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/coin-change/)
- [neetcode видео решения](https://youtu.be/H9bfqozjoqs)