# Java Substring Comparisons

## Problem Statement

Given a string `s` and an integer `k`, find the lexicographically smallest and largest substrings of length `k`.

### Lexicographical Order

Lexicographical (dictionary) order compares strings character by character:

- `ball < cat`
- `dog < dorm`
- `Happy < happy`
- `Zoo < ball`

### Example

For:

```text
s = "welcometojava"
k = 3
```

Possible substrings of length `3` are:

```text
wel
elc
lco
com
ome
met
eto
toj
oja
jav
ava
```

After sorting lexicographically:

```text
ava
com
elc
eto
jav
lco
met
oja
ome
toj
wel
```

- Smallest substring = `ava`
- Largest substring = `wel`

---

## Solution

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String str = sc.nextLine();
        int k = sc.nextInt();

        int n = str.length();
        ArrayList<String> arr = new ArrayList<>();

        for (int i = 0; i <= n - k; i++) {
            String s = str.substring(i, i + k);
            arr.add(s);
        }

        Collections.sort(arr);

        System.out.println(arr.get(0));
        System.out.println(arr.get(arr.size() - 1));

        sc.close();
    }
}
```

---

## Approach

### Step 1: Generate All Substrings of Length `k`

```java
for (int i = 0; i <= n - k; i++) {
    arr.add(str.substring(i, i + k));
}
```

For `"welcometojava"` and `k = 3`:

```text
wel, elc, lco, com, ome, met,
eto, toj, oja, jav, ava
```

### Step 2: Sort the Substrings

```java
Collections.sort(arr);
```

Sorting places the substrings in lexicographical order.

### Step 3: Print Smallest and Largest

```java
System.out.println(arr.get(0));
System.out.println(arr.get(arr.size() - 1));
```

- First element → smallest substring
- Last element → largest substring

---

## Sample Input

```text
welcometojava
3
```

## Sample Output

```text
ava
wel
```

---

## Time Complexity

Let:

- `n` = length of the string
- `k` = substring length

Generating all substrings:

```text
O(n)
```

Sorting:

```text
O((n - k + 1) log(n - k + 1))
```

Overall:

```text
O((n - k + 1) log(n - k + 1))
```

---

## Optimized Approach (Without Sorting)

Instead of storing and sorting all substrings, maintain the smallest and largest substring while iterating:

```java
String smallest = str.substring(0, k);
String largest = str.substring(0, k);

for (int i = 1; i <= str.length() - k; i++) {
    String curr = str.substring(i, i + k);

    if (curr.compareTo(smallest) < 0)
        smallest = curr;

    if (curr.compareTo(largest) > 0)
        largest = curr;
}

System.out.println(smallest);
System.out.println(largest);
```

### Time Complexity

```text
O(n)
```

This is the preferred solution for interviews and competitive programming.