2024-07-16 21:54
Tags: #z

___
# Решение
### 1) [[Two Pointers]]
Сложность: `O(n^2)`
Память: `O(1)`
#### Объяснение
Проходимся по каждой букве в цикле и определяем центр. Центр палиндрома задается границами с помощью указателей `l` и `r`. Центр может быть нечетным, а может быть четным, если он четный, то указатель `r` будет сдвинут на 1 вправо. Дальше наращивается палиндром: указатель `l` и `r` двигаются на 1 шаг от центра и проверяется, являются ли буквы на их местах равными.
- если нет, то двигаем центр и начинаем наращивать заново. 
- если да, то проверяем является ли палиндром максимальным, а также продолжаем наращивать.


#### Код
```java
class Solution {
  public String longestPalindrome(String s) {
    String res = "";
    int resLength = 0;
    int resLeftIdx = 0, resRightIdx = 0;
    for (int i = 0; i < s.length(); i++) {
        // odd length
        int l = i, r = i;
        while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
            if (r-l+1 > resLength) {
                resLength = r-l+1;
                resLeftIdx = l;
                resRightIdx = r;
            }
            l--;
            r++;
        }

        // even length
        l = i;
        r = i+1;
        while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
            if (r-l+1 > resLength) {
                resLength = r-l+1;
                resLeftIdx = l;
                resRightIdx = r;
            }
            l--;
            r++;
        }

    }
    return s.substring(resLeftIdx, resRightIdx + 1);
  }

}
```

### 2) [[Manacher's Algorithm]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
[[00 TODO]]
### Intuition :
**To avoid the unnecessary validation of palindromes, we can use Manacher's algorithm. The algorithm is explained brilliantly in this article. The idea is to use palindrome property to avoid unnecessary validations. We maintain a center and right boundary of a palindrome. We use previously calculated values to determine if we can expand around the center or not. If we can expand, we expand and update the center and right boundary. Otherwise, we move to the next character and repeat the process. We also maintain a variable max_len to keep track of the maximum length of the palindrome. We also maintain a variable max_str to keep track of the maximum substring.**

#### Algorithm :
We initialize a boolean table dp and mark all the values as false.
We will use a variable max_len to keep track of the maximum length of the palindrome.
We will iterate over the string and mark the diagonal elements as true as every single character is a palindrome.
Now, we will iterate over the string and for every character we will expand around its center.
For odd length palindrome, we will consider the current character as the center and expand around it.
For even length palindrome, we will consider the current character and the next character as the center and expand around it.
We will keep track of the maximum length and the maximum substring.
Print the maximum substring.
#### Complexity Analysis
Time complexity : O(n). Since expanding a palindrome around its center could take O(n) time, the overall complexity is O(n).

Space complexity : O(n). It uses O(n) space to store the table.
#### Код
```java
public class Solution {
    public String longestPalindrome(String s) {
        if (s.length() <= 1) {
            return s;
        }

        int maxLen = 1;
        String maxStr = s.substring(0, 1);
        s = "#" + s.replaceAll("", "#") + "#";
        int[] dp = new int[s.length()];
        int center = 0;
        int right = 0;

        for (int i = 0; i < s.length(); i++) {
            if (i < right) {
                dp[i] = Math.min(right - i, dp[2 * center - i]);
            }

            while (i - dp[i] - 1 >= 0 && i + dp[i] + 1 < s.length() && s.charAt(i - dp[i] - 1) == s.charAt(i + dp[i] + 1)) {
                dp[i]++;
            }

            if (i + dp[i] > right) {
                center = i;
                right = i + dp[i];
            }

            if (dp[i] > maxLen) {
                maxLen = dp[i];
                maxStr = s.substring(i - dp[i], i + dp[i] + 1).replaceAll("#", "");
            }
        }

        return maxStr;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/longest-palindromic-substring/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=XYQecbcd6_c)