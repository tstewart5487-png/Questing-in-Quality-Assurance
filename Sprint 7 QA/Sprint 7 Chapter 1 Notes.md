# Chapter 1

## Arithmetic Operators in Python

| Action | Operator | Notes | Example | Result |
|---|---|---|---|---|
| Add | `+` | | `3 + 4` | `7` |
| Subtract | `-` | | `3 - 4` | `-1` |
| Multiply | `*` | | `3 * 4` | `12` |
| Raise to power | `**` | Raising to the power means multiplying the number by itself a certain number of times. For example, `3 ** 4` means `3*3*3*3` | `3 ** 4` | `81` |
| Divide with a remainder | `/` | Dividing with a remainder means dividing two numbers where the result isn't whole, leaving some part of the number undivided. The remainder is the leftover part of the division. In Python, a remainder is always a float. | `3 / 4` | `0.75` |
| Divide without a remainder | `//` | If you use `//`, the remainder is discarded. This is also called floor division. | `3 // 4` | `0` |
| Find modulus | `%` | `%` is used to find the remainder of the division between two numbers, which is called modulus. | `3 % 4` | `3` |

### Order of Operations

| When? | Operation | Operator |
|---|---|---|
| First priority | Separating expressions | `()` |
| Second priority | Exponentiation | `**` |
| Third priority | Multiplication, division with remainder, division without remainder, modulus | `*`, `/`, `//`, `%` |
| Fourth priority | Addition and subtraction | `+` and `-` |

## Comparison Operators

Comparison operators compare two values or expressions, and can be used to write Boolean expressions in Python.

The six comparison operators:

| Comparison | Operator | Example |
|---|---|---|
| Less than | `<` | `3 < 4` |
| Greater than | `>` | `4 > 3` |
| Less than or equal to | `<=` | `3 <= 4` |
| Greater than or equal to | `>=` | `4 >= 3` |
| Equal to | `==` | `3 == 3` |
| Not equal to | `!=` | `3 != 4` |