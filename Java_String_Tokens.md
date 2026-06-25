# Java String Tokens

## Problem Statement

Given a string `s` matching the regular expression:

```text
[A-Za-z !,?._'@]+
```

Split the string into tokens.

A **token** is defined as one or more consecutive English alphabetic letters (`A-Z` or `a-z`).

Print:

1. The total number of tokens.
2. Each token on a new line.

---

## Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String str1 = sc.nextLine();
        int n = str1.length();

        ArrayList<String> arr = new ArrayList<>();

        for (int j = 0; j < n; j++) {
            int i = j;

            while (i < n &&
                   str1.charAt(i) != ' ' &&
                   str1.charAt(i) != '!' &&
                   str1.charAt(i) != ',' &&
                   str1.charAt(i) != '?' &&
                   str1.charAt(i) != '.' &&
                   str1.charAt(i) != '_' &&
                   str1.charAt(i) != '\'' &&
                   str1.charAt(i) != '@') {
                i++;
            }

            String str = str1.substring(j, i);

            if (!str.isEmpty()) {
                arr.add(str);
            }

            j = i;
        }

        System.out.println(arr.size());

        for (String a : arr) {
            System.out.println(a);
        }

        sc.close();
    }
}
```

---

## Approach

### Step 1: Read the Input String

```java
String str1 = sc.nextLine();
```

Example:

```text
He is a very very good boy, isn't he?
```

---

### Step 2: Traverse the String

Use two pointers:

```java
int j = 0;
int i = j;
```

Move `i` forward until a delimiter is found.

Delimiters:

```text
' '
'!'
','
'?'
'.'
'_'
'\''
'@'
```

---

### Step 3: Extract the Token

```java
String str = str1.substring(j, i);
```

Example:

```text
"He"
"is"
"a"
"very"
```

---

### Step 4: Store Non-Empty Tokens

```java
if (!str.isEmpty()) {
    arr.add(str);
}
```

This avoids adding empty strings caused by consecutive delimiters.

---

### Step 5: Print Results

```java
System.out.println(arr.size());

for (String token : arr) {
    System.out.println(token);
}
```

---

## Sample Input

```text
He is a very very good boy, isn't he?
```

## Sample Output

```text
10
He
is
a
very
very
good
boy
isn
t
he
```

---

## Dry Run

Input:

```text
He is a very very good boy, isn't he?
```

Tokens extracted:

```text
He
is
a
very
very
good
boy
isn
t
he
```

Count:

```text
10
```

---

## Simpler Regex Solution

HackerRank's intended solution is:

```java
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        String s = scan.nextLine().trim();

        if (s.length() == 0) {
            System.out.println(0);
            return;
        }

        String[] tokens = s.split("[ !,?._'@]+");

        System.out.println(tokens.length);

        for (String token : tokens) {
            System.out.println(token);
        }

        scan.close();
    }
}
```

### Regex Explanation

```java
"[ !,?._'@]+"
```

- `[]` → character class
- Matches any delimiter:
  - space
  - `!`
  - `,`
  - `?`
  - `.`
  - `_`
  - `'`
  - `@`
- `+` → one or more occurrences

Example:

```text
"He is a good boy"
```

becomes:

```text
["He", "is", "a", "good", "boy"]
```

---

## Time Complexity

### Manual Parsing

```text
Time Complexity: O(n)
Space Complexity: O(n)
```

### Regex Split

```text
Time Complexity: O(n)
Space Complexity: O(n)
```

where `n` is the length of the input string.