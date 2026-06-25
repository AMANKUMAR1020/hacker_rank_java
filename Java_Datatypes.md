# Java Datatypes

## Problem

Java has 8 primitive data types:

- `char`
- `boolean`
- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`

For this exercise, we'll work with the integer types:

| Data Type | Size |
|------------|------|
| `byte` | 8-bit signed integer |
| `short` | 16-bit signed integer |
| `int` | 32-bit signed integer |
| `long` | 64-bit signed integer |

Given an input integer, determine which primitive data types are capable of properly storing that input.

Reference: <https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html>

## Input Format

- The first line contains an integer `t`, denoting the number of test cases.
- Each of the next `t` lines contains an integer `n`, which can be arbitrarily large or small.

## Output Format

For each input variable `n` and appropriate primitive data type, print:

```text
n can be fitted in:
* dataType
```

If there is more than one appropriate data type, print each one on its own line and order them by size:

```text
byte → short → int → long
```

If the number cannot be stored in any of the four primitive data types, print:

```text
n can't be fitted anywhere.
```

## Sample Input

```text
5
-150
150000
1500000000
213333333333333333333333333333333333
-100000000000000
```

## Sample Output

```text
-150 can be fitted in:
* short
* int
* long
150000 can be fitted in:
* int
* long
1500000000 can be fitted in:
* int
* long
213333333333333333333333333333333333 can't be fitted anywhere.
-100000000000000 can be fitted in:
* long
```

## Explanation

### Example 1

```text
-150
```

can be stored in:

```text
short
int
long
```

### Example 2

```text
213333333333333333333333333333333333
```

is larger than the range of `long`, so it cannot be stored in any of the supported primitive integer data types.

---

# Solution

```java
import java.io.*;
import java.util.*;
import java.lang.*;

public class Solution {

    public static void solve(Scanner sc) {

        String str = sc.next();

        try {
            long x = Long.parseLong(str);

            System.out.println(str + " can be fitted in:");

            if (x >= Byte.MIN_VALUE && x <= Byte.MAX_VALUE)
                System.out.println("* byte");

            if (x >= Short.MIN_VALUE && x <= Short.MAX_VALUE)
                System.out.println("* short");

            if (x >= Integer.MIN_VALUE && x <= Integer.MAX_VALUE)
                System.out.println("* int");

            System.out.println("* long");

        } catch (Exception e) {
            System.out.println(str + " can't be fitted anywhere.");
        }
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

## Data Type Ranges

| Type | Minimum Value | Maximum Value |
|--------|-------------|-------------|
| `byte` | -128 | 127 |
| `short` | -32,768 | 32,767 |
| `int` | -2,147,483,648 | 2,147,483,647 |
| `long` | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |

## Key Idea

The solution:

1. Reads the number as a `String`.
2. Attempts to convert it into a `long` using:

```java
long x = Long.parseLong(str);
```

3. If parsing succeeds, checks whether the value fits into:
   - `byte`
   - `short`
   - `int`
   - `long`

4. If parsing fails, the number is outside the range of `long`, so:

```text
n can't be fitted anywhere.
```

is printed.