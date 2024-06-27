2024-06-27 16:08
Tags: #z

___
# Решение
### 1)
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение

#### Код
```java
public class tk3 {  
    public static void main(String[] args) throws IOException {  
        z3();  
    }  
  
    public static void z3() throws IOException {  
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));  
        int m = Integer.parseInt(br.readLine());  
        int[] shelf = new int[m];  
        int tailIdx = 0;  
        PriorityQueue<Integer> pq = new PriorityQueue<>(Comparator.naturalOrder());  
  
        for (int i = 0; i < m; i++) {  
            StringTokenizer st = new StringTokenizer(br.readLine());  
            boolean isAdd = st.nextToken().charAt(0) == '+';  
            int val = Integer.parseInt(st.nextToken());  
            if (isAdd) {  
                if (!pq.isEmpty()) {  
                    int pqBlank = pq.poll();  
                    shelf[pqBlank] = val;  
                    System.out.println(pqBlank+1);  
                } else {  
                    shelf[tailIdx] = val;  
                    System.out.println(tailIdx+1);  
                    tailIdx++;  
                }  
            } else {  
                for (int j = 0; j < tailIdx; j++) {  
                    if (shelf[j] == val) {  
                        shelf[j] = 0;  
                        pq.add(j);  
                    }  
                }  
            }  
  
  
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