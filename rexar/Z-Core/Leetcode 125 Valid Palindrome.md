2024-04-09 18:23 
Tags: #z

___
## Решение
### 1) [[Two Pointers]]
Сложность: `O(n)`
Память: `O(1)`
#### Объяснение
В данном решении используется метод двух указателей, при котором сохраняются два указателя: один в начале строки, а другой - в ее конце. Эти два указателя движутся друг к другу, пока не встретятся в середине строки.

На каждой итерации цикла while проверяются символы, на которые указывают начальный и последний указатели. Если один из символов не является буквой или цифрой (например, пробел или знак препинания), указатель перемещается на один шаг вправо (для start) или на один шаг влево (для last), пока не будет найдена буква или цифра.

Если оба символа являются буквами или цифрами, они преобразуются в строчные и сравниваются. Если они не равны, функция возвращает false, так как строка не является палиндромом. Если они равны, оба указателя перемещаются на один шаг вправо и влево соответственно.

Цикл while продолжается до тех пор, пока начальный указатель не станет больше последнего, что свидетельствует о том, что все символы были проверены и строка является палиндромом. После этого функция возвращает true.
#### Код
```java
class Solution {
    public boolean isPalindrome(String s) {
        if (s.isEmpty()) {
        	return true;
        }
        int start = 0;
        int last = s.length() - 1;
        while(start <= last) {
        	char currFirst = s.charAt(start);
        	char currLast = s.charAt(last);
        	if (!Character.isLetterOrDigit(currFirst )) {
        		start++;
        	} else if(!Character.isLetterOrDigit(currLast)) {
        		last--;
        	} else {
        		if (Character.toLowerCase(currFirst)
        		 != Character.toLowerCase(currLast)) {
        			return false;
        		}
        		start++;
        		last--;
        	}
        }
        return true;
    }
}
```

### 2) Мое решение (тоже [[Two Pointers]])
Сложность: `O(n)`
Память: `O(n)`
#### Объяснение
Собираем новую строку с помощью [[StringBuilder]], в которой будут находится только alphanumeric символы. Далее строка переводится в нижний регистр. Далее проходимся симметрично к центру проверяя что символы равны.
#### Код
```java
class Solution {
  public boolean isPalindrome(String s) {
    StringBuilder sb = new StringBuilder();
    for (char c: s.toCharArray()) {
      if ((c >= 'a' && c <= 'z') ||
        (c >= 'A' && c <= 'Z') ||
        (c >= '0' && c <= '9')) sb.append(c);
    }
    String pal = sb.toString().toLowerCase();
    int n = pal.length();
    for (int i = 0; i < n / 2; i++) {
      if (pal.charAt(i) != pal.charAt(n - i - 1)) return false;
    }
    return true;
  }
}
```

___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/valid-palindrome/description/)
- [neetcode видео решения](https://www.youtube.com/watch?v=bNvIQI2wAjk)
- [[Two Pointers]]