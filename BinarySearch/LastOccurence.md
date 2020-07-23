## Last occurence of an element
### problem Statement -
> Given a sorted array and a key, find th elast occurence of that key.

### Input Format -
* 5 10 10 20 20 40 40 40, 40
* 5 15 15 20 20, 20
* 10 10 10 10, 10
* 2 4 4 6, 2

### Output Format -
* 7
* 4
* 3
* 0

### Psuedocode -
```java
int lastOcc(int ar[], int key, int low, int high) {
    while(low <= high) {
        int mid = (low+high)/2;
        if(ar[mid] < key)
            low = mid + 1;
        else if(ar[mid] > key)
            high = mid - 1;
        else {
            if(mid == n-1 || ar[mid] != ar[mid+1])
                return mid;
            else
                //if there is same elements before that element, we need to seach for the right side.
                low = mid + 1;
        }
    }
    return -1;
}
```
___

## Count Occurences of a number.

### input Format - 
* 10 10 20 20 20 20 30
* 10 10 10 10

### Output Fomat - 
* 3
* 4

### Psuedocode-
> Here, directly binary search is not used. Instead we are using two bianry searches.

```Java
int countOcc(int ar[], int k, int n){
    int first = firstOcc(ar, n, key);
    if(first == -1)
        return 0;
    else{
        return (lastOcc(ar, n, key)-first+1);
    }
}
```