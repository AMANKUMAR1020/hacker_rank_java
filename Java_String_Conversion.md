# Java String Conversion

## Problem

You are given an integer `n`; you have to convert it into a string.

Complete the partially completed code in the editor. If your code successfully converts `n` into a string `s`, the code will print:

```text
Good job
```

Otherwise, it will print:

```text
Wrong answer
```

## Input Format

A single integer `n`.

### Constraints

```text
-100 <= n <= 100
```

## Sample Input 0

```text
100
```

## Sample Output 0

```text
Good job
```

---

# Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        String str = Integer.toString(n);
        int m = Integer.parseInt(str);

        if (n == m)
            System.out.println("Good job");
        else
            System.out.println("Wrong answer");

        sc.close();
    }
}
```

## Explanation

### Convert Integer to String

```java
String str = Integer.toString(n);
```

This converts the integer `n` into its string representation.

Example:

```java
int n = 100;
String str = Integer.toString(n);
```

Result:

```text
"100"
```

### Convert String Back to Integer

```java
int m = Integer.parseInt(str);
```

This converts the string back into an integer.

### Verification

```java
if (n == m)
```

Checks whether the original integer and the converted-back integer are equal.

If they are equal:

```text
Good job
```

Otherwise:

```text
Wrong answer
```

## Alternative Solution

You can also use:

```java
String str = String.valueOf(n);
```

instead of:

```java
String str = Integer.toString(n);
```

Both produce the same result.