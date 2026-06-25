# Java Strings Introduction

## Problem Statement

Given two strings `A` and `B` consisting of lowercase English letters, perform the following operations:

1. Print the sum of the lengths of `A` and `B`.
2. Determine if `A` is lexicographically greater than `B`.
   - Print `Yes` if `A > B`
   - Otherwise print `No`
3. Capitalize the first letter of both strings and print them separated by a space.

---

## Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String str1 = scanner.nextLine();
        String str2 = scanner.nextLine();

        int as = str1.length();
        int bs = str2.length();

        scanner.close();

        // Sum of lengths
        System.out.println(as + bs);

        // Lexicographical comparison
        System.out.println(str1.compareTo(str2) > 0 ? "Yes" : "No");

        // Capitalize first character
        str1 = str1.substring(0, 1).toUpperCase() + str1.substring(1);
        str2 = str2.substring(0, 1).toUpperCase() + str2.substring(1);

        // Print formatted strings
        System.out.println(str1 + " " + str2);
    }
}
```

---

## Explanation

### 1. Sum of Lengths

```java
System.out.println(as + bs);
```

The `length()` method returns the number of characters in a string.

### 2. Lexicographical Comparison

```java
str1.compareTo(str2) > 0
```

The `compareTo()` method compares two strings alphabetically:

- Returns a positive value if `str1 > str2`
- Returns a negative value if `str1 < str2`
- Returns `0` if both strings are equal

### 3. Capitalizing the First Letter

```java
str1 = str1.substring(0, 1).toUpperCase() + str1.substring(1);
```

Steps:

- Extract the first character using `substring(0,1)`
- Convert it to uppercase using `toUpperCase()`
- Append the remaining part of the string using `substring(1)`

The same logic is applied to `str2`.

---

## Sample Input

```text
hello
java
```

## Sample Output

```text
9
No
Hello Java
```

---

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Length Calculation | O(1) |
| String Comparison | O(min(n, m)) |
| Capitalization | O(n + m) |

**Overall Complexity:** `O(n + m)`