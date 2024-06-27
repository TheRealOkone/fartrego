2024-06-21 17:53
Tags: #z

___
# Решение
### 1) [[Greedy]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В самом начале считается сумма топлива и сумма стоимость поездки по кругу. Если стоимость выше количества топлива, значит точно нельзя проехать никак.
Дальше ищется индекс станции, с которой нужно начать движение (она уникальна по условию).
В цикле собираем остаток топлива после поездок, если остается отрицательное кол-во топлива, то значит со станции ранее невозможно объехать круг, и предполагаем, что следующий индекс нужный, и так повторить.
#### Код
```java
class Solution {

  public int canCompleteCircuit(int[] gas, int[] cost) {
    int sGas = 0, sCost = 0, res = 0, total = 0;
    for (int i = 0; i < gas.length; i++) {
      sGas += gas[i];
      sCost += cost[i];
    }
    if (sGas < sCost) return -1;
    for (int i = 0; i < gas.length; i++) {
      total += gas[i] - cost[i];
      if (total < 0) {
        total = 0;
        res = i + 1;
      }
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
- [leetcode задача](https://leetcode.com/problems/gas-station/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=lJwbPZGo05A)