2024-06-06 22:18
Tags: #z

___
# Решение
### 1)[[Tries (Prefix Tree)]]
#### Объяснение
Реализуем структуру [[Tries (Prefix Tree)|Trie]] через дерево, используя [[HashMap]] с ключем - буквой, значение - нодой с мапой на другие буквы. 
Корень дерева - пустышка, которая имеет ссылка на первые буквы слов. Цельное слово помечается пробелом (пустышкой) в конце.
Поиск работает рекурсивно проходясь по узлам, и проверяя имеется ли пробел/пустышка в конце. А префикс слова без этой проверки.
#### Код
```java
class Trie {
  Map < Character, Trie > map;
  public Trie() {
    map = new HashMap < > ();
  }

  public void insert(String word) {
    Trie tr = new Trie();
    if (word.length() < 1) {
      map.putIfAbsent(' ', tr);
      return;
    }
    Trie tmp = map.putIfAbsent(word.charAt(0), tr);
    if (tmp != null) tr = tmp;
    tr.insert(word.substring(1));
  }

  public boolean search(String word) {
    if (word.length() < 1) return map.get(' ') != null;
    Trie tr = map.get(word.charAt(0));
    if (tr != null) return tr.search(word.substring(1));
    return false;
  }

  public boolean startsWith(String prefix) {
    if (prefix.length() < 1) return true;
    Trie tr = map.get(prefix.charAt(0));
    if (tr != null) return tr.startsWith(prefix.substring(1));
    return false;
  }
}
```

### 2)Neetcode
#### Объяснение
То же самое, но по-другому. Нода выделяется в отдельный класс, вместо мапы используется массив, индексом которого является порядок буквы в алфавите. Конец слова помечается не пустышкой, а флагом `isWord`.
#### Код
```java
class Trie {

    Node root;

    public Trie() {
        root = new Node('\0'); //dummy node
    }

    public void insert(String word) {
        Node curr = root;
        for (char x : word.toCharArray()) {
            if (curr.children[x - 'a'] == null) {
                curr.children[x - 'a'] = new Node(x);
            }
            curr = curr.children[x - 'a'];
        }
        curr.isWord = true;
    }

    public boolean search(String word) {
        Node res = getLast(word);
        return (res != null && res.isWord);
    }

    //helper method
    public Node getLast(String word) {
        Node curr = root;
        for (char x : word.toCharArray()) {
            if (curr.children[x - 'a'] == null) {
                return null;
            }

            curr = curr.children[x - 'a'];
        }
        return curr;
    }

    public boolean startsWith(String prefix) {
        Node res = getLast(prefix);
        return res != null;
    }

    class Node {

        private char value;
        private boolean isWord;
        private Node[] children;

        public Node(char val) {
            this.value = val;
            this.isWord = false;
            this.children = new Node[26];
        }
    }
}

```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/implement-trie-prefix-tree/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=oobqoCJlHA0)
- [leetcode решение](https://leetcode.com/problems/implement-trie-prefix-tree/solutions/3305783/easy-solutions-in-java-python-and-c-look-at-once/)