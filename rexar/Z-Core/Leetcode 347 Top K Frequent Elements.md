2024-04-05 16:36
Tags: #z

___
## Решение
### 1) [[HashMap]] & [[BucketSort]]
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
- Создается HashMap где сначала проходим первую строку и увеличиваем счетчик цифры. 
- Получаем [[Set]] ключей и по ключам получаем значение (частота данной цифры). Эта частота является индексом бакета/корзины и кладется ключ в значение (т.е. что за цифра чаще всего встречается).
- Так как частота является индексом наших бакетов - мы проходимся с конца в начало и добавляем самые встречаемые цифры в результат. Не забываем проверят, чтобы размер результата не превысил `k`.
#### Код
```java
Map<Integer, Integer> count = new HashMap<>();
        List<Integer> bucket[] = new ArrayList[nums.length + 1];                
        
        for (int num : nums)
            count.merge(num, 1, Integer::sum);
        
        for (int key : count.keySet()){
            int freq = count.get(key);
            if (bucket[freq] == null)
                bucket[freq] = new ArrayList<>();
            bucket[freq].add(key);
        }
        
        int index = 0;
        int[] res = new int[k];
        for (int i = nums.length; i >= 0; i--)
            if (bucket[i] != null)
                for (int val : bucket[i]){
                    res[index++] = val;
                    if(index == k)
                        return res;
                }
        return res;
```
### 2) Свое (Не лучшее)
Сложность: `O(n log n)`
#### Объяснение
Создается HashMap где сначала проходим первую строку и увеличиваем счетчик цифры. Далее сортируется словарь по значениям в убывающем порядке с помощью `java stream api`. После складируем значения в результирующий массив.
#### Код
```java
class Solution {
  public int[] topKFrequent(int[] nums, int k) {
    Map < Integer, Integer > map = new HashMap < > ();
    for (int n: nums) {
      if (!map.containsKey(n)) map.put(n, 1);
      else {
        map.compute(n, (a, b) -> ++b);
      }
    }
    LinkedHashMap < Integer, Integer > sortedMap = map.entrySet()
      .stream()
      .sorted(Map.Entry. < Integer, Integer > comparingByValue().reversed())
      .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue,
        (e1, e2) -> e1, LinkedHashMap::new));

    Iterator < Integer > iterator = sortedMap.keySet().iterator();
    int[] res = new int[k];
    for (int i = 0; i < k; i++) {
      res[i] = iterator.next();
    }
    return res;
  }
}
```
___
### Zero-Links
- [[00 Sorting]]

___
### Links
- [leetcode задача](https://leetcode.com/problems/top-k-frequent-elements/)
- [neetcode видео решения](https://www.youtube.com/watch?v=YPTqKIgVk-k)
- [[Arrays & Hashing]]