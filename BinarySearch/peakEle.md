## Peak Element
### Problem Statement -
> Given an unsorted array. Find the peak element in it. An element is a peak element, if it is greater than its immediate left and imediate right element. If the element is at left end(0th index) and it's right is smaller, then that is also a peak element. Similary to the right.

### Input Format -
* 5 2 9 19 10 4
* 90 40 20 10 11
* 10 30 70

### Output Format -
* 19
* 90 or 11
* 70

### psuedocode
Efficient Solution - (using BS)
> Here we need to decide to which part we want to move. If the mid element is smaller than its left element, then we check in left part. If the mid element smaller than the right element then we check in right part. Otherwise, if both sides is smaller than the mid, then return mid.

```Java
int getPeak(int ar[], int n) {
    int low = 0, high = n-1;
    while(low<= high) {
        int mid = (low+high) /2;
        if (mid == 0 || ar[mid-1] <= ar[mid]) && (mid == n-1 || ar[mid+1] <= ar[mid])
            return mid;
        if(mid > 0 && ar[mid-1] >= ar[mid])
            high = mid - 1;
        else
            low = mid + 1;
    }
    return -1;
}
```