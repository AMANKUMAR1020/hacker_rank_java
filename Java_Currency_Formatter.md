# Java Currency Formatter

## Problem

Given a double-precision number `payment`, denoting an amount of money, use the `NumberFormat` class's `getCurrencyInstance()` method to convert `payment` into the following currency formats:

- US
- India
- China
- France

Then print the formatted values as follows:

```text
US: formattedPayment
India: formattedPayment
China: formattedPayment
France: formattedPayment
```

where `formattedPayment` is the value formatted according to the appropriate locale's currency.

> **Note:** India does not have a built-in `Locale`, so you must construct one where the language is `"en"` (English) and the country is `"IN"` (India).

## Input Format

A single double-precision number denoting `payment`.

## Output Format

Print the formatted currency values:

```text
US: u
India: i
China: c
France: f
```

where:

- `u` is formatted in US currency.
- `i` is formatted in Indian currency.
- `c` is formatted in Chinese currency.
- `f` is formatted in French currency.

## Sample Input

```text
12324.134
```

## Sample Output

```text
US: $12,324.13
India: Rs.12,324.13
China: ￥12,324.13
France: 12 324,13 €
```

## Explanation

The value `12324.134` is formatted according to each locale's currency conventions:

- US uses `$` and commas for thousands.
- India uses `Rs.`.
- China uses `￥`.
- France uses spaces as thousand separators and commas as decimal separators.

---

# Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        double payment = scanner.nextDouble();
        scanner.close();

        NumberFormat us =
                NumberFormat.getCurrencyInstance(Locale.US);

        NumberFormat india =
                NumberFormat.getCurrencyInstance(
                        new Locale("en", "IN"));

        NumberFormat china =
                NumberFormat.getCurrencyInstance(Locale.CHINA);

        NumberFormat france =
                NumberFormat.getCurrencyInstance(Locale.FRANCE);

        System.out.println("US: " + us.format(payment));
        System.out.println("India: " + india.format(payment));
        System.out.println("China: " + china.format(payment));
        System.out.println("France: " + france.format(payment));
    }
}
```

## Explanation

### US Currency

```java
NumberFormat us =
    NumberFormat.getCurrencyInstance(Locale.US);
```

Example:

```text
$12,324.13
```

### Indian Currency

```java
NumberFormat india =
    NumberFormat.getCurrencyInstance(
        new Locale("en", "IN"));
```

Example:

```text
Rs.12,324.13
```

### Chinese Currency

```java
NumberFormat china =
    NumberFormat.getCurrencyInstance(Locale.CHINA);
```

Example:

```text
￥12,324.13
```

### French Currency

```java
NumberFormat france =
    NumberFormat.getCurrencyInstance(Locale.FRANCE);
```

Example:

```text
12 324,13 €
```

## Key Methods

### Create Currency Formatter

```java
NumberFormat.getCurrencyInstance(locale);
```

Returns a formatter for the specified locale.

### Format a Number

```java
formatter.format(payment);
```

Converts a numeric value into a locale-specific currency string.

Example:

```java
NumberFormat us =
    NumberFormat.getCurrencyInstance(Locale.US);

System.out.println(us.format(12324.134));
```

Output:

```text
$12,324.13
```