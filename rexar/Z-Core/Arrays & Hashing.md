2024-04-10 01:58 
Tags: #

___
#
Стандартные массивы вида:
```java
int[] mas;
int mas[];
```
Значения примитивов в массиве инициализированы в 0.(проверить)
Инициализация:
```java
int[] mas = new int[size];
mas = new int[size];
int[] mas = new int[]{ 1,2,3,4,5,6,7,8,9,10 };
```
Двумерные массивы вида:
```java
int[][] mas;
int mas[][];
```
Инициализация:
```java
int[][] mas = new int[10][20];
int mas[][] = { { 1, 2, 3 }, { 4, 5 } }; 
```
Копирование
```java
int intArray[][] = { { 1, 2, 3 }, { 4, 5 } }; 
int cloneArray[][] = intArray.clone();
// will print false         
System.out.println(intArray == cloneArray);
```

Вывод
```java
Arrays.deepToString(mas);
```

___
### Zero-Links
- [[00 TODO]]

___
### Links
- [Документация](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html)