### Solution

```java
int flipBit(int n) {
    int numBits = Integer.BYTES * 8;
    if (n == -1) { // no 0s in bit representation of number
        return numBits;
    }

    int prevLength = 0;
    int currLength = 0;
    int maxLength = 1;

    // set "currLength" as # of trailing 1s
    int i = 0;
    while (getBit(n, i)) {
        currLength++;
        i++;
    }

    // Continue iterating through number
    for (  ; i < numBits; i++) {
        if (getBit(n, i)) {
            currLength++;
        } else {
            prevLength = currLength;
            currLength = 0;
        }
        maxLength = Math.max(maxLength, currLength + 1 + prevLength);
    }
    return maxLength;
}

private boolean getBit(int num, int bit) {
    return (num & (1 << bit)) != 0;
}
```

### Time/Space Complexity

- Time Complexity: O(1)
- Space Complexity: O(1)
