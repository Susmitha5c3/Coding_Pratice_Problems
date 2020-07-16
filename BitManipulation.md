## 1. Count total set bits.
### Problem Statement -
> Given a number **N**. Count the total number of set bits from **0 to N** inclusive.
### Input format -
* 2
* 4
* 17
### Output Format -
* 5
* 35
### Psuedocode -
> In this, by observing the bits from the left side vertically down, we will find the patterns like
* 0, 1, 0, 1...... in 0th position.
* 0, 0, 1, 1, 0, 0,........ in 1st position.
* and so on.....
> This pattern can be find as following:
* By dividing (n+1) with 2, the quotient will be the number of time 0, 1 pattern has appear in 0th position.
* By dividing (n+1) with 4, the quotient will be the number of times 0,0,1,1 pattern has appeared in 1st position...........and so on.
> Therefore, the number of set bits will be **( (N+1) /(2^i) * 2^i-1)**, where i = 1.
> There are times, where the pattern will not have equal number of ones according to that pattern. Let's say the vertical order of the 3rd postion can be 0,0,1,1,0,0,1. Here the complete pattern has appeared one time. But there is incomplete pattern which has one bit set. In such situations, we need do mod with the power of 2.
```Java
int CountTotalBits(int n){
    count = 0, pow = 2, i = 0
    if n == 1 
        return 1;
    n = n+1
    while( pow <= n ) {
        // Calculating number of patterns
        t = n / pow; 

        // Calculating number of  set bits
        count += t * (Math.pow(2, i)); 

         //Calculation for incomplete pattern
        count += (t%2 == 1) ? (n %  pow) : 0;
    }
    return count;
}

```
### Time Complexity - 
> O (Log N)
### Other Approaches - 
> We can do this by using Dynamic programming also. There are lot more approaches for this in geeksforgeeks.

___
## 2. Binary to Gray Code conversion
### Problem Statement -
> Given a decimal number **N**. Return the gray of the binary representation of N in decimal.
### Input Format - 
* 3
* 7
* 10
* 0
### Output Format -
* 4
* 15
* 0
### Psuedocode -
> **GreyCode Conversion -*** Let's consider the binay number is **111**. The MSB bit of the gray code is same as the MSB bit in binary representation. Then the next bit of gray code is the xor of the next bit and the previous bit in the binary represntation.
* Binary : 111
* Gray : 100
```java

char xor(char x, char y) {
    if(x == y) return '0';
        else return '1';
}

int convert(int n) {
    //convert decimal to binary string.
    String binary = Integer.toBinaryString(n);
    String gray = "";
    gray += binary.charAt(0);
    for(int i = 0; i < binary.length()-1; i++) {
        gray += xor(binary.charAt(i), binary.charAt(i+1));
    }
    //convert binary string to decimal
    int ans = Integer.parseInt(gray, 2);
    return ans;
}
```
### Other Approaches -
> Binary nunmber can also be converted to gray code as - N xor (N >> 1)
> If N = 3 ie. (011). Then (N>>1) = 001. The xor of these two is 2. Therefore gray code of 3 is 2.
___
## 3. Power of 2
### Problem Statement-
> Given a number **N**. Check if it can be expressed as power of 2.
### Input Format -
* 2
* 1
* 98
### Output Format -
* YES
* NO

### Psuedocode - 
1. A simple method is to check if **ceil(log2(n))** is equal to **floor(log2(n))**. If equal then the number can be expressd as power of 2.
2. By observing the numbers of **2^n**, it can only have one set bit. So we can simply count the number of set bits in the given number and if count is one then it is true.
3. If we subtract the **n** with **n-1**, then we get a number which has only one bit unset. Which is we actually doing complement of **n**. So, if a number n is a power of 2 then **bitwise &** of n and n-1 will be zero.  
### Time Complexity - 
>For first approach - O(Log N)
___
## 4. Swap Even and Odd bits.
### Problem Statement -
> Given an integer **N**. Swap even bits of N to odd bits and vice-versa.
> For eg : 23-(**0**0**0**1**0**1**1**1) - highlighted positions are even. These can be converted as 0**0**1**0**1**0**1**1** - 43 in dec.
### Input Format - 
* 2
* 23
* 2
### Output Format -
* 43
* 1
### Psuedocode -
> Basically we right shift all even bits by 1 to get odd bits. And we left shift all odd bits by 1 to get even bits.
* For getting all even bits of n -
    * We need to do bitwise and for **n** and **0nAAAAAAAA** which will give all even bits of n.
    * We use **0nAAAAAAAA** because - A(hex) = 10(dec) = 1010. Where it has even bits set.
* For getting all odd bits of n -
    * We need to do bitwise and for **n** and **0n55555555** which is an 32 bit integer, gives all odd bits of n.
    * We use **0n55555555** because - 5(hex) = 5(dec) = 0101. Where all odd bits are set.
* After getting even and odd bits we need to do right shift by 1 for even and left shift by 1 for odd.
* Next we need to combine those two ie. **even | odd**