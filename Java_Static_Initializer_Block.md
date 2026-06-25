# Java Static Initializer Block

## Problem

Static initialization blocks are executed when the class is loaded, and you can initialize static variables in those blocks.

You are given a class `Solution` with a `main` method. Complete the given code so that it outputs the area of a parallelogram with breadth `B` and height `H`.

If either `B <= 0` or `H <= 0`, the output should be:

```text
java.lang.Exception: Breadth and height must be positive
```

## Input Format

There are two lines of input:

1. The first line contains an integer `B`, the breadth of the parallelogram.
2. The second line contains an integer `H`, the height of the parallelogram.

## Output Format

- If both `B` and `H` are greater than `0`, print the area of the parallelogram.
- Otherwise, print:

```text
java.lang.Exception: Breadth and height must be positive
```

## Sample Input 1

```text
1
3
```

## Sample Output 1

```text
3
```

## Sample Input 2

```text
-1
2
```

## Sample Output 2

```text
java.lang.Exception: Breadth and height must be positive
```

---

# Solution

```java
import java.io.*;
import java.util.*;
import java.lang.Exception;

public class Solution {

    public static void main(String[] args) throws Exception{
        Scanner sc = new Scanner(System.in);
        int b = sc.nextInt();
        int h = sc.nextInt();
        
        try{
            if(b <= 0 || h <= 0)
                throw new Exception("Breadth and height must be positive");
             System.out.println(b*h);
            
        }catch(Exception e){
             System.out.println(e);
        }
    }
}
```

## Explanation

### Static Block

```java
static {
    ...
}
```

The static block executes when the class is loaded, before the `main()` method runs.

### Validation

```java
if (B <= 0 || H <= 0)
```

Checks whether breadth or height is non-positive.

### Area Calculation

```java
int area = B * H;
```

If both values are positive, the area of the parallelogram is printed.

### Example

Input:

```text
1
3
```

Output:

```text
3
```

Input:

```text
-1
2
```

Output:

```text
java.lang.Exception: Breadth and height must be positive
```