# Java String Reverse (Palindrome Check)

## Problem Statement

A palindrome is a word, phrase, number, or sequence of characters that reads the same forward and backward.

Given a string `A`, determine whether it is a palindrome.

- Print `Yes` if the string is a palindrome.
- Print `No` otherwise.

---

## Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String str1 = sc.nextLine();
        String str2;
        
        // int n = str1.length();
        // for(int i=n-1; 0<=i; i--){
        //     str2 += str1.charAt(i);            
        // }


        str2 = new StringBuilder(str1).reverse().toString();



        if (str1.compareTo(str2) == 0) {
            System.out.println("Yes");
        } else {
            System.out.println("No");
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

### Step 2: Reverse the String

```java
String str2 = new StringBuilder(str1).reverse().toString();
```

- `StringBuilder` is used to efficiently manipulate strings.
- `reverse()` reverses the sequence of characters.
- `toString()` converts it back to a `String`.

### Step 3: Compare Original and Reversed Strings

```java
if (str1.compareTo(str2) == 0)
```

If both strings are identical, the string is a palindrome.

---

## Example

### Input

```text
madam
```

### Reversed String

```text
madam
```

Since both strings are the same:

```text
Yes
```

---

## Sample Input

```text
madam
```

## Sample Output

```text
Yes
```

---

## Alternative Approach (Without StringBuilder)

```java
String reversed = "";

for (int i = str1.length() - 1; i >= 0; i--) {
    reversed += str1.charAt(i);
}

if (str1.equals(reversed))
    System.out.println("Yes");
else
    System.out.println("No");
```

---

## Optimized Two-Pointer Approach

```java
boolean palindrome = true;

int left = 0;
int right = str1.length() - 1;

while (left < right) {
    if (str1.charAt(left) != str1.charAt(right)) {
        palindrome = false;
        break;
    }

    left++;
    right--;
}

System.out.println(palindrome ? "Yes" : "No");
```

### Advantages

- No extra string creation.
- Constant extra space.

---

## Time Complexity

### Using StringBuilder

```text
Time Complexity: O(n)
Space Complexity: O(n)
```

### Using Two Pointers

```text
Time Complexity: O(n)
Space Complexity: O(1)
```

Where `n` is the length of the string.