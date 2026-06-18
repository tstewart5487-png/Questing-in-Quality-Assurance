# Chapter 5 Notes — Designing API Tests

## Table of Contents
1. [Designing API Tests](#designing-api-tests)
2. [Test Coverage for Parameters](#test-coverage-for-parameters)
3. [firstName Parameter — Equivalence Classes & Boundary Values](#firstname-parameter--equivalence-classes--boundary-values)
4. [phone Parameter — Test Cases](#phone-parameter--test-cases)
5. [Test API Validation](#test-api-validation)
6. [Writing an API Test Case](#writing-an-api-test-case)
7. [API Bug Reporting](#api-bug-reporting)

---

## Designing API Tests

When testing API endpoints, it's not enough to simply check whether the endpoint works with all valid data. Just like when testing any other requirement, we need to consider **negative cases** — when the app is not used as intended.

- **Positive test** — expected result is a success message (e.g. status code `200`)
- **Negative test** — expected result is a failure message (e.g. status code `400`)

Every request parameter must be checked with:
- Valid and invalid data
- Values from equivalence classes (EC)
- Boundary values (BV)

---

## Test Coverage for Parameters

To provide sufficient test coverage for an endpoint, design tests for every parameter:

1. Test all data for all parameters to verify the endpoint functions as expected
2. Test positive and negative cases (including BV and EC) for the `firstName` parameter
3. Test positive and negative cases (including BV and EC) for the `phone` parameter
4. Test positive and negative cases (including BV and EC) for the `address` parameter
5. Test positive and negative cases (including BV and EC) for the `email` parameter
6. Test positive and negative cases (including BV and EC) for the `comment` parameter
7. Test a request body with a missing parameter

**Example of a valid request body with all positive values:**

```json
{
    "firstName": "Pamela",
    "phone": "+19998887766",
    "address": "Seattle, 100th Ave 750",
    "email": "pamela@example.com",
    "comment": "Beware of the dog"
}
```

---

## firstName Parameter — Equivalence Classes & Boundary Values

**Requirement:** Only Latin letters, spaces, and dashes. Length no less than 2 and no more than 15 characters.

### Equivalence Classes

| Class | Range | Example Value |
|-------|-------|---------------|
| Invalid (too short) | Less than 2 characters | `P` |
| Valid | 2–15 characters | `Pamela` |
| Invalid (too long) | 16+ characters | `Pamelaelaelaelael` |

### Boundary Values

| Value | Length | Type |
|-------|--------|------|
| *(empty)* | 0 | Boundary — negative |
| `P` | 1 character | Boundary — negative |
| `Pa` | 2 characters | Boundary — positive |
| `Pam` | 3 characters | Boundary — positive |
| `Pamelaelaelael` | 14 characters | Boundary — positive |
| `Pamelaelaelaela` | 15 characters | Boundary — positive |
| `Pamelaelaelaelae` | 16 characters | Boundary — negative |
| `Pamelaelaelaelaea` | 17 characters | Boundary — negative |

> If a value from an equivalence class is the same as a boundary value, you don't need to test it twice.

### Negative Test Values for firstName

When running negative tests, keep all other parameters unchanged to make bugs easier to detect:

- `"P"` — 1 character (too short)
- `"Pamelaelaelaelal"` — 16 characters (too long)
- `"Pamelaelaelaelaela"` — 18 characters (too long)
- `"こんにちは"` — non-Latin characters
- `"Test#123"` — special characters
- `""` — empty string

---

## phone Parameter — Test Cases

| Test Value | Length/Type | Test Type |
|------------|-------------|-----------|
| `"123456789"` | 9 characters | Invalid EC — negative |
| `"+1234567890"` | 10–12 characters with `+` | Valid EC — positive |
| `"12345678901"` | 10–12 characters without `+` | Valid EC — positive |
| `"123456789012345"` | 13+ characters | Invalid EC — negative |
| `"1234567890"` | 10 characters | Boundary value — positive |
| `"123456789012"` | 12 characters | Boundary value — positive |
| `"123456789"` | 9 characters | Boundary value — negative |
| `"1234567890123"` | 13 characters | Boundary value — negative |
| `"abcde12345"` | Letters | Invalid data — negative |
| `"12345@67890"` | Special characters | Invalid data — negative |
| `"+1(234)567-890"` | Special characters interspersed | Invalid data — negative |
| `"123 456 7890"` | Whitespace within number | Invalid data — negative |
| `""` | Empty string | Invalid data — negative |
| *(missing)* | Parameter absent | Invalid data — negative |

---

## Test API Validation

**Validation** checks that a request to the API has been written correctly — that the data is in the necessary format.

Validation is built into the code by developers. It can be done on the client side or server side — but it's critical on the **backend** since hackers shouldn't have access to the server.

Validation can warn us about:
- Incorrect data type in the body
- Incorrect request body structure (e.g. XML instead of JSON)
- XML missing required tags
- Data recorded incorrectly (too many characters, wrong format)

### Testing Validation

To test validation, send requests with **missing parameters** to the API and verify the app reacts as described in the requirements. The goal is to confirm it produces an error due to incorrect structure.

---

## Writing an API Test Case

API test cases require more detail than UI test cases. Every test case must specify:

- The **request method**
- **Request parameters** — in the URL path and in the request body *(no request body needed for GET requests)*
- **Response status code**
- **Response body** (if any)

### Test Case Description

A clearly written test case outlines what the app is designed to do under certain conditions. Examples:

- Check if a new empty kit can be created
- Check if a list of products in a specific kit shows
- Check if specific products can be added to an existing kit

### Steps to Reproduce

- Use a numbered list
- One step = one action
- Include all request data (method, endpoint, request body)

---

## API Bug Reporting

### Steps to Reproduce
Include:
- Request method
- Endpoint
- Parameters
- URL
- Request body (if present)

### Environment
- Server address where the request is sent

### Expected Result
- The response described in the documentation (from apiDoc, Swagger, or other API docs)

### Actual Result
- Text description of what was received
- Include the response body

> If the actual result doesn't match the expected result, execute the test **at least 3 times** with different data in different environments (if they exist) to confirm it's a real bug. Retest after the bug is fixed.

### Bug Report Title Format

`[Request Method] [API Endpoint] — [Status Code] — [Description of Bug]`

### Additional Information to Include

- Data added to the database for testing
- Link to API documentation or relevant section
- Explanation of why this is a bug and the potential consequences
- Severity level and impact on other app functions
- Screenshots demonstrating the bug