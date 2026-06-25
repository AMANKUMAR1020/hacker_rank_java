# Java End-of-file

## Problem

The challenge here is to read lines of input until you reach EOF (End Of File), then number and print all lines of content.

> **Hint:** Java's `Scanner.hasNext()` or `Scanner.hasNextLine()` method is helpful for this problem.

## Input Format

Read some unknown number of lines of input from `stdin (System.in)` until you reach EOF.

Each line of input contains a non-empty String.

## Output Format

For each line, print:

```text
line_number line_content
```

where:

- `line_number` starts from `1`.
- A single space separates the line number and the line content.

## Sample Input

```text
Hello world
I am a file
Read me until end-of-file.
```

## Sample Output

```text
1 Hello world
2 I am a file
3 Read me until end-of-file.
```

## Explanation

Since there are three lines of input, we print:

1. The first line prefixed with `1`.
2. The second line prefixed with `2`.
3. The third line prefixed with `3`.

---

# Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int cnt = 1;

        while (sc.hasNextLine()) {
            String str = sc.nextLine();
            System.out.println(cnt++ + " " + str);
        }

        sc.close();
    }
}
```

## Key Idea

### Reading Until EOF

```java
while (sc.hasNextLine())
```

- Continues reading input as long as another line exists.
- Stops automatically when EOF is reached.

### Numbering the Lines

```java
int cnt = 1;
```

For each line:

```java
System.out.println(cnt++ + " " + str);
```

prints:

```text
1 line1
2 line2
3 line3
...
```

## Example

### Input

```text
Java
is
awesome
```

### Output

```text
1 Java
2 is
3 awesome
```