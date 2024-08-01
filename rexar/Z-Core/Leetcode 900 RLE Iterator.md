2024-07-24 21:44
Tags: #z

___
# Решение
### 1) Чистое
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение

#### Код
```java
class RLEIterator {
    int index;
    int[] encoding;
    public RLEIterator(int[] encoding) {
        index = 0;
        this.encoding = encoding;
    }
    
    public int next(int n) {
        while (index < encoding.length && n > encoding[index]) {
            n -= encoding[index];
            index += 2;
            
        }
        if (index >= encoding.length) {
            return -1;
        }
        encoding[index] -= n;
        return encoding[index + 1]; 
    }
}
```

### 2) Наше (чуть по-другому)
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение

#### Код
```java
class RLEIterator {

    int curIdx;
    int[] enc;

    public RLEIterator(int[] encoding) {
        enc = encoding;
        curIdx = 0;
    }
    
    public int next(int n) {
        int last = -1;
        while (n != 0) {
            if (curIdx >= enc.length) return -1;
            int cur = enc[curIdx];
            if (cur == 0) {
                curIdx+=2;
                continue;
            }
            if (n > cur) {
                n-=cur;
                enc[curIdx] = 0;
            } else {
                enc[curIdx] = cur-n;
                n = 0;
            }
            
            last = enc[curIdx+1];
        }
        return last;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/rle-iterator/description/)
- [neetcode видео решения]()