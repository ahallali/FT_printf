# ft_printf

A 42 project: a reimplementation of the C standard library function `printf`, packaged as a static library.

## Supported conversions

| Conversion | Output |
|---|---|
| `%c` | a single character |
| `%s` | a string |
| `%p` | a pointer address in hexadecimal |
| `%d` / `%i` | a signed decimal integer |
| `%u` | an unsigned decimal integer |
| `%x` / `%X` | an unsigned hexadecimal integer (lowercase / uppercase) |
| `%%` | a percent sign |

Like the original, `ft_printf` returns the number of characters printed.

## Build

```bash
make
```

This creates `libftprintf.a`.

## Usage

```c
#include "ft_printf.h"

int main(void)
{
    int count = ft_printf("%s is %d years old (0x%x)\n", "Ahmed", 30, 30);
    ft_printf("%d characters printed\n", count);
    return (0);
}
```

```bash
cc main.c libftprintf.a -o demo && ./demo
```

## How it works

`ft_printf` walks through the format string with `va_list` (`<stdarg.h>`). Plain characters are written as they are; when a `%` is found, the next character selects the helper that prints the matching argument and adds its length to the total.
