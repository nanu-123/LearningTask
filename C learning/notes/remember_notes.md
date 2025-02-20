# Best Practices for Writing Clean and Maintainable C Code

Below are some best practices to follow when writing C code to ensure readability, maintainability, and efficiency.

---

## 1. **Meaningful Variable Names**
- Choose meaningful variable names to make the program more understandable.
- A meaningful name can save a few lines of comments.

---

## 2. **Variable Definitions**
- Place variable definitions immediately after the left brace `{` that starts the `main` function.
- This ensures all variables are defined before being used.

---

## 3. **Proper Indentation**
- Watch the indentation of different body statements!
- Correct indentation avoids confusion and makes the code easier to read.
- An `else` in a control structure belongs to the latest `if` that did not get an `else` yet.
- Correct indentation helps quickly understand which `else` belongs to which `if` statement.

### Example: Importance of Correct Indentation
```c
#include <stdio.h>
int main(void) {
    int number;
    printf("Enter integer number: ");
    scanf("%d%*c", &number);
    if (number > 70)
        if (number > 80)
            printf("passed with great honor!\n");
        else
            printf("ok.\n");
}
```

## 4. **Avoid break and continue in Loops**
    - Avoid using break and continue statements in loops as they can make the code harder to follow.

---

## 5. **Avoid pow for Simple Exponentiations**
    - The pow function uses computationally expensive methods.
    - For simple exponentiations like 𝑥² or 𝑥³, use x * x or x * x * x instead.

---

## 6. **Function Declarations and Definitions**
    - To avoid compile errors and keep the code well-structured:
    - Avoid external dependencies in functions to maximize reusability.
    - Use local variables only and avoid global variables.

---

## 8. **Symbolic Constants for Array Sizes**
    - Use symbolic constants (e.g., #define) for all array sizes in your program.
    - This makes the code easier to maintain and modify.

---

## 9. **Array Indexing**
    - Only use indices in the interval [0, number_of_elements - 1].
    - Going out of bounds can lead to undefined behavior.

---

## 10. **Initialize Pointers**
    - Always initialize pointers to avoid unexpected behavior.
    - Uninitialized pointers can lead to segmentation faults or undefined behavior.

---

## 11. **Struct Definitions**
    - A newly defined struct type can only be used after its definition.
    - Define structure variables in the top section of the source code or in a header file (if applicable).

---

## **Summary**
    - Following these best practices will help you write clean, efficient, and maintainable C code. Always prioritize readability and avoid unnecessary complexity.

---
