2024-05-14 00:17
Tags: #z

___
# Решение
### 1) [[Backtracking]]
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
Используя рекурсию, мы идем по рекурсивному дереву по двум веткам.
1) Ответвление, где добавляется цифра на которую указывает индекс `start` и он сдвигается вправо
2) Ответвление, где мы ничего не добавляем и сдвигаем индекс `start` вправо
![[Leetcode 78 img.png]]
#### Код
```java
// The idea is to have two conditions: 
// One in which we will take the element into consideration, 
// Second in which we won't take the element into consideration.
class Solution {

    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> list = new ArrayList<>();
        helper(ans, 0, nums, list);
        return ans;
    }

    public void helper(
        List<List<Integer>> ans,
        int start,
        int[] nums,
        List<Integer> list
    ) {
        if (start >= nums.length) {
            ans.add(new ArrayList<>(list));
        } else {
            // add the element and start the  recursive call
            list.add(nums[start]);
            helper(ans, start + 1, nums, list);
            // remove the element and do the backtracking call.
            list.remove(list.size() - 1);
            helper(ans, start + 1, nums, list);
        }
    }
}

```

### 2) [[Backtracking]]
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
В самом начале добавляется пустое множество в результат. Далее проходимся в цикле по каждому числу, и добавляем его в каждое уже полученное множество - получаем новые уникальные множества и добавляем их в результат.
#### Код
```java
class Solution {
  public List < List < Integer >> subsets(int[] nums) {
    List < List < Integer >> res = new ArrayList < > ();
    res.add(new ArrayList < > ());

    for (int i = 0; i < nums.length; i++) {
      int cur = nums[i];
      int right = res.size();
      for (int j = 0; j < right; j++) {
        List < Integer > cp = new ArrayList < > (res.get(j));
        cp.add(cur);
        res.add(cp);
      }
    }
    return res;
  }
}
```

### 3) По строчкам
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
![[Leetcode 230 image.png]]
Можно заметить, что количество итоговых множеств, равняется 2^количество входных цифр. Также можно заметить, что эти цифры появляются в множествах с определенным интервалом (первая цифра интервал 2^1, вторая 2^2, третья 2^3 и т.д.).
Поэтому логика такая:
- инициализируется массив размером 2^количество входных цифр
- проходимся по входному массиву и заполняем "правую часть" интервала текущей цифрой, и так до конца выходного массива
- при переходе на новую цифру увеличиваем интервал в 2 раза

#### Код
```java
class Solution {
  public List < List < Integer >> subsets(int[] nums) {
    int n = nums.length;
    List < Integer > [] res = (ArrayList < Integer > []) new ArrayList[1 << n];
    for (int i = 0; i < 1 << n; i++) {
      res[i] = new ArrayList < Integer > ();
    }

    int segment = 2;
    for (int num: nums) {
      for (int i = 0; i < res.length; i++) {
        if (i % segment >= segment / 2) {
          res[i].add(num);
        }
      }
      segment = segment << 1;
    }

    return Arrays.asList(res);
  }

}
```

### 4) По колонкам
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
То же самое что и во [[#3) По строчкам|3]], только меняются циклы местами и сбрасывается интервал при каждой смене колонки.
#### Код
```java
class Solution {
  public List < List < Integer >> subsets(int[] nums) {
    int n = nums.length;
    List < Integer > [] res = (ArrayList < Integer > []) new ArrayList[1 << n];
    for (int i = 0; i < 1 << n; i++) {
      res[i] = new ArrayList < Integer > ();
    }

    int segment = 2;
    for (int i = 0; i < res.length; i++) {
      for (int num: nums) {
        if (i % segment >= segment / 2) {
          res[i].add(num);
        }
        segment = segment << 1;
      }
      segment = 2;
    }

    return Arrays.asList(res);
  }

}
```

### 5) По строчкам со сдвигом 
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
Все также как и в решениях [[#3) По строчкам|3]] и [[#4) По колонкам|4]], только используя на один цикл больше можно определять в какие именно ячейки записывать цифру, а проверять условия проходясь по всем.
#### Код
```java
class Solution {
  public List < List < Integer >> subsets(int[] nums) {
    int n = nums.length;
    List < Integer > [] res = (ArrayList < Integer > []) new ArrayList[1 << n];
    for (int i = 0; i < 1 << n; i++) {
      res[i] = new ArrayList < Integer > ();
    }

    int segment = 1;
    for (int num: nums) {
      for (int i = segment; i < res.length; i += segment << 1) {
        for (int j = i; j < i + segment; j++) {
          res[j].add(num);
        }

      }

      segment = segment << 1;
    }

    return Arrays.asList(res);
  }

}
```

### 6) Битовая маска
Сложность: `O(n*2^n)`
Память: `O(n)` или `O(n*2^n)`
#### Объяснение
Подмножеством массива длины n является (2 в степени n). Запустим цикл i от 0 до (2 в степени n). Затем возьмем двоичную форму i и составим подмножество. Так как двоичная форма содержит только 0 или 1, то если 1, то добавляем элемент из массива в список подмножества, иначе - нет. В подмножестве массива каждый элемент имеет 2 варианта: либо он войдет в подмножество, либо не войдет. Таким образом, 1 означает, что элемент войдет в подмножество, 0 - элемент не войдет в подмножество.

Пример: nums = [1,2,3]
          Количество подмножеств = (2 в степени 3) = 8.
          Таким образом, выполните цикл от 0 до 7.

![[Leetcode 78 bitmask.png]]
#### Код
```java
class Solution {
  public List < List < Integer >> subsets(int[] nums) {
    List < List < Integer >> ml = new ArrayList < > ();
    int n = nums.length;

    int numOfSub = 1 << n;

    for (int i = 0; i < numOfSub; i++) {
      List < Integer > cl = new ArrayList < > ();
      int temp = i;

      for (int j = n - 1; j >= 0; j--) {
        int rem = temp & 1;
        temp = temp >> 1;

        if (rem == 1) {
          cl.add(0, nums[j]);
        }
      }

      ml.add(cl);
    }

    return ml;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/subsets/solutions/1766675/java-intuition-of-approach-backtracking/)
- [neetcode видео решения](https://youtu.be/REOH22Xwdkk)