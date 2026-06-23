# Java Loops II

## Problem

We use the integers `a`, `b`, and `n` to create the following series:

```text
(a + 2^0 * b),
(a + 2^0 * b + 2^1 * b),
(a + 2^0 * b + 2^1 * b + 2^2 * b),
...
```

You are given `q` queries in the form of `a`, `b`, and `n`. For each query, print the series corresponding to the given values as a single line of `n` space-separated integers.

## Input Format

- The first line contains an integer `q`, denoting the number of queries.
- Each of the next `q` lines contains three space-separated integers describing the respective values of `a`, `b`, and `n`.

## Output Format

For each query, print the corresponding series on a new line. Each series must be printed in order as a single line of `n` space-separated integers.

## Sample Input

```text
2
0 2 10
5 3 5
```

## Sample Output

```text
2 6 14 30 62 126 254 510 1022 2046
8 14 26 50 98
```

## Explanation

### Query 1

Given:

```text
a = 0
b = 2
n = 10
```

The series becomes:

```text
2
2 + 4 = 6
6 + 8 = 14
14 + 16 = 30
...
```

The first 10 terms are:

```text
2 6 14 30 62 126 254 510 1022 2046
```

### Query 2

Given:

```text
a = 5
b = 3
n = 5
```

The series becomes:

```text
8 14 26 50 98
```

---

# Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void solve(Scanner sc) {
        int a = sc.nextInt();
        int b = sc.nextInt();
        int n = sc.nextInt();

        int res = a;

        for (int i = 0; i < n; i++) {
            res += b * (1 << i);
            System.out.print(res + " ");
        }

        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while (t-- != 0) {
            solve(sc);
        }

        sc.close();
    }
}
```

## Key Idea

The expression:

```java
1 << i
```

computes:

```text
2^i
```

So each term adds:

```text
b × 2^i
```

to the running sum.

Example for:

```text
a = 5, b = 3
```

| i | Added Value | Running Sum |
|---|-------------|-------------|
| 0 | 3 × 2⁰ = 3 | 8 |
| 1 | 3 × 2¹ = 6 | 14 |
| 2 | 3 × 2² = 12 | 26 |
| 3 | 3 × 2³ = 24 | 50 |
| 4 | 3 × 2⁴ = 48 | 98 |

Output:

```text
8 14 26 50 98
```