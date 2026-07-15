# POM Wrapper Methods

## Concept: Wrapper/Helper Methods

- A wrapper method combines multiple smaller method calls into one convenient call
- Example: `enter_locations()` wraps `enter_from_location()` + `enter_to_location()`

## Why Locators Aren't Visible in the Wrapper Method

- The wrapper method doesn't touch locators directly
- It just calls other methods, and those methods contain the actual `find_element(*LOCATOR)` calls
- Chain: `enter_locations()` calls `enter_from_location()` / `enter_to_location()`, each of which uses `FROM_LOCATOR` / `TO_LOCATOR`

## Build Order (Dependencies Matter)

- [ ] Define locators as class attributes (`FROM_LOCATOR = (By.ID, 'from')`, etc.)
- [ ] Define the individual action methods that use those locators (`enter_from_location`, `enter_to_location`)
- [ ] Define the wrapper method that calls the individual methods (`enter_locations`)

## Requirement

- The wrapper method depends entirely on the smaller methods already existing
- If `enter_from_location` or `enter_to_location` aren't defined, `enter_locations` has nothing to call and will raise an error

## Trade-off: The Core POM Principle

- Writing the Page Object (POM) takes more upfront effort — more methods, more structure
- Writing tests becomes much simpler — one clean method call instead of repeating `find_element(...).send_keys(...)` everywhere

Example comparison:

```python
# Without POM (repeated in every test)
driver.find_element(By.ID, 'from').send_keys("123 Main St")
driver.find_element(By.ID, 'to').send_keys("456 Oak Ave")

# With POM (one line, reusable)
page.enter_locations("123 Main St", "456 Oak Ave")
```

## Maintenance Benefit

- If a locator (e.g., a CSS ID) changes, you only update it in one place — the POM class
- Every test using that method automatically stays correct — no hunting through multiple test files

## Analogy

- Manager (`enter_locations`) delegates to workers (`enter_from_location`, `enter_to_location`)
- If the workers don't exist, the manager's instructions go nowhere