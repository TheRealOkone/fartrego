2024-07-29 15:43
Tags: #z

___
# Решение
### 1)
Сложность: `O(log n)`
Память: `O(1)`
#### Объяснение

#### Код
```java
class Solution {
    public int subtractProductAndSum(int n) {
        int l = 1;
        int r = 0;
        while (n != 0) {
            int c = n%10;
            n/=10;
            l*=c;
            r+=c;
        }
        return l-r;
    }
}
```
### 2)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение

#### Код

___
### Zero-Links
- 

___
### Links
- [leetcode задача]()
- [neetcode видео решения]()