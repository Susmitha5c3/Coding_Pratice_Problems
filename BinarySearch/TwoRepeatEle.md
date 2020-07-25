## Two Reapeated Elements

### Problem Statement -
> Given an array of size **N+2** containing integers from **1....N** with two elements repeated. Find those two repaeated elements.

### Input Format - 
* 3
* 4
* 1 2 1 3 4 3
* 2
* 1 2 2 1
* 2
* 1 1 2 2
### Output Format -
* 1 3
* 2 1
* 1 2
### Psuedocode -
> Traverse the complete array, take the array elements as index and mark the element at this index postion .
Marking can be done, for example by multiplying the element at this index by -1.
Also, check if the element at this index is already negative, if it is output the index.

```c++
void twoRepeated(int ar[], int N){
    
    // Your code here
     for(int i = 0; i < N+2; i++) {
        if(ar[abs(ar[i]) -1] < 0) 
            cout<<abs(ar[i])<<" ";
        else
            ar[abs(ar[i])-1] *= -1;
    }
    
}
```