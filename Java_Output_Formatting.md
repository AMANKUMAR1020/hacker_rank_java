# Java Output Formatting

## Problem

Java's `System.out.printf()` function can be used to print formatted output. The purpose of this exercise is to test your understanding of formatting output using `printf`.

To get you started, a portion of the solution is provided for you in the editor; you must format and print the input to complete the solution.

## Input Format

Every line of input will contain a `String` followed by an integer.

- Each `String` will have a maximum of 10 alphabetic characters.
- Each integer will be in the inclusive range from 0 to 999.

## Output Format

In each line of output there should be two columns:

1. The first column contains the String and is left-justified using exactly 15 characters.
2. The second column contains the integer, expressed in exactly 3 digits; if the original input has fewer than 3 digits, pad the leading digits with zeroes.

## Sample Input

```text
java 100
cpp 65
python 50
```

## Sample Output

```text
================================
java           100
cpp            065
python         050
================================
```

## Explanation

- Each String is left-justified with trailing spaces through the first 15 characters.
- Each integer is displayed using exactly 3 digits.
- Integers with fewer than 3 digits are padded with leading zeroes.

Examples:

| Input Integer | Output |
|--------------|--------|
| 100 | 100 |
| 65  | 065 |
| 50  | 050 |
| 7   | 007 |

---

# Solution

```java
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("================================");

        for (int i = 0; i < 3; i++) {
            String s = sc.next();
            int x = sc.nextInt();

            System.out.printf("%-15s%03d%n", s, x);
        }

        System.out.println("================================");

        sc.close();
    }
}
```

## Format Specifiers Used

```java
%-15s
```

- `%s` → Print a String.
- `15` → Reserve 15 character positions.
- `-` → Left-justify the String.

```java
%03d
```

- `%d` → Print an integer.
- `3` → Use exactly 3 digits.
- `0` → Pad with leading zeroes if necessary.

Example:

```java
System.out.printf("%-15s%03d%n", "cpp", 65);
```

Output:

```text
cpp            065
```