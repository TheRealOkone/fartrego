2024-06-27 16:08
Tags: #z

___
# Решение
### 1)
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
![[Tinkoff junior ex 2 img.png]]
#### Код
```java
public class tk23 {  
    public static void main(String[] args) {  
        draw(5,7);  
    }  
  
    private static void draw(int n, int m) {  
        int counter = 1;  
        int[][]mtx = new int[m][n];  
        int x=0, y=0;  
        int mid = Math.min(n,m);  
        for (int i = 1; i <= m*n; i++) {  
            mtx[y][x] = counter;  
            counter++;  
            if (x == 0 || y == m-1) {  
                if (x+y+2>mid) {  
                    y = x+y+2-mid;  
                    x = n-1;  
                } else {  
                    x= y+1;  
                    y=0;  
                }  
  
            } else {  
                x--;  
                y++;  
            }  
            }  
  
        for (int[] row : mtx) System.out.println(Arrays.toString(row));  
    }  
  
    private static boolean checkIfInBounds(int x, int y, int[][] mtx) {  
        try {  
            int tmp = mtx[y][x];  
            return true;        } catch (ArrayIndexOutOfBoundsException e) {  
            return false;  
        }  
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
- [[Задачи от Tinkoff для Junior Java developers]]