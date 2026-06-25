# Java Date and Time

## Problem

The `Calendar` class is an abstract class that provides methods for converting between a specific instant in time and a set of calendar fields such as:

- `YEAR`
- `MONTH`
- `DAY_OF_MONTH`
- `HOUR`

and many others.

You are given a date. Your task is to write the method `findDay`, which returns the day of the week for the given date.

## Function Description

Complete the `findDay` function.

### Parameters

| Parameter | Type |
|-----------|------|
| month | int |
| day | int |
| year | int |

### Returns

| Type | Description |
|--------|-------------|
| String | The day of the week in capital letters |

## Input Format

A single line containing three space-separated integers:

```text
MM DD YYYY
```

representing the month, day, and year respectively.

## Sample Input

```text
08 05 2015
```

## Sample Output

```text
WEDNESDAY
```

## Explanation

The day on **August 5, 2015** was:

```text
WEDNESDAY
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
import java.time.LocalDate;

class Result {

    public static String findDay(int month, int day, int year) {
        return LocalDate.of(year, month, day)
                        .getDayOfWeek()
                        .name();
    }

}

public class Solution {

    public static void main(String[] args) throws IOException {

        BufferedReader bufferedReader =
                new BufferedReader(new InputStreamReader(System.in));

        BufferedWriter bufferedWriter =
                new BufferedWriter(
                        new FileWriter(System.getenv("OUTPUT_PATH")));

        String[] firstMultipleInput =
                bufferedReader.readLine()
                              .replaceAll("\\s+$", "")
                              .split(" ");

        int month = Integer.parseInt(firstMultipleInput[0]);
        int day = Integer.parseInt(firstMultipleInput[1]);
        int year = Integer.parseInt(firstMultipleInput[2]);

        String res = Result.findDay(month, day, year);

        bufferedWriter.write(res);
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

## Explanation

### Create a Date

```java
LocalDate.of(year, month, day)
```

Creates a `LocalDate` object representing the given date.

Example:

```java
LocalDate.of(2015, 8, 5);
```

### Get Day of Week

```java
.getDayOfWeek()
```

Returns the day of the week as an enum value.

### Convert to Uppercase String

```java
.name()
```

Returns the enum name in uppercase.

Example:

```java
LocalDate.of(2015, 8, 5)
         .getDayOfWeek()
         .name();
```

Output:

```text
WEDNESDAY
```

## Example

### Input

```text
12 25 2024
```

### Output

```text
WEDNESDAY
```