# Java Stdin and Stdout I

## Problem

Most HackerRank challenges require you to read input from stdin (standard input) and write output to stdout (standard output).

One popular way to read input from stdin is by using the `Scanner` class and specifying the input stream as `System.in`.

Example:

```java
Scanner scanner = new Scanner(System.in);
String myString = scanner.next();
int myInt = scanner.nextInt();
scanner.close();

System.out.println("myString is: " + myString);
System.out.println("myInt is: " + myInt);
```

The code above creates a `Scanner` object named `scanner` and uses it to read a `String` and an `int`. It then closes the `Scanner` object because there is no more input to read and prints the values to stdout.

If the input is:

```text
Hi 5
```

The output will be:

```text
myString is: Hi
myInt is: 5
```

Alternatively, you can use the `BufferedReader` class.

## Task

In this challenge, you must read **3 integers** from stdin and then print them to stdout. Each integer must be printed on a new line.

## Input Format

There are 3 lines of input, and each line contains a single integer.

## Sample Input

```text
42
100
125
```

## Sample Output

```text
42
100
125
```

---

# Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int myInt1 = sc.nextInt();
        int myInt2 = sc.nextInt();
        int myInt3 = sc.nextInt();

        sc.close();

        System.out.println(myInt1 + "\n" + myInt2 + "\n" + myInt3);
    }
}
```