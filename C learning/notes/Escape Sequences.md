# Escape Sequences in C Language

Escape sequences in C are special character combinations used in string and character literals to represent non-printable or special characters.

## Common Escape Sequences

| Escape Sequence | Description |
|----------------|-------------|
| `\n` | Newline (moves cursor to a new line) |
| `\t` | Horizontal tab |
| `\r` | Carriage return |
| `\b` | Backspace |
| `\f` | Form feed |
| `\v` | Vertical tab |
| `\a` | Alert (produces a beep sound) |
| `\'` | Single quote (used in character literals) |
| `\"` | Double quote (used in string literals) |
| `\\` | Backslash |
| `\?` | Question mark (used to avoid trigraph ambiguity) |
| `\xhh` | Hexadecimal number representation |
| `\ooo` | Octal number representation |

## Example Usage in C

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n"); // Prints "Hello, World!" followed by a new line
    printf("Tab\tSeparated\n"); // Prints "Tab    Separated"
    printf("Beep sound\a\n"); // Produces a beep sound (if supported)
    printf("Backslash: \\\n"); // Prints "Backslash: \"
    return 0;
}
```

## Explanation
- `\n` moves the cursor to a new line.
- `\t` inserts a tab space.
- `\a` triggers a beep sound (if the system supports it).
- `\\` allows printing of the backslash character.

Escape sequences help format output, control spacing, and include special characters in string literals efficiently.

