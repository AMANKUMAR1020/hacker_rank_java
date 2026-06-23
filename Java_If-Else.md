# Java If-Else

## Problem

In this challenge, we test your knowledge of using `if-else` conditional statements to automate decision-making processes.

### Task

Given an integer `N`, perform the following conditional actions:

- If `N` is odd, print `Weird`.
- If `N` is even and in the inclusive range of `2` to `5`, print `Not Weird`.
- If `N` is even and in the inclusive range of `6` to `20`, print `Weird`.
- If `N` is even and greater than `20`, print `Not Weird`.

Complete the stub code provided in your editor to print whether or not `N` is weird.

## Input Format

A single line containing a positive integer, `N`.

## Output Format

Print `Weird` if the number is weird; otherwise, print `Not Weird`.

## Sample Input 0

```text
3
```

## Sample Output 0

```text
Weird
```

## Sample Input 1

```text
24
```

## Sample Output 1

```text
Not Weird
```

## Explanation

### Sample Case 0

`3` is odd and odd numbers are weird, so we print:

```text
Weird
```

### Sample Case 1

`24` is even and greater than `20`, so it is not weird. Thus, we print:

```text
Not Weird
```

---

# Solution

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(
                new InputStreamReader(System.in));

        int N = Integer.parseInt(bufferedReader.readLine().trim());

        if (N % 2 == 1)
            System.out.println("Weird");
        else if (2 <= N && N <= 5)
            System.out.println("Not Weird");
        else if (6 <= N && N <= 20)
            System.out.println("Weird");
        else if (N > 20)
            System.out.println("Not Weird");

        bufferedReader.close();
    }
}
```