## Maximum even odd subarray
### Problem statement - 
> Given an array, find the length of maximum subarray which has alternative even(odd) and odd(even) elements.

### Input Format-
* 10 12 14 7 8
* 7 10 13 14
* 10 12 8 4
### Output Format -
* 3
* 4
* 1

### Psuedocode -
1. Naive Solution O(N^2) :
```C++
int evenOdd(int arr, int n) {
    int length = 1; //As single element is also valid subarray
    for(int i = 0; i < n ; i++ ){
        int curr = 1; //As single element is also valid subarray. 
        for(int j = i + 1; j < n; j++) {
            if(ar[j] % 2 == 0 && ar[j-1] % 2 != 0) || (ar[j] %2 != 0 && ar[j-1] %2 == 0)
                curr++;
            else
                break;
        }
        length = max(curr, length);
    }
    return length;
}
```

2. Efficient Solution O(N) : Based on the Kadane's Algorithm

```C++
int evenOdd(int ar[], int n) {
    int res = 1, curr = 1;
    for(int i = 1; i < n; i++){
        if(ar[i] % 2 == 0 && ar[i-1] % 2 != 0) || (ar[i] %2 != 0 && ar[i-1] %2 == 0) {
            curr++;
            res = max(res, curr);
        }
        else
            curr = 1;
    }
    return res;
}
```