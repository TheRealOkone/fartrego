2024-07-24 20:16
Tags: #z

___
# Решение
### 1) [[Fast and Slow Pointers OR Floyd's Cycle-Finding Algorithm]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Двигаем один указатель на 1 шаг, другой на 2, если быстрый становится **null**, тогда цикла нет, если же указатели указывают на одну и ту же ноду, значит цикл есть.
#### Код
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow_pointer = head, fast_pointer = head;
        while (fast_pointer != null && fast_pointer.next != null) {
            slow_pointer = slow_pointer.next;
            fast_pointer = fast_pointer.next.next;
            if (slow_pointer == fast_pointer) {
                return true;
            }
        }
        return false;
    }
}
```

### 2) Visited nodes
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Ходим по списку и записываем пройденные ноды в [[Set]], если алгоритм проходится по пройденной ноде, то цикл имеется.
#### Код
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        HashSet<ListNode> visited_nodes = new HashSet<>();
        ListNode current_node = head;
        while (current_node != null) {
            if (visited_nodes.contains(current_node)) {
                return true;
            }
            visited_nodes.add(current_node);
            current_node = current_node.next;
        }
        return false;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/linked-list-cycle/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=gBTe7lFR3vc)