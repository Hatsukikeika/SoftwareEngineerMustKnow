### KMP pattern search

This is an efficient algorithm on pattern matching, which reduce the time complexity from Brute-force O(m*n) to KMP O(m + n):

The KMP algorithm can be divided into two differnt parts, **build LPS map** and **match**:

#### buildLPS

```java
public int[] buildLPS(T[] pattern){
    int lpsPtr = 0, ptr = 1, len = pattern.length;
    int[] lps = new int[len];

    while(ptr < len){
        if(pattern[ptr].compareTo(pattern[lpsPtr])){
            lps[ptr] = lpsPtr + 1;
            ptr++;
            lpsPtr++;
        } else if (lpsPtr == 0) {
            lps[ptr] = 0;
            ptr++;
        } else {
            lpsPtr = lps[lpsPtr - 1];
        }
    }

    return lps;
}
```

#### pattern match

```java
public int match(T[] raw, T[] pattern, int[] lps){
    if(raw.length < pattern.length) return -1;

    int i = 0, j = 0;
    while(i < raw.length){
        if(raw[i].compareTo(pattern[j]) == 0){
            i++;
            j++;
        } else if (j == 0) {
            i++;
        } else {
            j = lps[j - 1];
        }

        if(j = lps.length) return i - j;
    }

    return -1;
}
```