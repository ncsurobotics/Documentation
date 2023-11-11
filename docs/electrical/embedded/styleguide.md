AquaPack Robotics Embedded Programming Style Guide

*Note, this page is currently in the process of being written*

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Rules](#rules)
  - [General Rules](#general-rules)
    - [Line Width](#line-width)
    - [Braces](#braces)
    - [Parentheses](#parentheses)
    - [Common Abbreviations](#common-abbreviations)
    - [Casts](#casts)
    - [Keywords](#keywords)
  - [Comment Rules](#comment-rules)
    - [Comment Locations](#comment-locations)
  - [White Space Rules](#white-space-rules)
    - [Pointer (\* and \&) Operators](#pointer--and--operators)
    - [Alignment Rules](#alignment-rules)
    - [Tab Rules](#tab-rules)
  - [Module Rules](#module-rules)
    - [Naming Conventions](#naming-conventions)
    - [Header Files](#header-files)
    - [Source Files](#source-files)
  - [Data Type Rules](#data-type-rules)
    - [Type Definitions](#type-definitions)
    - [Use of Types](#use-of-types)
  - [Procedure Rules](#procedure-rules)
  - [Variable Rules](#variable-rules)
  - [Statement Rules](#statement-rules)

## Overview

This guide follows the general outline and some of the recommendations of [*Barr Group's Embedded C Coding Standard*](https://barrgroup.com/embedded-systems/books/embedded-c-coding-standard), set forth by Michael Barr.

Many of these rules are common sense and you probably are already following them in your own coding style. However, for consistency across the team it is practical to write them explicitly.

??? info Last updated: 2023-09-06 12:16 PM

---

## Rules

### General Rules

#### Line Width

1. No line width is enforced as we do not do paper code reviews. Please use your best discretion for when a line is considered too long (if you're not sure, try to keep the longest line to around 80 characters).
2. The preprocessor directive (`#define`) should not be used to alter or rename any keyword or other part of the C programming language.
3. The minimum target standard for both C and C++ is **C/C++ 11**. However, if newer versions such as 14 or 17 are available for the toolchain in use, they are preferred.

#### Braces

1. Left braces should appear on the same line as the statement they are connected with. Right braces should always be on a new line after their associated block of code.

    ``` c title="Example"
    if (condition) {
        code block;
    } else {
        code block line 2;
        code block line 1;
        code block line 3;
    }
    ```

#### Parentheses

1. To maintain clarity of long expressions, parentheses should be used to ensure proper execution order and provide better information to maintainers.
2. For further clarity, each side of a logical operator should be surrounded with parentheses, unless it is a single level operation.

```c title="Example"
(current_depth == target_depth) && (current_depth < pool_depth)

soft_arm && hard_arm
```

#### Common Abbreviations

1. Unless it is an abbreviation in common use and understood widely among programmers, refrain from using abbreviations as they can obfuscate the meaning of code.
2. Common variable names, such as `i` for a loop counter can be used under the condition that it is of limited scope and purpose, and that the context it is in is exceedingly clear.

#### Casts

1. Should a cast be required, the relevant lines should be commented to explain assumptions made.

#### Keywords

1. The use of `goto` should be exceedingly limited to only cases where it is justifiably required, and no other solution can be found (including rewriting other code to make the `goto` unecessary).
2. Uses of the `continue` keyword should be limited, but are allowed where it simplifies the code structure and makes it more legible.
3. Generally if something can be defined as `static`, it should be.
4. `const` should be applied in all locations where appropriate. In some cases, it may be more applicable than a preprocessor directive, while the preprocessor directive may be more applicable in others.
5. `volatile` should be used in all cases where a variable can be modified by anything outside of the normal control flow of the code (i.e. an ISR, variables shared between RTOS threads, etc).

### Comment Rules

1. Both single (//) and multi (/*) comment styles are considered acceptable, and should be used as applicable. When multi-line comments are used, all lines should begin with an asterisk (\*)
2. Multi-line comments should maintain a level of indentation with the leading asterisks vertical to each other, as shown below.
3. One leading space should be put between the comment text and the comment symbol.
4. If placed at the end of a line of code, all comments should be vertically aligned (within the context of a file).

```c title="Example"
the first line of code;  // comment text

/* comment text
 * comment text
 * comment text
 */

 line of code;          // comment text
 another line of code;  // comment text
```

1. Assume the reader is competent in the language, and avoid explaining the obvious. (*You aren't trying to hit a comment count for an assignment, you're trying to actually be helpful to yourself and others in the future*)
2. Single line comments should be used where the function of a single line may be ambiguous.

#### Comment Locations

1. Functions should be preceeded by a short comment block explaining the relevant values (inputs, outputs) and an extremely brief description of the purpose of the function. This comment block should follow Doxygen styling, [linked here](https://www.doxygen.nl/manual/docblocks.html).

```c title="Example"
/**
 * Sums two numbers
 * @param A an integer
 * @param B an integer
 * @return The summation
 */
int sum(int A, int B) {
    int c;
    c = a + b;
    return c;
}
```

### White Space Rules

1. The keywords `if, while, for, switch,` and `return` should be followed by a single space if there is more text on the same line.
2. Unless specified by another whitespace rule, all operators should be surrounded on either side by a single space.
3. Unary operators should not have a space between the operator and the operand.
4. Structure pointer and member operators should have no whitespace on either side.
5. Parentheses, braces, and brackets should not have an adjacent space on the interior side.
6. Excluding the end of a line, separating commas should should be followed by one space.
7. Semicolons should follow a preceeding statement without a space, but should always be followed by a space unless they end a line.
8. Use whitespace to separate blocks of code from each other in a logical fashion. It is suggested to use either 1 or 3 lines of separation, case dependent.

#### Pointer (* and &) Operators

1. Pointer operators should be written without a space on the operand side (i.e. `type *name`).
2. Pointer variables should be declared on a line separate from non-pointer variables of the same type, to avoid confusion between the two.

#### Alignment Rules

1. The # of a preprocessor directive should always be left aligned, regardless of the indentation of the line.
2. Align relevant blocks of code together (Don't be stupid).
    TODO: Make this nicer?

#### Tab Rules

1. The unicode tab character should not appear in files. Instead, the specified tab size is 4 spaces.

### Module Rules

#### Naming Conventions

1. File names should consist only of lower case letters, numbers, and underscores.
2. File names are recommended to be no longer than 16 characters. Ideally file names are specific and short, like the file itself.
3. All module names should not overlap with those of the standard library.
4. All files that contain a `main()` function should include "main" within the filename. In general, there will be only one file containing a main function. In this case, the file hsould be named `main.c` or `main.cpp`.

#### Header Files

1. Include preprocessor guards against multiple inclusion within all header files (#ifndef NAME_H)
2. `#pragma once` should not be used for protection against multiple files, see previous rule for alternative.
3. No variables should be defined within a header file, nor should any storage be allocated.
4. Header files should concern themselves strictly with the information that is needed to be known by other modules. (Everything else should be declared within the source file itself)
5. Unless required for a specific purpose, headers and source files should always be paired. Multiple source files per header file is discouraged.

#### Source Files

1. Source files should be specific, and contain only the information relevant to controlling one 'domain' (UART driver, Servo control, etc).
2. Source files should always `#include` the corresponding header file.
3. No absolute or relative paths should be used in `#include` statements. Instead, the build system should be used to include relevant links.
4. Do not include extraneous `#include` statements.
5. Do not directly `#include` another source file; always `#include` the relevant header file.
6. Any variables shared internally across the entire module but that aren't declared according to the rules of the header file should be declared at the top of the module's source file.

### Data Type Rules

#### Type Definitions

1. When defining new data types, they should always be appended with the `_t` designation.
2. Structs and enums should be implemented only through `typedef` declarations.
3. Any data types that are `public` should have their module name prepended to them in the pattern `module_type`.
4. Any data types that are `public` are to be declared in their module's respective *header* file.
5. Any data types that are `private` are to be declared in their module's respective *source* file.

#### Use of Types

1. Any time a specific number of bits needs to be used, one of the fixed-width integer types defined in `stdint.h` should be used, rather than one of the named types (short, long, long long).
2. `char` types should be used **only** when related to strings; See rule 1 in this subsection.
3. `bool` types should be used from the C standard library (`stdbool.h`), rather than defined using enums or preprocessor directives.
4. Bit fields--such as those used for register mapping--should be defined only within unsigned integer types.
5. Bitwise operations should only be done on unsigned integer types.
6. Signed and unsigned integers should preferably never be mixed within operations
7. Avoid floating point operations wherever practical. 
   (*There is some discretion required here. If it makes sense to do floating point (you have an FPU, it would violate common mathematical assumptions to do otherwise, etc.) proceed accordingly.*)

TODO: Add content pertaining to unions

### Procedure Rules

TODO: content

### Variable Rules

TODO: content

### Statement Rules

TODO: content
