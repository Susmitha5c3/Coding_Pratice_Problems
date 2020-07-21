## Maximum Difference
### Problem Statement -
> Given an array of size N. Find the maximum value if **arr[i]-ar[j]** such that j > i.

### Input Format -
* 2 3 10 6 4 8 1
* 7 9 5 6 3 2
* 10 20 30
* 30 10 8 2

### Output Format - 
* 8
* 2
* 20 
* -2

### Psuedocode -
> Subtracting larger number from smaller number will not work.
> We need to consider every element as **arr[j]** and also we need to keep track of the minimum element. So at every arr[j], we will subtract the minimum element from arr[j] to find the maximum difference.
``` C++
int maxDiff(int ar[], int n) {
    int res = ar[0] - ar[1], min = ar[0];
    for(int j = 1; j < n; j++) {
        res = max(res, min - ar[j]);
        min = min(ar[j], min);
    }
    return res;
}
``` 