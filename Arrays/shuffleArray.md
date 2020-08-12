## Shuffle Array

> Given an array[a1,a2,a3,a4........,b1,b2,b3,....] of size **n** with **2n** integers in it. shuffle the array such that, the array elements become [a1,b1,a2,b2,a3,b3,.......]

### Input
* [2,5,1,3,4,7], n = 3
### Output 
* [2,3,5,4,1,7]

### Psuedocode:
> 1. We can do a divide and conquer approach, by diving the array elements and then swaping those array elements. 

>Time complexirty : O(Nlog N)

> 2. Here, we are neglecting the first and last element of the array as they dont move. For every element at index **i**, we need to move it to the **2\*i** th index. And that element is moved to the **2*i** th index.

```Java
static void shufleArray(int []a, int n) 
{ 
    int temp; 
    n = n / 2; 
  
    for (int start = n + 1, j = n + 1, done = 0, i; 
         done < 2 * n - 2; done++) 
    { 
        if (start == j) 
        { 
            start--; 
            j--; 
        } 
  
        i = j > n ? j - n : j; 
        j = j > n ? 2 * i : 2 * i - 1; 
        temp= a[start]; 
        a[start]= a[j]; 
        a[j]= temp; 
  
    } 
} 
```

# This approach may fails...