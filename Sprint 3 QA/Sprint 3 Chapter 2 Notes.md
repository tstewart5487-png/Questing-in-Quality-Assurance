# UI Testing & HTML Reference

## Types of UI Testing

### Visual (Layout) Testing
Tester verifies that the webpage and all UI elements are displayed in the browser as intended based on the requirements. A QA engineer needs to ensure that the visual elements and layouts of a software application or website appear correctly and consistently across different devices, browsers, and resolutions.

### Functional Testing
During functional testing, we must ensure that elements work as they should (buttons can be clicked, links take users where promised). QA engineers need to know how these common elements work inside and out to catch any odd behaviors, even when they're not in the requirements.

---

## Breakdown of UI Elements

### Interaction Elements

#### Input Field
- Space that allows users to enter various types of data
- **Testing tip:** Ensure that input fields accept the correct kind of information.

#### Text Area
- Also called "Text Input Fields" or "Multi-line Text Elements"
- Allows users to type one or more lines
- **Testing tip:** Check for text formatting, character limits, and responsiveness.

#### Radio Buttons
- Circular control elements — empty when unselected, dot when selected
- Every radio button is labeled with a description of the choice it represents
- Toggle switches are also considered radio buttons
- **Testing tip:** Make sure only one radio button is selectable at a time.

#### Checkboxes
- Square-shaped control elements
- A checkmark appears inside the box when selected
- Allow users to select multiple options independently
- May also look like a toggle switch
- **Testing tip:** Make sure multiple checkboxes can be selected without any issues.

#### Combo Boxes
- Combination of a text input field and a dropdown list
- The list drops when the user starts typing or clicks into the field
- **Testing tip:** Check that options are displayed correctly and the chosen option is selectable.

#### Dropdown Lists
- Activated by clicking on any of its areas
- Does not allow free text input
- Offers one or several suggested values
- **Testing tip:** Ensure that selectable options are displayed correctly.

#### Forms
- Allows for user input
- Forms have 3 characteristics:
  1. Has a purpose and allows the user to perform certain actions
  2. A selection of buttons, radio buttons, checkboxes, dropdown lists, and text fields for data entry
  3. User must be notified when the action has been completed
- **Testing tip:** Every part of a form must be tested. For example, to test a sign-up form, you need to enter a name, last name, username, password, and phone number.

#### Carousel and Gallery Elements
- Display a dynamic set of images or content in a rotating format
- Allows users to interact with a variety of visuals
- **Testing tip:** Confirm that the carousel or gallery smoothly transitions between images, responds to user interactions, and displays content correctly. Don't forget to check any navigation buttons or indicators as well.

---

### Call-to-Action Elements

#### Icons
- Visual symbols representing objects and actions performed when clicked
- **Testing tip:** Ensure icons are recognizable and lead to the intended actions.

#### Buttons
- Clickable elements with text inside that perform an action
- **Testing tip:** Confirm that buttons respond appropriately when clicked.

#### Links
- Allow users to navigate to another element or page
- **Testing tip:** Check that links lead to the correct destinations.

---

### Information Elements

#### Labels
- Provide information about other elements
- **Testing tip:** Make sure labels are clear and associated with the correct elements.

#### Tooltips
- Explain the type and format of information that needs to be entered
- Offer additional information when a user hovers over a webpage element
- **Testing tip:** Confirm tooltips appear and disappear at the right times.

#### Placeholders
- Provide a short hint describing the expected value of an input field
- Displayed in the input field before the user enters a value
- **Testing tip:** Ensure placeholders are helpful and disappear when users start typing.

---

### Design Tools

#### Figma
- Interface design tool used by QA engineers to review app layouts

---

## Data Validation Testing

| Type | Description |
|---|---|
| **Positive Testing** | Valid data — verifies the system accepts correct input |
| **Negative Testing** | Invalid data — verifies the system rejects incorrect input |

- **Client-side validation** is handled by frontend code
- **Server-side validation** is handled by backend code

---

## HTML Basics

**Hypertext Markup Language (HTML)** is a markup language (not a programming language) consisting of elements that represent various types of content and functionality on a webpage, including headings, paragraphs, images, links, lists, forms, tables, and more.

### What a QA Engineer Can Do with HTML
- Pinpoint the exact location of an element on the page in a bug report
- Test how web pages behave on different resolutions and devices
- Look for potential security vulnerabilities in page code

### HTML Document Structure

```html
<html>
  <head>
    <!-- Metadata: title, meta tags, links to styles, external scripts -->
  </head>
  <body>
    <!-- Visible content: text, images, links, and other elements -->
  </body>
</html>
```

- HTML elements are organized like a family tree — **parent elements** contain **child elements**
- Elements are represented by **tags**

### Tag Types

#### Paired Tags (opening + closing)
| Tag | Purpose |
|---|---|
| `<p>` | Paragraph |
| `<h1>` – `<h6>` | Headings |
| `<div>` | Division or section |
| `<a>` | Hyperlink |

#### Unpaired Tags (self-closing)
| Tag | Purpose |
|---|---|
| `<br>` | Line break |
| `<img>` | Embeds an image |
| `<input>` | Specifies an input field |

---

### HTML Attributes
- Provide additional information about HTML elements
- Always specified inside the opening or self-closing tag

### Input Tag Types

| Attribute | Description |
|---|---|
| `<input type="text">` | Accepts text input (default) |
| `<input type="password">` | Accepts hidden text, displayed as dots |
| `<input type="checkbox">` | Creates a checkbox |
| `<input type="radio">` | Creates a radio button |

### Select Tag
- Used to create a dropdown list
- Requires the `<option>` tag to define available options

```html
<select>
  <option>Option 1</option>
  <option>Option 2</option>
</select>
```