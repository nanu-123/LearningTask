# Format Conversion Specifiers

Format conversion specifiers are used in programming languages like C, Python, and others to format and display data in a specific way. These specifiers define how a value should be converted and represented as a string.

## Common Format Specifiers

### In C Language
In C, format specifiers are used with functions like `printf()` and `scanf()` to handle input and output formatting.

| Specifier | Description |
|-----------|-------------|
| `%d` | Integer (signed) |
| `%i` | Integer (signed) |
| `%u` | Unsigned integer |
| `%f` | Floating-point number |
| `%lf` | Double floating-point number |
| `%c` | Character |
| `%s` | String |
| `%x` | Hexadecimal integer (lowercase) |
| `%X` | Hexadecimal integer (uppercase) |
| `%o` | Octal integer |
| `%%` | Prints a `%` symbol |

Example:
```c
#include <stdio.h>
int main() {
    int num = 10;
    printf("The number is %d", num);
    return 0;
}
```


