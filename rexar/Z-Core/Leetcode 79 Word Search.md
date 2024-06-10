2024-05-30 21:25
Tags: #z

___
# Решение
### 1) [[Backtracking]] && [[Recursion]]
Сложность: `O(m*n*4^len(word)))`
Память: `O(1)`
#### Объяснение
Проходимся по всем буквам, используя на каждой алгоритм [[Depth-first search (DFS)]], также используется трюк, что мы помечаем пройденные буквы, сдвигая их по ASCII таблице за пределы алфавита.
#### Код
```java
//This is a typical backtracking problem similar to Number of Islands.
//In number of Isalnds, we sinked the islands. Here, we will do the same by adding changing the value of the char.
//I added 100 because it will exceed the ascii limit for characters and will change it to some ascii value which is not an alphabet.

class Solution {

    public boolean exist(char[][] board, String word) {
        int m = board.length;
        int n = board[0].length;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (check(board, word, i, j, m, n, 0)) {
                    return true;
                }
            }
        }
        return false;
    }

    public boolean check(
        char[][] board,
        String word,
        int i,
        int j,
        int m,
        int n,
        int cur
    ) {
        if (cur >= word.length()) return true;
        if (
            i < 0 ||
            j < 0 ||
            i >= m ||
            j >= n ||
            board[i][j] != word.charAt(cur)
        ) return false;
        boolean exist = false;
        if (board[i][j] == word.charAt(cur)) {
            board[i][j] += 100;
            exist =
                check(board, word, i + 1, j, m, n, cur + 1) ||
                check(board, word, i, j + 1, m, n, cur + 1) ||
                check(board, word, i - 1, j, m, n, cur + 1) ||
                check(board, word, i, j - 1, m, n, cur + 1);
            board[i][j] -= 100;
        }
        return exist;
    }
}
```
### 2) Эффективное
Сложность: `O(m*n*4^len(word))`
Память: `O(1)`
#### Объяснение
С самого начала проверяется, если у нас слово длиннее, чем количество букв в матрице.
Дальше считается "частота" букв в `boardf (board freq)`, после проходимся по буквам `word` и уменьшаем счетчик частоты на 1 за каждую букву, а также проверяем стал ли счетчик меньше 0 (если меньше 0, тогда в матрице не хватает букв для сбора).
Далее сравнивается количество излишних букв первой и последней буквы слова, чтобы определить с какого конца будет эффективней начать собирать слово (чем меньше первичных входов в алгоритм [[Depth-first search (DFS)|dfs]], тем быстрее конечный алгоритм).
После всех оптимизаций используется алгоритм [[Depth-first search (DFS)|dfs]] с поиском во все 4 стороны.

#### Код
```java
class Solution {
public boolean exist(char[][] board, String word) {
        int m = board.length, n = board[0].length;
        if (m*n < word.length())
            return false;
        char[] wrd = word.toCharArray();
        int[] boardf = new int[128];
        for (int i = 0; i < m; ++i)
            for (int j = 0; j < n; ++j)++boardf[board[i][j]];

        for (char ch : wrd)
            if (--boardf[ch] < 0)
                return false;
        
        if (boardf[wrd[0]] > boardf[wrd[wrd.length - 1]])reverse(wrd);

        for (int i = 0; i < m; ++i){
            for (int j = 0; j < n; ++j)
                if (wrd[0] == board[i][j] && found(board, i, j, wrd, new boolean[m][n], 0))
                    return true;
        }
        return false;
    }

    private void reverse(char[] word){
        int n = word.length;
        for (int i = 0; i < n/2; ++i){
            char temp = word[i];
            word[i] = word[n - i - 1];
            word[n - i - 1] = temp;
        }
    }

    private static final int[] dirs = {0, -1, 0, 1, 0};
    private boolean found(char[][] board, int row, int col, char[] word, boolean[][] visited, int index){
        if (index == word.length)
            return true;
        if (row < 0 || col < 0 || row == board.length || col == board[0].length
            || board[row][col] != word[index] || visited[row][col])
            return false;
        visited[row][col] = true;
        for (int i = 0; i < 4; ++i){
            if (found(board, row + dirs[i], col + dirs[i + 1], word, visited, index + 1))
                return true;
        }
        visited[row][col] = false;
        return false;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/word-search/description/)
- [neetcode видео решения](https://youtu.be/pfiQ_PS1g8E)