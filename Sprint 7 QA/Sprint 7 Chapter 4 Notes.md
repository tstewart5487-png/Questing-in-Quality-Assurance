# Multi-Branch If Statements

- The first check is done using an `if` statement
- Additional conditions use `elif` blocks
- Multiple `elif` blocks can be used as needed
- The code corresponding to the condition that first evaluates to `True` will be executed
- If all conditions turn out to be `False`, the statement in the last `else` block is executed
- **Important:** only one block will be executed, no matter how many conditions or `elif` blocks you have!

## Boolean Operators

| Operator | Behavior |
|---|---|
| `and` | Returns `True` if both conditions are `True` |
| `or` | Returns `True` if at least one of the conditions is `True` |
| `not` | Inverts the Boolean value |

## `range()`

```python
range(start, stop, step)
```

- **start**: The starting number is optional and defaults to `0`
- **stop**: The number where the range stops — not included
- **step**: How much the numbers will be increased is optional, and by default, it increases by `1`

## `continue`

The `continue` keyword is used together with a nested `if` statement in order to skip an iteration.