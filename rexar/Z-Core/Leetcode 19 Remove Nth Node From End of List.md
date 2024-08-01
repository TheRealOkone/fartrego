2024-07-17 22:51
Tags: #z

___
# Решение
### 1) Fast & Slow указатели
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Двигаем указатель `fast` на `n` узлов вперед, если он стал нулевым, значит удалить нужно "голову", так как она стоит на `n` уровне.
Далее в цикле двигаем указатели `slow` и `fast` вперед, до тех пор пока `fast` не упрется в конец. У `slow` перезаписывается связь на следующий элемент.
#### Код
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode fast = head, slow = head;
        for (int i = 0; i < n; i++) fast = fast.next;
        if (fast == null) return head.next;
        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }
        slow.next = slow.next.next;
        return head;
    }
}
```
### 2) Просчет глубины и узел пустышка 
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В рекурсии погружаемся до самого конца списка, и возвращаем уровень узла. Таким образом можно определить где нужно перезаписать ссылку.
Пустышка же нужна, чтобы перезаписать "голову", если на нее указывает `n`.

#### Код
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head.next == null) return null;
        ListNode dummy = new ListNode(0, head);
        deep(dummy, n);
        return dummy.next;
    }

    public int deep(ListNode prev, int n) {
        ListNode node = prev.next;
        if (node == null) return 0;
        if (node.next == null) {
            if (n == 1) prev.next = null;
            return 1;
        }
        int lvl = deep(node, n)+1;
        if (lvl == n) {
            prev.next = node.next;
        }
        return lvl;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=XVuQxVej6y8)