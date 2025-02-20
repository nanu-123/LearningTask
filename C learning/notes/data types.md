# Data Types in C

In C programming, data types define the type of data a variable can hold, such as integers, floating-point numbers, or characters. The size and range of these data types depend on the system architecture (e.g., 16-bit, 32-bit, or 64-bit). Below is a table of the most commonly used data types in C, their typical sizes, and their ranges.

---

## Primary Data Types in C

| **Data Type**       | **Size (Bytes)** | **Range**                                                                 |
|----------------------|------------------|---------------------------------------------------------------------------|
| `char`               | 1                | -128 to 127 (signed) or 0 to 255 (unsigned)                              |
| `unsigned char`      | 1                | 0 to 255                                                                 |
| `short`              | 2                | -32,768 to 32,767 (signed) or 0 to 65,535 (unsigned)                     |
| `unsigned short`     | 2                | 0 to 65,535                                                              |
| `int`                | 4 (typically)    | -2,147,483,648 to 2,147,483,647 (signed) or 0 to 4,294,967,295 (unsigned)|
| `unsigned int`       | 4 (typically)    | 0 to 4,294,967,295                                                       |
| `long`               | 4 or 8           | -2,147,483,648 to 2,147,483,647 (4 bytes) or -9.2e18 to 9.2e18 (8 bytes) |
| `unsigned long`      | 4 or 8           | 0 to 4,294,967,295 (4 bytes) or 0 to 1.8e19 (8 bytes)                    |
| `long long`          | 8                | -9.2e18 to 9.2e18 (signed) or 0 to 1.8e19 (unsigned)                     |
| `unsigned long long` | 8                | 0 to 1.8e19                                                              |
| `float`              | 4                | 1.2e-38 to 3.4e38 (6-7 decimal digits precision)                         |
| `double`             | 8                | 2.3e-308 to 1.7e308 (15-16 decimal digits precision)                     |
| `long double`        | 10, 12, or 16    | 3.4e-4932 to 1.1e4932 (19-20 decimal digits precision)                   |

---

## Fixed-Width Integer Types (from `<stdint.h>`)

Fixed-width integer types are used to guarantee the size of the data type, making code more portable. These types are defined in the `<stdint.h>` header.

| **Data Type**   | **Size (Bytes)** | **Range**                                      |
|-----------------|------------------|-----------------------------------------------|
| `int8_t`        | 1                | -128 to 127                                   |
| `uint8_t`       | 1                | 0 to 255                                      |
| `int16_t`       | 2                | -32,768 to 32,767                             |
| `uint16_t`      | 2                | 0 to 65,535                                   |
| `int32_t`       | 4                | -2,147,483,648 to 2,147,483,647               |
| `uint32_t`      | 4                | 0 to 4,294,967,295                            |
| `int64_t`       | 8                | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| `uint64_t`      | 8                | 0 to 18,446,744,073,709,551,615               |

---


## Explanation of Data Types

1. **`char`**:
   - Used to store single characters.
   - Size: 1 byte.
   - Can be signed or unsigned.

2. **`int`**:
   - Used to store integers.
   - Size: Typically 4 bytes (but can vary depending on the system).

3. **`float`**:
   - Used to store single-precision floating-point numbers.
   - Size: 4 bytes.

4. **`double`**:
   - Used to store double-precision floating-point numbers.
   - Size: 8 bytes.

5. **`long double`**:
   - Used for extended precision floating-point numbers.
   - Size: Typically 10, 12, or 16 bytes (system-dependent).

6. **`short`**:
   - Used to store small integers.
   - Size: 2 bytes.

7. **`long`**:
   - Used to store larger integers.
   - Size: 4 or 8 bytes (system-dependent).

8. **`long long`**:
   - Used to store very large integers.
   - Size: 8 bytes.

---

## Derived Data Types

- **Arrays**: A collection of elements of the same data type.
- **Pointers**: Stores memory addresses.
- **Structures**: A user-defined data type that groups variables of different data types.
- **Unions**: Similar to structures but share the same memory location for all members.

---

## Modifiers

- **`signed`**: Allows positive and negative values (default for `char`, `int`, etc.).
- **`unsigned`**: Allows only positive values (doubles the positive range).
- **`short`**: Reduces the size of the data type.
- **`long`**: Increases the size of the data type.

---

## Example Code

```c
#include <stdio.h>

int main() {
    char c = 'A';
    int i = 100;
    float f = 3.14;
    double d = 3.1415926535;
    long double ld = 3.141592653589793238;

    printf("char: %c, size: %lu byte\n", c, sizeof(c));
    printf("int: %d, size: %lu bytes\n", i, sizeof(i));
    printf("float: %f, size: %lu bytes\n", f, sizeof(f));
    printf("double: %lf, size: %lu bytes\n", d, sizeof(d));
    printf("long double: %Lf, size: %lu bytes\n", ld, sizeof(ld));

    return 0;
}
