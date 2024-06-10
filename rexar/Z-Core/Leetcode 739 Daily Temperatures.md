2024-06-07 22:40
Tags: #z

___
# Решение
### 1) [[Stack]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
В решении используется стек, который хранит в себе даты. Значения хранятся в таком порядке, что температуры монотонно убывают. На каждом шаге прохода по температурам у нас идет проверка, на то прервется ли монотонность с добавлением нового элемента, если да, то из стека достаются значения пока он не вернется к монотонности. Т.к. хранятся даты, мы и получаем результат для дня.
#### Код
```java
class Solution {

    public int[] dailyTemperatures(int[] temperatures) {
        int[] ans = new int[temperatures.length];
        Stack<Integer> stack = new Stack<>();
        for (int currDay = 0; currDay < temperatures.length; currDay++) {
            while (
                !stack.isEmpty() &&
                temperatures[currDay] > temperatures[stack.peek()]
            ) {
                int prevDay = stack.pop();
                ans[prevDay] = currDay - prevDay;
            }
            stack.add(currDay);
        }
        return ans;
    }
}

```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/daily-temperatures/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=cTBiBSnjO3c)