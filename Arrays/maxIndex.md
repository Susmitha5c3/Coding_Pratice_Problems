## Maximum element
### Problem Statement - 
> Given an array, find the maximum difference of index **j - i** such that **Ar[i] <= A[j]**.

### Input Format -
* 2
* 1 10
* 9
* 34 8 10 3 2 80 30 33 1
### Output Format -
* 1
* 6

### Psuedocode -
> Here, if we have a maximum value of **j-i**, then the elements before A[i] is larger than A[j]. Also the elements after A[j] is smaller than the A[i].

>Therefore, calculate the left array and right array of minimum nd maximum elements, then traverse the array, until we find left[i] < right[j]. Once we find this calculate the differnce of index and proceed furthur.

```Java
int maxDiff(int ar[], int n) {
    int l[n] = new int[n];
    int r[n] = new int[n];
    l[0] = ar[0];
    for(int i = 1; i< n; i++) {
        l[i] = min(l[i-1] , ar[i])
    }
    r[n-1] = ar[n-1];
    for(int i = n-2; i>= 0; i--) {
        r[i] = max(r[i+1], ar[i]);
    }
    int i = 0, j = 0, max = -1;
    while(i < n && j < n) {
        if(l[i] < r[i]) {
            max = Math.max(max, (j-i));
            j += 1;
        }
        else {
            i+=1;
        }
    }
    return max;
}
```

### Time complexity -
> O(N), Aux Space - O(N)

### For more approaches -
[maxIndex](https://www.geeksforgeeks.org/given-an-array-arr-find-the-maximum-j-i-such-that-arrj-arri/)