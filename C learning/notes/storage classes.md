# Storage Classes in C Language

Storage classes in C define the scope, visibility, and lifetime of variables or functions. There are four types of storage classes in C:

## 1. Automatic Storage Class (`auto`)
- The default storage class for local variables.
- Allocated on the stack and deallocated when the function exits.
- Cannot be accessed outside the function.

### Example:
```c
#include <stdio.h>
void func() {
    auto int x = 10; // 'x' is automatically allocated
    printf("Value of x: %d\n", x);
}
int main() {
    func();
    return 0;
}
```

## 2. Register Storage Class (`register`)
- Stores variables in CPU registers instead of RAM (if possible).
- Provides faster access but does not guarantee storage in registers.
- Cannot use `&` (address-of) operator.

### Example:
```c
#include <stdio.h>
int main() {
    register int x = 5; // Hint to store 'x' in a CPU register
    printf("Value of x: %d\n", x);
    return 0;
}
```

## 3. Static Storage Class (`static`)
- Retains variable value between function calls.
- Default value is zero if uninitialized.
- Can be used for local or global variables with different behavior.

### Example (Local Static Variable):
```c
#include <stdio.h>
void counter() {
    static int count = 0; // Retains value between function calls
    count++;
    printf("Count: %d\n", count);
}
int main() {
    counter();
    counter();
    return 0;
}
```

### Example (Global Static Variable):
```c
#include <stdio.h>
static int x = 10; // Scope limited to this file
int main() {
    printf("Value of x: %d\n", x);
    return 0;
}
```

## 4. External Storage Class (`extern`)
- Declares a global variable without defining it.
- Used when a variable is defined in another file.

### Example (Multiple File Usage):
#### File1.c
```c
#include <stdio.h>
int num = 10; // Definition of extern variable
```
#### File2.c
```c
#include <stdio.h>
extern int num; // Declaration of extern variable
int main() {
    printf("Value of num: %d\n", num);
    return 0;
}
```

## Summary Table

| Storage Class | Scope | Lifetime | Default Value |
|--------------|-------|----------|--------------|
| `auto` | Block | Function execution | Garbage |
| `register` | Block | Function execution | Garbage |
| `static` (local) | Block | Program lifetime | Zero |
| `static` (global) | File | Program lifetime | Zero |
| `extern` | Global | Program lifetime | Zero |

Understanding storage classes helps in optimizing memory usage, controlling variable visibility, and improving code efficiency.

