# Java Substring

## Problem Statement

Given a string `S` and two indices `start` and `end`, print the substring consisting of all characters in the range from `start` to `end - 1`.

Java provides the `substring()` method to extract a portion of a string.

---

## Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        String S = in.next();
        int start = in.nextInt();
        int end = in.nextInt();

        System.out.println(S.substring(start, end));

        in.close();
    }
}
```

---

## Explanation

### Reading Input

```java
String S = in.next();
int start = in.nextInt();
int end = in.nextInt();
```

- `S` stores the input string.
- `start` is the starting index (inclusive).
- `end` is the ending index (exclusive).

### Extracting the Substring

```java
S.substring(start, end);
```

The `substring()` method returns a new string containing characters from:

- `start` (inclusive)
- `end` (exclusive)

### Example

```java
String s = "Helloworld";
System.out.println(s.substring(3, 7));
```

Output:

```text
lowo
```

Character positions:

| Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|-------|---|---|---|---|---|---|---|---|---|---|
| Char  | H | e | l | l | o | w | o | r | l | d |

`substring(3, 7)` extracts characters at indices `3, 4, 5, 6`.

Result:

```text
lowo
```

---

## Sample Input

```text
Helloworld
3 7
```

## Sample Output

```text
lowo
```

---

## Time Complexity

- **Time Complexity:** `O(k)`
- **Space Complexity:** `O(k)`

Where:

```text
k = end - start
```

because the substring contains `k` characters.