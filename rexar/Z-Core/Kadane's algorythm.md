2024-06-06 20:24
Tags: #z

___
#
~~Алгоритм используют с [[Sliding window]]~~ это его вариант для решения только задачи maxSubArray

Алгоритм основан на запоминании пиковых значений для массива и пикового значения для конечного сабмассива, и перерассчете этих значений при добавлени к нему новых элементов.


![[maximum-subarray-sum.png]]

```java
     public int kadane(int[] arr) {  

	 int n = arr.length;
         int max_so_far=arr[0];
         int max_ending_here=arr[0];  
         for(int i=1;i<n;i++)  
         {  
             max_ending_here =Math.max(arr[i], max_ending_here +arr[i]);  

             if(max_so_far<max_ending_here){  
             max_so_far=max_ending_here;  
             }  

         }  
     return max_so_far;  
     }
```
___
### Zero-Links


___
### Links
- [видео объяснение](https://www.youtube.com/watch?v=MCriLqc_8sY)