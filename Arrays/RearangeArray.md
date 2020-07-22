## Rearrange the Array
### Problem Statement -
> Given an sorted array, rearrange this array such that first maximum element is at first position, first minimum element is at second position, second maximum element is at thrid position and so on.
### Input Format -
* 6
* 1 2 3 4 5 6
* 11 
* 10 20 30 40 50 60 70 80 90 100 110
### Output Format -
* 6 1 5 2 4 3
* 110 10 100 20 90 30 80 40 70 50 60

### Psuedocode -
> Here, we need to place old value and new value at the same place and then access the new value.
```Java
public static void rearrange(int arr[], int n) 
    { 
        int max_idx = n - 1, min_idx = 0; 
  
        // store maximum element of array 
        int max_elem = arr[n - 1] + 1; 
  
        // traverse array elements 
        for (int i = 0; i < n; i++) { 
            // at even index : we have to put 
            // maximum element 
            if (i % 2 == 0) { 
                arr[i] += (arr[max_idx] % max_elem) * max_elem; 
                max_idx--; 
            } 
  
            // at odd index : we have to put minimum element 
            else { 
                arr[i] += (arr[min_idx] % max_elem) * max_elem; 
                min_idx++; 
            } 
        } 
  
        // array elements back to it's original form 
        for (int i = 0; i < n; i++) 
            arr[i] = arr[i] / max_elem; 
    } 
```