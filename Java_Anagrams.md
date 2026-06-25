# Java Anagrams

## Problem Statement

Two strings are called **anagrams** if they contain the same characters with the same frequencies, regardless of their order.

The comparison is **case-insensitive**.

### Examples

```text
CAT  → ACT
Hello → hello
tac → CAT
```

All of the above are anagrams.

---

## Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String str1 = sc.nextLine().toLowerCase();
        String str2 = sc.nextLine().toLowerCase();

        char[] ch1 = str1.toCharArray();
        char[] ch2 = str2.toCharArray();

        Arrays.sort(ch1);
        Arrays.sort(ch2);

        str1 = new String(ch1);
        str2 = new String(ch2);

        if (str1.compareTo(str2) == 0) {
            System.out.println("Anagrams");
        } else {
            System.out.println("Not Anagrams");
        }

        sc.close();
    }
}
```

---

## Approach

### Step 1: Convert Both Strings to Lowercase

```java
str1 = str1.toLowerCase();
str2 = str2.toLowerCase();
```

This ensures the comparison is case-insensitive.

Example:

```text
Hello → hello
HELLO → hello
```

---

### Step 2: Convert Strings to Character Arrays

```java
char[] ch1 = str1.toCharArray();
char[] ch2 = str2.toCharArray();
```

Example:

```text
"anagram" → [a, n, a, g, r, a, m]
```

---

### Step 3: Sort Both Arrays

```java
Arrays.sort(ch1);
Arrays.sort(ch2);
```

Example:

```text
anagram → aaagmnr
margana → aaagmnr
```

If two strings are anagrams, their sorted forms will be identical.

---

### Step 4: Compare the Sorted Strings

```java
if (str1.compareTo(str2) == 0)
```

or equivalently:

```java
if (str1.equals(str2))
```

If both sorted strings are equal:

```text
Anagrams
```

Otherwise:

```text
Not Anagrams
```

---

## Example 1

### Input

```text
anagram
margana
```

### Sorted Strings

```text
aaagmnr
aaagmnr
```

### Output

```text
Anagrams
```

---

## Example 2

### Input

```text
anagramm
marganaa
```

### Sorted Strings

```text
aaagmmnr
aaaagmnr
```

### Output

```text
Not Anagrams
```

---

## Example 3

### Input

```text
Hello
hello
```

### After Lowercase Conversion

```text
hello
hello
```

### Output

```text
Anagrams
```

---

## Alternative Frequency Count Approach

Instead of sorting, count the frequency of each character.

```java
int[] freq = new int[26];

for (char c : str1.toLowerCase().toCharArray())
    freq[c - 'a']++;

for (char c : str2.toLowerCase().toCharArray())
    freq[c - 'a']--;

boolean anagram = true;

for (int x : freq) {
    if (x != 0) {
        anagram = false;
        break;
    }
}

System.out.println(anagram ? "Anagrams" : "Not Anagrams");
```

### Advantages

- No sorting required.
- Faster for large strings.

---

## Time Complexity

### Sorting Approach

```text
Time Complexity: O(n log n)
Space Complexity: O(n)
```

where `n` is the length of the string.

### Frequency Count Approach

```text
Time Complexity: O(n)
Space Complexity: O(1)
```

The frequency-count solution is the most efficient.