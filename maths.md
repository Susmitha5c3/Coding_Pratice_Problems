## 1. Digits of a factorial
### Problem Statement -
> Given a number N. Find the number of digits of its factorial.
### Input Format -
* 2
* 5
* 120
### Output Format -
* 3
* 199
### Psuedocode -
> When you need to calculate the digits of some number X. You do 10k=X. As 10 to power k tells us the k(digits).
The above point can easily be understood if you see that 10^4=10000 has (4+1) digits.

> Let's take 10!=10x to get the value of x.  
--> Take log both sides log(10)!=xlog10    
--> log(10\*9\*8*..*1)=x  
--> log10+log9+log8+...+log1=x  
--> Take the floor of sum and add 1 to get the number of digits.

___

## 2. Check a number is prime or not. Primilty test.
### Pesudocode - 
> We can loop lo 2 to n-1 and if any number between that range divides n the renturn false. Or else return true. It's time complexty is O(N)

> We can have following futher optimizations:

1. Instead of checking till N, we can simple check upto sqrt(N) because a larger facotr of n must be a multiple of smaller factor that has already been checked.
2. We can also improve it by the observation of the prime numbers. Every prime number is of the form **6k+-1** except 2 and 3.
    * This is so because it isrepresented as **6k+i** where i goes from 0 to 5.
    * Any number of form **6k+0**, **6k+2**, **6k+4** will be divisible by 4. And any number of form **6k+3** will be divisible by 3. Hence they can be primes.
    * Therefore, we are only left with **6k+1** and **6k+5**, which can effectively written as **6k+-1**.
    * But if a number **6k+-1**, is not everytime garauntee that it is a prime. Hence we need to check whether the number is divisible by **6k+-1**.

```Java
boolean isPrime(int n) {
    if(n<= 1)
        return false;
    if(n <= 3) return true;
    if(n % 2 == 0 || n % 3 == 0) return false;

    for(int i = 5; i*i <= n; i++) {
        if(n % i == 0 || n % (i+2) == 0)
            return false;
    }
    return true;
}
```
### Time Complexity -
> O( sqrt(N) )

___

## 3. Exactly 3 divisors
### Problem Statement -
> Given a positive integer **N**. Find how many numbers less than or equal to N has the exactly 3 divisors.
### Input Format -
* 3
* 6
* 10
* 30
### Output Format - 
* 1
* 2
* 3
### Psuedocode -
> Write the count upto some numbers like 1 to 25, then you can observe the pattern

> In this, the numbers which have 3 divisors, --- two divisors are --> 1 and itself. The third divisor is the prime number which it's square is less than or equal to N. i.e prime perfect number.

```
// here we are directly checking the square is less than n and then we are checking if it is prime.
for i = 2 to i * i <= N do 
    if(isPrime(N)) count++;
    // isPrime function is same as above.
return count.
```
### Time comlexity -
> O( sqrt(N) * sqrt(N) )

### Optimization -
> This can be further reduced to **O(sqrt(n) * sqrt(sqrt(n)))**, by using seive for calculating primes.

> Find all the perfect squares less than N (Ofcourse it is sqrt(N) ) and iterate over it to check if its prime or not using seive method in sqrt(i) time (where 'i' is the number you checking prime for and it will be less than equal to sqrt(1e9) ).
___
## 4. Sum of pairs of Hamming Distance
### Problem Statement -
> Given an array A of N non-negative integers, find the sum of hamming distances of all pairs of integers in the array.

> HAMMING DISTANCE - Hamming distance between two non-negative integers is defined as the number of positions at which the corresponding bits are different.

> For eg : a = 2, b = 5. Their binary representations are a = 0010, b = 0101. Here in these two, 3 bit positions are different. Hence the distance for this is 3.

### Input Format - 
* [1]
* [2, 3, 6]
### Output Format - 
* 0
* 8
> **Explaination for second testcase** f(2, 2) + f(2, 4) + f(2, 6) + f(4, 2) + f(4, 4) + f(4, 6) + f(6, 2) + f(6, 4) + f(6, 6) = 8

### PsuedoCode -
> check math section in InterviewBit