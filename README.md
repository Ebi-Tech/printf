<<<<<<< HEAD
# _printf
```_printf``` is a custom implementation of the C programming function ```printf```.

**Prototype:** ```int _printf(const char *, ...);```

## Some Examples
**Integer**
* Input: ```_printf("There are %i dozens in a gross\n", 12);```
* Output: ```There are 12 dozens in a gross```

**Character**
* Input: ```_printf("The first letter in the alphabet is %c\n", 'A');```
* Output: ```The first letter in the alphabet is A```

**String**
* Input: ```_printf("%s\n", 'This is a string.');```
* Output: ```This is a string.```

**Decimal:**
* Input: ```_printf("%d\n", 1000);```
* Output:  ```1000```

**Rot13**
* Input: ```_printf("Unknown:[%R]\n", "HELLO WORLD");```
* Output:  ```URYYB JBEYQ```

**FLAGS**
* Input: ```printf("Flag: [%+ d]", 1230);```
* Output:  ```Flag: [+1230] => 13```

**OCTAL**
* Input: ```printf("Unsigned octal:[%o]", 6);```
* Output:  ```Unsigned octal:[6] => 18```



## Project Requirements
* All files will be compiled on Ubuntu 14.04 LTS
* Programs and functions will be compiled with gcc 4.8.4 using flags -Wall -Werror -Wextra and -pedantic
* Code must follow the [Betty] style
* Global variables are not allowed
* Authorized functions and macros:
  * ```write``` (man 2 write)
  * ```malloc``` (man 3 malloc)
  * ```free``` (man 3 free)
  * ```va_start``` (man 3 va_start)
  * ```va_end``` (man 3 va_end)
  * ```va_copy``` (man 3 va_copy)
  * ```va_arg``` (man 3 va_arg)

## Mandatory Tasks
- [x] Write function that produces output with conversion specifiers ```c```, ```s```, and ```%```.
- [x] Handle conversion specifiers ```d```, ```i```.
- [x] Create a man page for your function.
## Advanced Tasks
- [x] Handle conversion specifier ```b```.
- [x] Handle conversion specifiers ```u```, ```o```, ```x```, ```X```.
- [x] Use a local buffer of 1024 chars in order to call write as little as possible.
- [x] Handle conversion specifier ```S```.
- [x] Handle conversion specifier ```p```.
- [x] Handle flag characters ```+```, space, and ```#``` for non-custom conversion specifiers.
- [ ] Handle length modifiers ```l``` and ```h``` for non-custom conversion specifiers.
- [ ] Handle the field width for non-custom conversion specifiers.
- [ ] Handle the precision for non-custom conversion specifiers.
- [ ] Handle the ```0``` flag character for non-custom conversion specifiers.
- [x] Handle the custom conversion specifier ```r``` that prints the reversed string.
- [x] Handle the custom conversion specifier ```R``` that prints the rot13'ed string.
- [ ] All above options should work well together.
## File Descriptions
**_printf.c**
* contains the  fucntion ```_printf```, which uses the prototype ```int _printf(const char *format, ...);```. The format string is composed of zero or more directives. See ```man 3 printf``` for more detail. **_printf** will return the number of characters printed (excluding the null byte used to end output to strings) and will write output to **stdout**, the standard output stream.

**_putchar.c**
* contains the function ```_putchar```, which writes a character to stdout.

**main.h**
*contains all function prototypes used for ```_printf```.

**man_3_printf**
* manual page for the custom ```_printf``` function.

**functions.c** **functions1.c** **functions2.c**
* contains all function of each specifier used for ```_printf```.
* all function have its own description inside the file.

**handle_print.c**
* contains arguments types used for ```_printf```.

**get_flags.c**
* contains all function for each flag use for ```_printf```.

**utils.c**
* contains some necessary functionalities for ```_printf```.

**ger_width.c**
* contains functions to get width for spcifics spcifiers.

**writee_handlers.c**
* contains write functions.

By Divine Ifechukwude and Ofili Obianuju
=======
Compilation

Your code will be compiled this way:
$ gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c
As a consequence, be careful not to push any c file containing a main function in the root directory of your project (you could have a test folder containing all your tests files including main functions)
Our main files will include your main header file (main.h): #include main.h
You might want to look at the gcc flag -Wno-format when testing with your _printf and the standard printf. Example of test file that you could use:
alex@ubuntu:~/c/printf$ cat main.c 
#include <limits.h>
#include <stdio.h>
#include "main.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */
int main(void)
{
    int len;
    int len2;
    unsigned int ui;
    void *addr;

    len = _printf("Let's try to printf a simple sentence.\n");
    len2 = printf("Let's try to printf a simple sentence.\n");
    ui = (unsigned int)INT_MAX + 1024;
    addr = (void *)0x7ffe637541f0;
    _printf("Length:[%d, %i]\n", len, len);
    printf("Length:[%d, %i]\n", len2, len2);
    _printf("Negative:[%d]\n", -762534);
    printf("Negative:[%d]\n", -762534);
    _printf("Unsigned:[%u]\n", ui);
    printf("Unsigned:[%u]\n", ui);
    _printf("Unsigned octal:[%o]\n", ui);
    printf("Unsigned octal:[%o]\n", ui);
    _printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
    printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
    _printf("Character:[%c]\n", 'H');
    printf("Character:[%c]\n", 'H');
    _printf("String:[%s]\n", "I am a string !");
    printf("String:[%s]\n", "I am a string !");
    _printf("Address:[%p]\n", addr);
    printf("Address:[%p]\n", addr);
    len = _printf("Percent:[%%]\n");
    len2 = printf("Percent:[%%]\n");
    _printf("Len:[%d]\n", len);
    printf("Len:[%d]\n", len2);
    _printf("Unknown:[%r]\n");
    printf("Unknown:[%r]\n");
    return (0);
}

We strongly encourage you to work all together on a set of tests
If the task does not specify what to do with an edge case, do the same as printf



Tasks

0. I'm not going anywhere. You can print that wherever you want to. I'm here and I'm a Spur for life

Write a function that produces output according to a format.

Prototype: int _printf(const char *format, ...);
Returns: the number of characters printed (excluding the null byte used to end output to strings)
write output to stdout, the standard output stream
format is a character string. The format string is composed of zero or more directives. See man 3 printf for more detail. You need to handle the following conversion specifiers:
c
s
%
You don’t have to reproduce the buffer handling of the C library printf function
You don’t have to handle the flag characters
You don’t have to handle field width
You don’t have to handle precision
You don’t have to handle the length modifiers

1. Education is when you read the fine print. Experience is what you get if you don't

Handle the following conversion specifiers:

d
i
You don’t have to handle the flag characters
You don’t have to handle field width
You don’t have to handle precision
You don’t have to handle the length modifiers

2. With a face like mine, I do better in print

Handle the following custom conversion specifiers:

b: the unsigned int argument is converted to binary

3. What one has not experienced, one will never understand in print

Handle the following conversion specifiers:

u
o
x
X
You don’t have to handle the flag characters
You don’t have to handle field width
You don’t have to handle precision
You don’t have to handle the length modifiers

4. Nothing in fine print is ever good news

Use a local buffer of 1024 chars in order to call write as little as possible.

Repo:

GitHub repository: printf
>>>>>>> 2f911693d553dfa826a0d565da636a280611d96d
