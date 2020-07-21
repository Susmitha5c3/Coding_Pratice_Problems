## Stock Buy and Sell
### Problem Statement -
> We are given a prices of the stock. We can buy it onany day and sell it on any day such that we have a maximum profit.

### Input Format -
* 1 5 3 8 12
* 30 20 10
* 10 20 30 
### Output format -
* 13
* 0
* 20
> Considering the first sample test case, we fist buy the stock of price **1** and sell it on the day of price **5**, which is the second day. Therefore, the maximum profit upto there is **(5-1) = 4**. Next we will buy the stock on the day of price **3** and sell it on the day of price **12**. Therefore the profit becomes **4 + (12-3) = 13**.

### Psuedocode - 
1. Navie Solution O(N^2):
> Here we are considering two indexes **start** and **end**. And we can write a recursive function. If there is less than or equal to the one element in the range of start and end, then we dont buy any stock so we simply return 0.
> Now, we are considering a pair of ar[i] and ar[j] such that ar[i] < ar[j] and i < j. i.e we are buying at ar[i] and selling it at ar[j] and make some profit. 
> Once we found this pair, we can add the profit of this to the current pair and recursively call for the left of **i** and right of **j**.
```C++
// Initially start = 0, end = n
int maxProfit(int price[], int start, int end) {
    if(end <= start)
        return 0;
    int profit =  0;
    for(int i = start; i < end; i++){
        for(int j = i+1; j <= end; j++) {
            if(price[i] < price[j]) {
                int curr_profit = price[j] - price[i] + maxProfit(price, start, i-1) + maxProfit(price, j+1, end);
                profit = max(curr_profit, profit);
            }
        }
    }
    return profit;
}
```
2. Efficient Solution O(N) :
> As we know the prices of the stocks. If the prices are going down we let them go down. Once the price reaches the minimum or bottom, then we buy the stock. And if the prices are going up we let them go up and once these prices reaches maximum we sell the stock.

```C++
int maxProfit(int price[], int n) {
    int profit = 0;
    for(int i = 1; i < n; i++) {
        if(price[i] > price[i-1]){
            profit += price[i] - price[i-1];
        }
    }
    return profit;
}
```