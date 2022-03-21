Attempted at: Coderbyte

### Question

You will be given a list of stock prices for a given day and your goal is to return the maximum profit that could have been made by buying a stock at the given price and then selling the stock later on. For example if the input is: [45, 24, 35, 31, 40, 38, 11] then your program should return 16 because if you bought the stock at $24 and sold it at $40, a profit of $16 was made and this is the largest profit that could be made. If no profit could have been made, return -1.

### My Solution

```ts
function ArrayChallenge(arr: number[]) {
    let maxProfit = 0;
    arr.forEach((item, idx) => {
        // pick only possible profits in days that are to come
        const possibleProfits = arr.filter((num, i) => num > item && i > idx);
        if (possibleProfits.length !== 0) {
            possibleProfits.forEach((price) => {
                let profit = price - item;
                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            });
        }
    });
    // code goes here
    if (maxProfit === 0) {
        maxProfit = -1;
    }
    let output = `${maxProfit}MY_CHALLENGE_KEY`;
    // I also had to return the output concatenated with my challenge key and replaced with _ at every 4th letter
    let replaceIdx = 1;
    for (let i = 0; i < output.length; i++) {
        if (replaceIdx == 4) {
            output = output.substr(0, i) + '_' + output.substr(i + 1, output.length);
            replaceIdx = 1;
        } else {
            replaceIdx++;
        }
    }
    return output;
}

// keep this function call here
// @ts-ignore
console.log(ArrayChallenge(readline()));
```

Result: Passed 10/10 Test cases. But my solution had O(n²) complexity and the optimal solution is O(n)
