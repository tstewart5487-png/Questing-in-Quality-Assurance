# Chapter 6 Notes

## Testing with Minimal Requirements

You’ve been given the task of testing the endpoint:

```http
GET /api/v1/kits/{id}
```

And that’s all the information you've received.

### Example Request

Retrieve information about the kit with `id=6`:

```http
GET /api/v1/kits/6
```

The response body is an object containing four key-value pairs that provide information about:

* The kit's ID
* The kit's name
* The products contained in the kit
* The number of products in the kit

---

## Objects

### Programming Objects

An object in programming is a collection of related data and actions that work together.

### JSON Objects

In JSON, an object is a set of key-value pairs wrapped in curly braces `{}`.

Rules:

* Each key is a string.
* Each key has a value.
* Keys must be enclosed in double quotes.

Example:

```json
{
  "id": 6,
  "name": "Starter Kit"
}
```

---

## Using Swagger Documentation

The response model can be found in Swagger:

### KitResponseModel

This model is useful because it shows:

* The expected response structure
* Expected data types
* Required fields

---

## Useful Database Endpoints

### Retrieve All Products

```http
/api/db/resources/product_model.csv
```

This endpoint returns all products available in the database.

### Retrieve All Kits

```http
/api/db/resources/kit_model.csv
```

This endpoint returns all kits stored in the database.

---

## What Should Be Tested?

Based on the available information, verify that:

### Data Types

Response data types match those defined in `KitResponseModel`.

### Response Structure

Response structure matches the API documentation.

### Product Validation

Products returned in the kit exist in the list of available products.

### Data Consistency

The kit data returned by the API matches the corresponding data in `kit_model.csv`.

### Product Count

The value of `productsCount` equals the total quantity of products contained in the kit.

---

# Basic API Response Validation Checklist

When testing responses, always verify:

## Status Code

Examples:

* 200 OK
* 400 Bad Request
* 404 Not Found
* 500 Internal Server Error

## Response Structure

Ensure all expected fields are present.

## Data Types

Verify values match the documented data types.

## Response Data

Confirm values are correct and consistent with source data.

---

# Arrays

Arrays are:

* Stored in square brackets `[]`
* Used to store multiple values under a single key

Example:

```json
{
  "products": [
    {
      "id": 1,
      "quantity": 2
    }
  ]
}
```

---

## JSON Rules

* JSON follows the `key:value` format.
* All keys must be enclosed in double quotes.
* String values must be enclosed in double quotes.

Example:

```json
{
  "name": "Chips"
}
```

---

## JSON Validation

Always validate JSON syntax before testing.

Recommended validator:

https://jsonlint.com/

Using a validator helps:

* Prevent syntax mistakes
* Speed up debugging
* Build familiarity with JSON structure

---

# Array Length Validation

If requirements specify a maximum array length, the API should enforce it.

Example:

If maximum array length = 3

Valid:

```json
[1]
```

```json
[1, 2]
```

```json
[1, 2, 3]
```

Invalid:

```json
[1, 2, 3, 4]
```

Expected result:

* Request rejected
* Appropriate validation error returned

Failure to enforce the limit is a bug.

---

## Nested Arrays

Example:

```json
{
  "box": [
    ["letter", "letter"],
    [],
    [42, 32, 5]
  ]
}
```

This contains:

1. An array containing two strings
2. An empty array
3. An array containing three numbers

---

# Documentation Discrepancies

While reviewing `KitResponseModel`, you may notice fields that appear in documentation but not in example responses.

Example:

The `units` key exists in the model but is omitted from the example response.

This is usually a documentation issue, not an API bug.

### Recommended Action

* Inform your supervisor
* Update the documentation
* Add the missing field to the example response

---

# Testing Values in Key-Value Pairs

When reviewing a request body, create negative test scenarios for every field.

Example:

```json
{
  "id": 1,
  "quantity": 2
}
```

Fields to test:

* `id`
* `quantity`
* Parent object
* Parent array

---

## Common Negative Tests

Ask questions such as:

* What if a negative number is passed?
* What if a value exceeds expected limits?
* What if the value is empty?
* What if the value is the wrong data type?

Examples:

```json
{
  "quantity": -1
}
```

```json
{
  "quantity": 100000000000000
}
```

```json
{
  "quantity": null
}
```

Checking negative numbers and empty values is almost always worthwhile.

---

# Testing Arrays

As QA engineers, we must predict how the system behaves with different array inputs.

### Test Scenarios

* Missing keys in array elements
* Extra keys in array elements
* Empty array
* Incorrect data type
* Different numbers of array elements

Example:

```json
{
  "products": []
}
```

### Possible Result

```http
500 Internal Server Error
```

This usually indicates a bug.

A properly validated request should return a 4xx error with a meaningful explanation.

Example:

```http
400 Bad Request
```

```json
{
  "message": "Products array cannot be empty"
}
```

---

# Testing Objects

## Negative Testing for Objects

Test:

### Empty Object

```json
{}
```

### Missing Object

No object included in the request body.

### Invalid Object Structure

Malformed JSON object.

### Incorrect Data Type

Example:

```json
{
  "products": {}
}
```

Instead of an array, an object is provided.

### Actual Result

```http
500 Internal Server Error
```

This suggests missing schema validation.

### Expected Result

```http
400 Bad Request
```

Example response:

```json
{
  "message": "products must be an array"
}
```

The server should reject invalid input with a clear validation error instead of crashing.
