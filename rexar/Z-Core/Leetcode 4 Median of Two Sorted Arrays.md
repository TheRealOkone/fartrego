2024-07-14 18:39
Tags: #z

___
# Решение
### 1) [[Binary Search]]
Сложность: `O(log(m+n))`
Память: `O(1)`
#### Объяснение
В самом начале, если требуется меняем местами массивы повторным вызовов функция - требуется, чтобы первый был наименьшим.
Поиск медианы будет осуществляться с помощью алгоритма бинарного поиска.

Будем использовать 2 указателя `l` - левая граница в бинарном поиске и `r` -  правая граница в бинарном поиске, их среднее значение `(l+r)/2` является медианой меньшего массива, а медиана меньшего массива является последним элементом левой партиции меньшего массива.

Медиана будет найдена, если партиции будут сбалансированы:
- Если самый правый элемент левой партиции в меньшем массиве будет меньше, чем самый левый элемент правой партиции в большем массиве.
- Если самый правый элемент левой партиции в большем массиве будет меньше, чем самый левый элемент правой партиции в меньшем массиве.
(проще понять по картинке)
![[Leetcode 4 Median of Two Sorted Arrays partitions correct img.png]] 
Чтобы получить медиану, нужно узнать чет/нечет суммы размеров массивов.
- Если нечетная, то берется максимум от самых правых элементов левой партиции.
- Если четная, то берется среднее арифметическое от максимума самых правых элементов левой партиции и минимума самых левых элементов правой партиции.
(проще понять по картинке)
![[Leetcode 4 Median of Two Sorted Arrays even median finding img.png]]
Если партиции не сбалансированы, требуется сделать перебалансировку.
- Если у левой партиции правый крайний элемент оказывается больше, чем у правой партиции левый крайний, то `r` сдвигается на `индекс медианы - 1`
- Если же наоборот, то `l` сдвигается на `индекс медианы + 1`
#### Код
```java
class Solution {
    public double findMedianSortedArrays(int[] smArr, int[] bigArr) {
        
        int smArrLen = smArr.length, bigArrLen = bigArr.length;
        
        // Ensure smArr is the smaller array for simplicity
        if (smArrLen > bigArrLen)
            return findMedianSortedArrays(bigArr, smArr);
        
        int n = smArrLen + bigArrLen;
        int half = (smArrLen + bigArrLen + 1) / 2; // Calculate the half partition size
        int l = 0, r = smArrLen;
        
        while (l <= r) {
            int midSmArr = (l + r) / 2; // Calculate mid index for smArr
            int midBigArr = half - midSmArr; // Calculate mid index for bigArr
            
            int leftSmArr = Integer.MIN_VALUE, leftBigArr = Integer.MIN_VALUE, rightSmArr = Integer.MAX_VALUE, rightBigArr = Integer.MAX_VALUE;
            
            // Determine values of leftSmArr, leftBigArr, rightSmArr, and rightBigArr
            if (midSmArr < smArrLen)
                rightSmArr = smArr[midSmArr];
            if (midBigArr < bigArrLen)
                rightBigArr = bigArr[midBigArr];
            if (midSmArr - 1 >= 0)
                leftSmArr = smArr[midSmArr - 1];
            if (midBigArr - 1 >= 0)
                leftBigArr = bigArr[midBigArr - 1];
            
            if (leftSmArr <= rightBigArr && leftBigArr <= rightSmArr) {
                // The partition is correct, we found the median
                if (n % 2 == 1)
                    return Math.max(leftSmArr, leftBigArr);
                else
                    return ((double)(Math.max(leftSmArr, leftBigArr) + Math.min(rightSmArr, rightBigArr))) / 2.0;
            }
            else if (leftSmArr > rightBigArr) {
                // Move towards the half side of smArr
                r = midSmArr - 1;
            }
            else {
                // Move towards the right side of smArr
                l = midSmArr + 1;
            }
        }
        
        return 0; // If the code reaches here, the input arrays were not sorted.
    }
}
```
### 2) [[Two Pointers]]
Сложность: `O(n+m)`
Память: `O(1)`
#### Объяснение
- **Initialize two pointers**, i and j, both initially set to 0.
- **Move the pointer** that corresponds to the **smaller value forward at each step.**
- Continue moving the pointers **until you have processed half of the total number of elements.**
- Calculate and **return the median** based on the values pointed to by i and j.
#### Код
```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n = nums1.length;
        int m = nums2.length;
        int i = 0, j = 0, m1 = 0, m2 = 0;

        // Find median.
        for (int count = 0; count <= (n + m) / 2; count++) {
            m2 = m1;
            if (i != n && j != m) {
                if (nums1[i] > nums2[j]) {
                    m1 = nums2[j++];
                } else {
                    m1 = nums1[i++];
                }
            } else if (i < n) {
                m1 = nums1[i++];
            } else {
                m1 = nums2[j++];
            }
        }

        // Check if the sum of n and m is odd.
        if ((n + m) % 2 == 1) {
            return (double) m1;
        } else {
            double ans = (double) m1 + (double) m2;
            return ans / 2.0;
        }
    }
}
```
___
### Zero-Links
- 

___
### Links
- [leetcode задача](https://leetcode.com/problems/median-of-two-sorted-arrays/)
- [neetcode видео решения](https://www.youtube.com/watch?v=q6IEA26hvXc)