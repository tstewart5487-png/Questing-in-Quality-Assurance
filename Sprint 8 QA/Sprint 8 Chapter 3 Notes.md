# Selenium

In PyCharm: `from selenium import webdriver`

## Creating a Driver

- Object of the WebDriver class
- Specify which browser for tests

```python
driver = webdriver.Chrome()   # create a Google Chrome driver
driver = webdriver.Firefox()  # create a Firefox driver
```

### Custom Settings

```python
chrome_options = webdriver.ChromeOptions()              # Create an object for settings
chrome_options.add_argument('--headless')                # Add a setting
chrome_options.add_argument('--window-size=640,480')     # Add another setting
driver = webdriver.Chrome(options=chrome_options)         # Create a driver and pass the settings
```

- `--headless` launches the browser without showing the window
- `--window-size` launches the browser with the specified window size — useful for testing interfaces in systems with a particular screen resolution

## Opening Pages

- `get()`
  ```python
  driver.get('https://google.com/')
  ```

### Maximize Window

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.maximize_window()
driver.get('https://google.com/')
```

## Closing Windows

- `driver.quit()`
- ⚠️ If you don't quit the session, some background processes may fail to shut down correctly, leading to a data leak or an access error.

## Retrieving URL / Assert

```python
current_url = driver.current_url
```

- Saves the URL to `current_url`

### assert

```python
assert current_url == 'https://google.com/'
```

- Checks to see if currently on google.com

```python
assert 'google.com' in driver.current_url
```

## Finding Elements

### find_element()

- Finds one element
- Returns a WebElement object
- If it returns multiple elements, it will find the first one

### find_elements()

- For multiple elements — for example, all of the buttons
- Returned in a list
- If the method finds only one element, it returns a list with only one item
- If it doesn't find any, it returns an empty list

Both methods need arguments:
- ID of a button or other attributes
- XPath or HTML tag

### By

To use `By` class methods, you have to import it:

```python
from selenium.webdriver.common.by import By
```

- `By.ID` for the id attribute
- `By.NAME` for the name attribute
- `By.CLASS_NAME` for the class attribute name
- `By.TAG_NAME` search by the HTML tag
- `By.CSS_SELECTOR` by the CSS selector
- `By.XPATH` by XPath

### Example

```python
import time

from selenium.webdriver.common.by import By
from selenium import webdriver

driver = webdriver.Chrome()
# Open the page (remember, the link is unique for each session)
driver.get("https://cnt-58f226c9-c4cf-45ff-bc0e-36185cc797fa.containerhub.tripleten-services.com/")

# Pause execution for 2 seconds to allow the page to load fully
time.sleep(2)

# To find one element, returns one unique element
driver.find_element(By.CSS_SELECTOR, "img.logo-image")

# To find a group of elements, returns more than one element
driver.find_elements(By.CSS_SELECTOR, ".mode")

# Close the browser and end the WebDriver session
driver.quit()
```

- 💡 If the `find_element()` method doesn't find the required element, the test will stop with an error, and the browser window will remain open. If this happens, don't forget to close the browser manually to avoid overloading your computer.

### Saving an Element for Later Use

```python
element = driver.find_element(By.CSS_SELECTOR, "img.logo-image")
print(element)
```

## Retrieving Element Properties

### get_property()

- Retrieves specific property values of an element, like its current real-time value or state
- Useful for:
  - Input fields
  - Checkboxes
  - Elements whose values might change dynamically through user interactions or JavaScript changes
- `get_attribute("value")` retrieves the value attribute as written in the HTML
- `get_property("value")` retrieves the updated value as modified by user actions or scripts

```python
# Find the input element by its ID
input_element = driver.find_element(By.ID, "from")

# Simulate user typing "East" into the input field
input_element.send_keys("East")

# Access its property
print(input_element.get_property("value"))

# Output: "East"
```

## Clicking an Element

- `click()`

```python
driver.find_element(By.XPATH, "//button[@aria-pressed='false']").click()
```

## Explicit Waits

- Halt a process for an exact period of time
- If the page loads faster, the process will no longer wait

```python
from selenium.webdriver.support.wait import WebDriverWait
WebDriverWait(driver, 3)
```

### Explicit Wait Conditions

- `expected_conditions` — class first, `.`, then the condition itself
- `element_to_be_clickable`: waits until the element is clickable
- `presence_of_element_located`: waits until element is present on the page
- `visibility_of_element_located`: waits until element is present on the page and visible

```python
expected_conditions.element_to_be_clickable
```

- ⏰ Explicit conditions won't work without an import:
  ```python
  from selenium.webdriver.support import expected_conditions
  ```
- Is this specific element ready for a human to use it?

## Implicit Waits

- Global — applies to every single element search
- Looks only for the element to be present in the DOM
- Does the HTML exist yet?

### Waits Comparison

- **Sleep** enforces a static wait, pausing execution for a specified number of seconds, regardless of the circumstances.
- **Implicit waits** offer a fixed timeout for finding elements, but they don't have to wait until the given time if the element is found earlier. However, they don't adapt to other conditions beyond the presence of the element.
- **Explicit waits** are more dynamic and can be configured to pause until certain conditions are met, such as an element becoming visible or clickable. Once the condition is satisfied, the wait is lifted, and the process continues.

## Filling Fields

### send_keys()

```python
send_keys("Buy a Hamster")
```

### Clearing Fields

- `clear()`

```python
driver.find_element(By.ID, "from").send_keys("East 2nd Street, 601")
driver.find_element(By.ID, "to").send_keys("1300 1st St")
driver.find_element(By.ID, "from").clear()
```

## text

- Retrieves the text of an element

```python
driver.find_element(By.CLASS_NAME, "logo-disclaimer").text
```

Example use case: imagine you have to test that the word "PLATFORM" is spelt correctly on Urban Routes.