2024-07-12 18:18
Tags: #z

___
# Решение
### 1) [[Linked List]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
Первый цикл складывает цифры по позициям у обоих узлов списка, пока один из списков не кончится.
Далее мы определяем у какого списка остались цифры и выбираем его для работы во втором цикле.
Во втором цикле делается все то же самое, что и в первом, только с учетом переполнения разряда.
В конце идет проверка на переполнения разряда последней цифры.
#### Код
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int prev = 0;
        ListNode root = l1;
        ListNode prevNode = new ListNode(0);
        while (l1 != null && l2 != null) {
            int cur = l1.val + l2.val + prev;
            prev = cur / 10;
            cur %= 10;
            l1.val = cur;
            prevNode = l1;
            l1 = l1.next;
            l2 = l2.next;
        }

        ListNode curNode = prevNode;
        if (l2 != null) curNode.next = l2;
        curNode = curNode.next;

        while (curNode != null) {
            int cur = curNode.val + prev;
            prev = cur / 10;
            cur %= 10;
            curNode.val = cur;
            prevNode = curNode;
            curNode = curNode.next;
        }

        if (prev != 0) prevNode.next = new ListNode(prev);

        return root;
    }
}
```
### 2) [[Linked List]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
В цикле условием выхода является, что мы дошли до конца всех списков и у нас нет переполнения разряда.
В цикле создается новый список с результатом, ситуации с получением данных от **null** обрабатывается с помощью тернарных операторов.
#### Код
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode tail = dummyHead;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int digit1 = (l1 != null) ? l1.val : 0;
            int digit2 = (l2 != null) ? l2.val : 0;

            int sum = digit1 + digit2 + carry;
            int digit = sum % 10;
            carry = sum / 10;

            ListNode newNode = new ListNode(digit);
            tail.next = newNode;
            tail = tail.next;

            l1 = (l1 != null) ? l1.next : null;
            l2 = (l2 != null) ? l2.next : null;
        }

        ListNode result = dummyHead.next;
        dummyHead.next = null;
        return result;
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/add-two-numbers/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=wgFPrzTjm7s)