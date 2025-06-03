# CPython with Amharic Language Support

## Introduction

This modified version of CPython allows developers to write Python code using Amharic keywords and selected Amharic function names directly. This feature aims to make Python programming more accessible and intuitive for Amharic-speaking developers.

The modifications involve changes to the CPython interpreter's lexer (keyword definitions in `pegen/c_generator.py`), parser (grammar rules in `Grammar/python.gram`), and built-in function definitions (`Python/bltinmodule.c`).

## Features

### Amharic Keywords

Standard Python keywords can be replaced with their Amharic equivalents. Below is a list of supported Amharic keywords and their corresponding English Python keywords:

| Amharic Keyword | English Keyword |
|-----------------|-----------------|
| ሐሰት            | False           |
| ምንም            | None            |
| እውነት            | True            |
| እና             | and             |
| እንደ            | as              |
| አረጋግጥ          | assert          |
| አሲንክ           | async           |
| ተጠባበቅ          | await           |
| አቋርጥ           | break           |
| ክፍል            | class           |
| ቀጥል            | continue        |
| ተግባር           | def             |
| ሰርዝ            | del             |
| ካልሆነ-ከሆነ      | elif            |
| አለበለዚያ        | else            |
| በስተቀር          | except          |
| በመጨረሻ          | finally         |
| ለእያንዳንዱ       | for             |
| ከ              | from            |
| አለምአቀፍ         | global          |
| ከሆነ            | if              |
| አስገባ           | import          |
| ውስጥ            | in              |
| ነው             | is              |
| ላምዳ            | lambda          |
| ከባቢያዊ-ያልሆነ   | nonlocal        |
| አይደለም          | not             |
| ወይም            | or              |
| እለፍ            | pass            |
| አስነሳ           | raise           |
| መልስ            | return          |
| ሞክር            | try             |
| እስከ            | while           |
| አብሮ            | with            |
| አመንጭ           | yield           |

### Amharic Function Aliases

Selected built-in functions have Amharic aliases. Currently, this includes:

*   **`print`**: `አትም`

## How to Build

To build this modified CPython from source, follow these steps:

1.  **Install Build Dependencies**: Ensure your system has all the necessary dependencies for building CPython. This typically includes a C compiler (like GCC or Clang), make, and other development libraries. Refer to the official CPython [Developer's Guide](https://devguide.python.org/getting-started/setup-building/) for detailed prerequisites for your operating system.

2.  **Regenerate Parser and Other Generated Files**: Due to the changes in the grammar and keyword definitions, you need to regenerate the parser and other auto-generated files. Run the following command from the root of the CPython repository:
    ```bash
    make regen-all
    ```

3.  **Compile CPython**: After regenerating the necessary files, compile CPython using:
    ```bash
    make
    ```
    For a faster build, you can use parallel compilation by specifying the number of jobs (e.g., `make -j8` if you have 8 CPU cores).

## Example Usage

Here's a simple Python code snippet demonstrating the use of Amharic keywords and the `አትም` print alias:

```python
# Example Amharic-Python

ተግባር አስላ(ሀ, ለ):
  ከሆነ ሀ > ለ:
    መልስ ሀ - ለ
  አለበለዚያ:
    መልስ ለ - ሀ

አትም(አስላ(5, 10)) # Output: 5

አትም("ሰላም፣ ዓለም!") # Output: ሰላም፣ ዓለም!

ለእያንዳንዱ ንጥል ውስጥ [1, 2, 3]:
    ከሆነ ንጥል == 2:
        አትም("2 ተገኝቷል!")
        ቀጥል
    አትም(ንጥል)

ከሆነ እውነት እና አይደለም ሐሰት:
    አትም("ሎጂክ ይሰራል!")
```

## Note on Build Errors

If you encounter build errors after modifying the grammar or other core files:
*   Ensure that `make regen-all` was run successfully. Missing this step is a common source of issues.
*   Double-check that all build dependencies for CPython are correctly installed on your system.
*   Clean your build directory (`make clean` or `git clean -fdx`) and try the build process again.
*   For specific errors, consult the error messages provided by the compiler, as they often point to the exact location and nature of the problem.

This project aims to be a proof-of-concept and a starting point for broader Amharic language integration in Python.
