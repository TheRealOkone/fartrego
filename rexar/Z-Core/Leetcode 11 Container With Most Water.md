2024-07-17 19:16
Tags: #z

___
# Решение
### 1) [[Two Pointers]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Используем два указателя `l` и `r` для хранения максимальной высоты с каждой стороны. Сравниваем максимумы, и начинаем "сжимать" емкость с той стороны, где максимум ниже. Сжимаем до тех пор, пока не найдется высота выше локального максимума. Дальше пересчитываем площадь воды и продолжаем сжимать, пока стенки не "схлопнутся".
>[!info]-
>у нас уже есть максимальная площадь с этой высотой — поскольку это нижний указатель, это означает, что каждое следующее расстояние, которое ближе, всегда будет меньшим расстоянием с той же или меньшей высотой, что означает меньшую площадь.
Поэтому нам не нужно просматривать все остальные комбинации с этим указателем.
#### Код
```java
class Solution {
    public int maxArea(int[] height) {
        int n = height.length;
        int l = 0, r = n-1;
        int maxSqr = -1;
        int lMax = height[l];
        int rMax = height[r];
        while (l < r) {
            int range = r-l;
            int lowestH = Math.min(lMax, rMax);
            maxSqr = Math.max(maxSqr, range*lowestH);
            if (lMax <= rMax) {
                l++;
                while (lMax > height[l] && l < r) {
                    l++;
                }
                lMax = height[l];
            } else {
                r--;
                while (rMax > height[r] && l < r) {
                    r--;
                }
                rMax = height[r];
            }
        }

        return maxSqr;
        
    }
}
```
### 2) [[Two Pointers]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Так же как и в [[#1) Two Pointers| 1 решении]], только короче, но и работает медленее, так как пересчет площади происходит на каждом сдвиге стенки.
#### Код
```java
class Solution {
    public int maxArea(int[] height) {
        int l = 0;
        int r = height.length - 1;
        int maxArea = 0;

        while (l < r) {
            int lowest = Math.min(height[l], height[r]);
            int range = r - l;
            int currentArea = lowest*range;
            maxArea = Math.max(maxArea, currentArea);

            if (height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }

        return maxArea;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/container-with-most-water/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=UuiTKBwPgAo)