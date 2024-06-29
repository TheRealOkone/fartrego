2024-05-12 23:56
Tags: #

___
## Обход графа в ширину
![[Breadth-First-Search-Algorithm.gif]]

1. Поместить узел, с которого начинается поиск, в изначально пустую очередь.
2. Извлечь из начала очереди узел u ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) и пометить его как развёрнутый.
    - Если узел u ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) является целевым узлом, то завершить поиск с результатом «успех».
    - В противном случае, в конец очереди добавляются все преемники узла u ![{\displaystyle u}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3e6bb763d22c20916ed4f0bb6bd49d7470cffd8) , которые ещё не развёрнуты и не находятся в очереди.
3. Если очередь пуста, то все узлы были просмотрены, следовательно, целевой узел недостижим из начального; завершить поиск с результатом «неудача».
4. Вернуться к п. 2.

```java
public static <T> Optional<Tree<T>> search(T value, Tree<T> root) {
	Queue<Tree<T>> queue = new ArrayDeque<>();
	queue.add(root);
	while(!queue.isEmpty()) {
	    Tree<T> currentNode = queue.remove();
	    if (currentNode.getValue().equals(value)) {
		    return Optional.of(currentNode);
		} else {
		    queue.addAll(currentNode.getChildren());
		}
	}
	return Optional.empty();
}
```

___
### Zero-Links


___
### Links
- [wiki](https://en.wikipedia.org/wiki/Breadth-first_search)