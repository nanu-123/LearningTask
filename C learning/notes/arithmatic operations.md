# Integer Division, Remainder, and Increment/Decrement in C

## 1. Integer Division

The division of two integer numbers yields an integer result.

### Example:
```c
1 / 2 = 0
```

However, if one of the numbers is a floating-point number, the result will be a floating-point number:

```c
1.0 / 2 = 0.5
```

## 2. Remainder Operator (`%`)

The remainder operator `%` yields the remainder after integer division.

It can only be used with integer numbers.

### Example:
```c
5 % 3 = 2
```

## 3. Increment (`++`) and Decrement (`--`) Operators

The increment (`++`) and decrement (`--`) operators increase or decrease the value of a variable by 1.

The placement of the operator (before or after the variable) affects the result:

- **Post-increment (`i++`)**: Use the current value of `i` in the expression, then increment `i` by 1.
- **Pre-increment (`++i`)**: Increment `i` by 1, then use the updated value in the expression.

### Example 1: Post-increment
```c
i = 1;
j = 1;
j = i++;
```
#### Result:
```c
i = 2; // i is incremented after the assignment
j = 1; // j gets the original value of i (1)
```

### Example 2: Pre-increment
```c
i = 1;
j = 1;
j = ++i;
```
#### Result:
```c
i = 2; // i is incremented before the assignment
j = 2; // j gets the updated value of i (2)
```

## Explanation of Results

### Post-increment (`i++`):
- The current value of `i` is used in the expression (`j = i`).
- After the expression is evaluated, `i` is incremented by 1.

### Pre-increment (`++i`):
- `i` is incremented by 1 first.
- The updated value of `i` is then used in the expression (`j = i`).

## Summary

- Integer division truncates the fractional part.
- The remainder operator (`%`) works only with integers and returns the remainder of a division.
- Increment (`++`) and decrement (`--`) operators can be used in two ways:
  - **Post-increment/decrement**: Use the current value, then update the variable.
  - **Pre-increment/decrement**: Update the variable first, then use the new value.

