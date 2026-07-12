# Chapter 2: DOM

## DOM (Document Object Model)

- Model of a web page made up of different objects
- Manages structure and style

```html
<!doctype html>
<html lang="eng">
  <head></head>
  <body>
    <h1>Hi</h1>
    <p style="color: red">How are you?</p>
  </body>
</html>
```

- Children are the elements in a DOM tree one level below the selected element
- An element 1 level above is the parent
- Descendants are below
- Ancestors are above

## HTML Elements

HTML elements are made up of:
- Opening tag
- Content
- Closing tag
- Element type
  - Tells the browser what to do with the element
  - `h1` are first level headers
  - `h2` are second level headers
- All HTML elements are nodes, but not all nodes are HTML elements
  - An HTML element is a specific type of node that represents only the tags, like `<h1>`, `<p>`, or `<img>`
  - Only tag-based nodes are elements

### Attributes

- HTML elements can have attributes
- Contained in the opening tag only
- Several attributes are separated by a space
- The value of the attribute `id` is an element identifier

## CSS Selector

### Selector

- Python uses this to locate elements in HTML
- Syntax: `tag[attribute='value']`
- If a selector matches more than one element, Python may encounter ambiguity when running an automated test
- Using the `id` attribute is ideal for locating elements because it's unique
  - However, not all elements have ids
  - In such cases, other selectors, like `class`, might also be reliable
  - Syntax: `tag[class=value]`

### Short Notation for Locators

The `.` and `#` symbols are shortcuts to target elements by their class or id attributes:
- `.` is used for classes. For example, `.button` selects all elements with the class "button"
- `#` is used for ids. For example, `#header` targets the single element with the id "header"

Example — rewriting the "From" field selector using shortcuts:

```python
# Locator for the "From" field using long notation
input[id='from']

# Locator for the "From" field using short notation
input#from
```

## XPath

- XML Path language
- More flexible and can select elements based on things like their content
- Syntax: `//tag[@attribute='value']`
  - `//` means we are searching anywhere in the HTML document
  - `tag` represents the HTML tag of the element
  - `[@attribute='value']` is called a predicate
    - Filters elements based on an attribute and its value
    - `@` refers to an HTML attribute of an element
- Always test your XPath and CSS Selector expressions in the browser's developer console before using them in your automated tests
- Allows us to target elements based on:
  - Attributes, text, or their position in the document

### Examples

- `//a[contains(@href, "https://www.google.com/intl")]`
  - Finds a link element that contains a specific URL
  - The `<a>` tag indicates the link element in its `href` attribute
  - `contains` is a special XPath method that helps search for specific text
- `text()` finds elements based on the text they contain
  - Syntax: `//tag[text()='value']`
  - Will only match a tag with exactly the text
- `contains()` finds elements containing partial text
  - Match any tag element that includes the text
  - Syntax: `//tag[contains(text(), "text")]`

### Interview Questions

Interview questions about XPath sometimes do come up. Here are two examples:
1. Locating the parent element based on its child: `//`
2. Finding all elements with a certain class name: `//tag[@class='value']`

Questions about locator strategy are frequently asked in interviews, and following this flow will help you give an accurate and efficient answer:

1. **Always use IDs if available** — using a unique ID is the fastest and most reliable way to locate an element. But sometimes elements do not have ids, or even if they do, they may be dynamic (ids that change with each refresh); in this case, we cannot use ids.
2. **Use class or name as a second alternative** — make sure the class name or name is not available or unique; if it is not, we will look at other alternatives.
3. **Use CSS Selector as a custom locator** — CSS Selector is faster than XPath, so it should be the first preferred custom locator. However, it has fewer features than XPath.
4. **Use XPath as a final option** — if you need to locate with text, use methods such as `contains`, or move from a child element to a parent element, XPath will be a great final savior. Although XPath has slower performance than CSS Selector, you can locate any element with XPath.

## Writing an Automation Test

By following these best practices, you'll be able to write reliable and maintainable locators for your automated UI tests.

- **Use unique attributes and values** — when writing locators, it's important to use unique attributes. This ensures that your tests are targeting the correct element on the page. You can use attributes like IDs, names, classes, or data attributes to identify elements.
- 💡 Absolute XPath locators can be fragile. They often rely on an absolute path, so they are prone to breaking when changes are made to the page layout. For this reason, it's best to avoid them.
- **Use descriptive names** — this makes it easier to understand which elements your tests are targeting.
- **Keep your locators up to date** — as a page's layout changes, you might need to update your locators. Make sure to review and update your locators regularly to ensure that they still target the correct elements.