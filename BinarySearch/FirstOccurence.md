## First Occurence of an element
### Problem Statement -
> Given a sorted array and a key, find the first occurence of that key in the array.

### Input Format -
* 5 10 10 20 20 20 20, 20
* 5 5 5 5, 5
* 15 20 25 45, 30


### Output Format -
* 3
* 0
* -1

### Psuedocode-
> Based on binary Search

```Java
int firstOcc(int ar[], int key, int low, int high) {
    while(low <= high) {
        int mid = (low+high)/2;
        if(ar[mid] < key)
            low = mid + 1;
        else if(ar[mid] > key)
            high = mid - 1;
        else {
            if(mid == 0 || ar[mid] != ar[mid-1])
                return mid;
            else
                //if there is same elements before that element, we need to seach for the left side.
                high = mid - 1;
        }
    }
    return -1;
}
```