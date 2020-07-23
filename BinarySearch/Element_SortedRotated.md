## Element in Sorted and Rotated Array

### Problem Statement -
> Given a sorted and rotated array with a key to search. Find the position of the key. An array which is completely sorted either increasing or decreasing order is a valid input array.

### Input Format -
* 4 8 10 14 2, 8
* 12 16 20 50 5 9, 5
* 100 200 300 70 80, 90

### Output Format - 
* 1
* 4
* -1

### Psuedocode -

Efficient Approach (Using BS) -
> Here, after finding the mid, we want to decide whether which half we want to ignore. And also we want to decide which half is sorted. There will be a case where both the halves are sorted. For these conditions, we need to check the mid element with any of the corner cases, whether with the ar[0] or with the ar[n-1].

> After finding the sorted part, weneed to check whether our element is in between this range. If not we move to the next part.

```Java
int search(int ar[], int low, int high, int x) {
    while(low <= high){
        int mid = (low+high)/2;
        if(ar[mid] == x)
            return mid;
        else if(ar[mid] > ar[low]) { // Left half
            if(x >= ar[low] && x < ar[mid])
                high = mid -1;
            else 
                low = mid +1;
        }
        else {
            //Right half
            if(x > ar[mid] && x<= ar[high])
                low = mid +1;
            else
                high = mid -1;
        }
    }
    return -1;
}
```