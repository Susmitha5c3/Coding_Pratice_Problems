## Element in Infinite sized array

### Problem Statement-
> Given an infinite sorted array and a key, return the position of the kay given.

### Input Format - 
* {10, 15, 17, 19, 20, 40, 60, 100, 220,........}, 19
* {2, 7, 9, 11, 50, 78, 90, 200.........}, 25

### Output Format - 
* 3
* -1

### Psuedocode -
1. Naive Solution - O(pos)

```Java
int position(int ar[], int key) {
    int i =0;
    while(true) {
        if(ar[i] == key) return i;
        else if(ar[i]> key  ) return -1;
    }
}
```
2. Efficient Approach - O(log (pos))
> Here we start **i** with 1, and if we find the key at position **i**, then we return i. If **ar[i]** less than the key, then we double the index i ie. **i = i*2**. Else we, get the range of our key, which is **(i/2)+1 to i**. We can simply do binary search on that range.

```Java
int position(int ar[], int key) {
    if(ar[0] == key) return 0;
    int i = 1;
    while(ar[i] < key) {
        i = i * 2;
    }
    if(ar[i] == key) return i;
    binarySearch(ar, key, i/2+1, i-1);
}
```

Time Complexity -
> We will go upto **2*pos** th postion if our element is prsent at the **pos**. To reach this position (2\*pos), we are taking **log(2\*pos)** time. Now for binary search, we have range which is less than the positon. So it will take **log(<pos)**.

> Hence total time complexity is O(log pos).