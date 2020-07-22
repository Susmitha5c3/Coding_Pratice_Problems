## Check if array is sorted and rotated.
### problem Statement -
> An array can be increasingly sorted order and decreasingly sorted order.
### Input Format -
* 4
* 3 4 1 2
* 3
* 1 2 3
* 4
* 10 20 30 14
* 5
* 30 20 10 50 35
* 5
* 30 20 10 50 25
### Output Format -
* Yes
* No
* No
* Yes
* No

### psuedocode -
>  if array is Decreasingly or Increasingly Sorted in a Sorted and Rotated Array. Simple,If the positon of Max. Element is just before Min. Element, then it is Increasingly Sorted
Else if position of Max. Element is just after Min. Element then it is Decreasingly Sorted,
Else it is not sorted and rotated.

> In case of Increasingly Sorted,
Check if array is increasing upto Max. Element
Check if array is increasing again after Min Element
Check if Last Element is smaller than the first element

> In case of Decreasingly Sorted,
Check if array is decreasing upto Min. Element
Check if array is decreasing again after Max Element
Check if Last Element is larger than the first element

```C++
bool checkRotatedAndSorted(int ar[], int n){
    
    // Your code here
    int min = ar[0], idx1 = 0;
    for(int i = 1; i<n ;i++) {
        if(min > ar[i]){
            min = ar[i];
            idx1 = i;
        }
    }
    
    int max = ar[0], idx2 = 0;
    for(int i = 1; i<n ;i++) {
        if(max > ar[i]){
            max = ar[i];
            idx2 = i;
        }
    }
    
    bool f1 = true, f2 = true, f3 = true, f4 = true;
    for(int i = 0; i < idx2-1; i++) {
        if(ar[i]  > ar[i+1]) f1 = false;
    }
    
    for(int i = idx1 + 1; i < n-1; i++) {
        if(ar[i] > ar[i +1]) f2 = false;
    }
    for(int i = 0; i < idx1-1; i++) {
        if(ar[i]  < ar[i+1]) f3 = false;
    }
    for(int i = idx2+1; i < n-1; i++) {
        if(ar[i]  < ar[i+1]) f4 = false;
    }
    if(f1 && f2 && ar[n-1] < ar[0]) return true;
    else if(f3 && f4 && ar[n-1] >  ar[0]) return true;
    else return false;
 }
```