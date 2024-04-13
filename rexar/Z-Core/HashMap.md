2024-04-01 23:12
Tags: #z

___
# Описание
Класс `HashMap` является самой популярной коллекцией из всех словарей (`Map`). С одной стороны, он очень похож на HashSet и имеет все его методы.
Создать объект его типа можно:
```java
Map<KeyType, ValueType> name = new HashMap<>();
```
Время записи и поиска значения является `O(1)`, так как позиция элемента определяется с помощью [[HashCode]]
# Популярные методы
- **put(`K` key, `V` value)** - кладет значение с таким ключем.
- **putIfAbsent(`K` key, `V` value)** - кладет значение с таким ключем только, если оно отсутствует.
- **get(`Object` key)** - Возвращает значение, с которым сопоставлен указанный ключ, или значение null
- **getOrDefault(`Object` key, `V` defaultValue)** - Возвращает значение, с которым сопоставлен указанный ключ, или значение по умолчанию.
- **remove(`Object` key)** - удаляет значение с ключом.
- **compute(`K` key, `BiFunction` < ? super `K`, ? super `V`, ? extends `V`> remappingFunction)** - для указанного ключа `key` этот метод устанавливает в качестве value результат выполнения функции `remappingFunction`.
- **computeIfAbsent(`K` key, `Function` < ? super `K`, ? extends `V`> mappingFunction)** - метод добавит новый элемент в [Map](https://javarush.com/groups/posts/763-9-glavnihkh-voprosov-o-map-v-java), но только в том случае, если элемент с таким ключом там отсутствует. В качестве `value` ему будет присвоен результат выполнения функции `mappingFunction`.
- **computeIfPresent(`K` key, `BiFunction` < ? super `K`, ? super `V`, ? extends `V`> remappingFunction)** - тот же принцип, что и у `Map.compute()`, но все вычисления будут выполнены только в случае, если элемент с ключом `key` уже существует.
- **entrySet()** - возвращает [[Set]] ключей и значений.
- **values()** - возвращает [[Collection]] значений.
- **containsKey(`Object` key)** - возвращает `true`, если такой ключ существует.
- **replace(`K` key, `V` newValue)** — заменяет значение ключа `key` на `newValue`, если такой ключ существует. Если нет — ничего не происходит.


___
### Zero-Links
- 

___
### Links
- [Документация](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)
- [Статья JavaRush](https://javarush.com/quests/lectures/questsyntaxpro.level13.lecture03)
- [Примеры с JavaRush](https://javarush.com/groups/posts/524-khvatit-pisatjh-ciklih-top-10-luchshikh-metodov-dlja-rabotih-s-kollekcijami-iz-java8)
- [Статья с хабра](https://habr.com/ru/articles/128017/)
- [[Java Collection Framework]]