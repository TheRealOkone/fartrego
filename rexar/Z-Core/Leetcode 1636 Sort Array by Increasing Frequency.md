2024-07-23 22:11
Tags: #z

___
# Решение
### 1) [[HashMap]] & [[BucketSort]]
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение
Считаем частоту в мапу, после с помощью [[BucketSort]] сортируем по частоте, а в каждой ячейке массива используем [[Heap OR Priority Queue]] для, того чтобы отсортировать в убывающем порядке.

#### Код
```java
class Solution {
    public int[] frequencySort(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        PriorityQueue<Integer> bucket[] = new PriorityQueue[nums.length + 1];

        for (int num : nums) map.merge(num, 1, Integer::sum);
        for (Map.Entry<Integer, Integer> e : map.entrySet()) {
            int idx = e.getValue();
            if (bucket[idx] == null) {
                bucket[idx] = new PriorityQueue<>(Comparator.reverseOrder());
            }
            bucket[idx].add(e.getKey());
        }

        int[] res = new int[nums.length];
        int idx = 0;
        for (int i = 0; i < nums.length + 1; i++) {
            if (bucket[i] != null) {
                while (bucket[i].peek() != null) {
                    int cur = bucket[i].poll();
                    for (int j = 0; j < i; j++) {
                        res[idx] = cur;
                        idx++;
                    }
                }
            }
        }

        return res;
    }
}
```

### 2) Custom Sort Comparator
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение
То же самое что 1, только по-умному сделанный свой компаратор.
#### Код
```java
class Solution {
    public int[] frequencySort(int[] nums) {
        int[] count = new int[201];
        for (int num : nums) {
            count[num + 100]++;
        }
        Integer[] numsArr = Arrays.stream(nums).boxed().toArray(Integer[]::new);
        Arrays.sort(numsArr, (a, b) -> {
            if (count[a + 100] == count[b + 100]) {
                return b - a;
            }
            return count[a + 100] - count[b + 100];
        });
        return Arrays.stream(numsArr).mapToInt(Integer::intValue).toArray();
    }
}
```

### 3) Stream API
Сложность: `O(n log n)`
Память: `O(n)`
#### Объяснение
То же самое что 1, только по-умному сделанный свой компаратор.
#### Код
```java
public int[] frequencySort(int[] nums) {
	Map<Integer, Integer> map = new HashMap<>();
	// count frequency of each number
	Arrays.stream(nums).forEach(n -> map.put(n, map.getOrDefault(n, 0) + 1));
	// custom sort
	return Arrays.stream(nums).boxed()
			.sorted((a,b) -> map.get(a) != map.get(b) ? map.get(a) - map.get(b) : b - a)
			.mapToInt(n -> n)
			.toArray();
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/sort-array-by-increasing-frequency/description/)
- [neetcode видео решения]()