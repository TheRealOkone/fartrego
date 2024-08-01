2024-07-29 16:04
Tags: #z

___
# Решение
### 1) [[Moore Voting Algorithm]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Проходимся по массиву и считаем "ценность" кандидата, если встречается такой же элемент то увеличиваем, иначе уменьшаем. Если же становится нулем, значит такой элемент не может быть мажоритарным.
Даже если мажоритарный элемент имеет только `n/2` алгоритм все-равно будет работать.
#### Код
```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int candidate = 0;
        
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            
            if (num == candidate) {
                count++;
            } else {
                count--;
            }
        }
        
        return candidate;
    }
}
```
### 2) [[HashMap]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Считаем числа, и получаем наибольший.
#### Код
```java
class Solution {
    public int majorityElement(int[] nums) {
        int n = nums.length;
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) map.merge(num, 1, Integer::sum);
        return Collections.max(map.entrySet(), Map.Entry.comparingByValue()).getKey();
    }
}
```

### 3) [[HashMap]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Считаем числа, и получаем наибольший.
#### Код
```java
class Solution {
    public int majorityElement(int[] nums) {
        int n = nums.length;
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) { 
            int tmp = map.getOrDefault(num,0);
            tmp++;
            map.put(num, tmp);
            if (tmp>n/2) return num;
        }
        return -1;

    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()