## Leaders in Array
## Problem Statement - 
> Given an array and pint all the leaders in that array. An element ar[i] is said to be leader if all right elements of ar[i] is less than it.
### Input Format - 
* 7 10 4 3 6 5 2
* 10 20 30
* 30 20 10
### Output Format -
* 6 5 2
* 30
* 30 20 10
### Psuedocode -
> This is an efficient approach but the drawback is it's prints the elements in reverse order. We need to reverse the elements.
``` C++
void leaders(int arr[], int N) {
    int curr_ldr = ar[N-1];
    cout<<curr_ldr<<" ";
    for(int i = N-2; i >= 0; i++) {
        if(cur_ldr <= arr[i]){
            curr_ldr = arr[i];
            cout<<curr_ldr<<" ";
        }
    }
}
```
### Time Complexity -
> O(N)
