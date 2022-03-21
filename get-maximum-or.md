Attempted At: Hackerrank

### Question 

ToDo

```
// arr = [1, 2, 3], k = 2
// for 1: [1*2*2, 2, 3] = [4, 2, 3] = 4 | 2 | 3 = 7
// for 2: [1, 2*2*2, 3] = [1, 8, 3] = 1 | 8 | 3 = 11
// for 3: [1, 2, 3*2*2] = [1, 2, 12] = 1 | 2 | 12 = 15
// return 15
```

### My Solution
```ts
export const getMaxOr = (arr: number[], k: number) => {
    let maxSum = 0;
    for (let i = 0; i < arr.length; i++) {
        let result = 0;
        for (let j = 0; j < arr.length; j++) {
            if (j === i) {
                result = result | (arr[j] * 2 ** k);
            } else {
                result = result | arr[j];
            }
        }
        if (result > maxSum) {
            maxSum = result;
        }
    }
    return maxSum;
};
```

Result: Passed 6/14 Test cases. Failed cases with array length of more than 10000 items due to program not executed within time limits.
