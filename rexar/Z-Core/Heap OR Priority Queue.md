2024-06-10 11:32
Tags: #z

___
В джаве нет кучи, но вот как она выглядит:
![[Heap-as-array.png]]
Куча бывает максимальной и минимальной, главное - желаемый элемент всегда в начале, остальное зависит от реализации.
## PriorityQueue
Очередь, в которой первый элемент наименьший по компаратору.
Конструкторы:
![[PriorityQueueConstructors.png]]
- методы такие же как и у очередей
- offer круче чем put
- удаление возможно элементов только по значению(-ям) или фильтру

___
### Zero-Links
 - [[Java Big O#Queue]]

___
### Links
- [wiki_Heap](https://en.wikipedia.org/wiki/Heap_(data_structure))
- [Документация](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/PriorityQueue.html)