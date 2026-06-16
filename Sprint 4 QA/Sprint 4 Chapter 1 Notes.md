# Chapter 1 Notes: Application Programming Interface (API)

## Table of Contents
* [How an API Works](#how-an-api-works)
* [Protocols, Rules, and Data Manipulation](#protocols-rules-and-data-manipulation)
  * [Core Concepts](#core-concepts)
* [JSON Responses](#json-responses)
  * [3 Essential Parts of JSON Data](#3-essential-parts-of-json-data)
  * [Additional JSON Structures](#additional-json-structures)
* [API Architectural Styles](#api-architectural-styles)
  * [1. REST (Representational State Transfer)](#1-rest-representational-state-transfer)
  * [2. SOAP (Simple Object Access Protocol)](#2-soap-simple-object-access-protocol)
  * [Why Enterprise Systems Prefer SOAP](#why-enterprise-systems-prefer-soap)
* [API Testing Tools](#api-testing-tools)

---

## How an API Works
1. **Request:** The client sends a request to a server through the API pathway.
2. **Processing:** The server receives the request and queries the database for information.
3. **Response:** The server sends the data back to the client as a payload through the API.

> 💡 **Practical Benefit:** Having numerous APIs allows each server to specialize in a specific task. An engineer's job is often to stick these parts together as needed, while a QA's job is to test that everything was stuck together and works properly.

---

## Protocols, Rules, and Data Manipulation
APIs provide a set of protocols and rules that enable access to the features or data of an operating system, application, or other service. 

Using an API, you can access and manipulate data in a database in three main ways:
* **Retrieving** (using the **GET** command)
* **Changing**
* **Deleting**

A good API documentation contains information about all possible requests that a client can make.

### Core Concepts
* **Pathway:** The API itself.
* **Payload:** The actual data being sent or received.

---

## JSON Responses
Responses typically follow a format called **JSON** (JavaScript Object Notation). It is the most widely used method for storing data in web applications and exchanging data between applications.

### 3 Essential Parts of JSON Data
1. **Curly Brackets `{}`**
   * Indicate where data starts and ends.
   * Nested data can be created with more brackets as needed to create data objects.
2. **Keys**
   * The JSON variable names.
   * Must **always** be wrapped in quotation marks.
3. **Values**
   * The data assigned to the variables.

### Additional JSON Structures
* **Arrays:** Ordered lists in JSON created by placing information inside square brackets `[]`. The order/index of the data inside an array is critical.
* **Null Values:** If you need to explicitly indicate that a certain parameter doesn't have an assigned value, write it as `null` (e.g., `"pets": null`). This indicates the value is undefined.

---

## API Architectural Styles
An API architectural pattern is a design approach used to build and organize an API. It defines how components interact, how data flows, and how the API is accessed.

> 🛠️ **QA Engineering Note:** It is critical for QA engineers to understand the architectural style because it directly affects how architectural components exchange messages. This choice also impacts the specific methods and tools you will use for testing.

### 1. REST (Representational State Transfer)
An architectural style built on guidelines and principles that can be implemented in different ways.

* **Flexibility:** Highly flexible; supports JSON and other data formats.
* **Protocol:** Requires the HTTP protocol.
* **Debugging:** Uses standard HTTP errors, making debugging easy.
* **Security:** Features less advanced built-in security mechanisms.
* **Speed:** Generally faster due to lightweight, compact communication.
* **Popularity:** More common and widely used for casual and standard web applications.

#### REST Data Example (Lightweight JSON)
```json
{
  "name": "Alice",
  "age": 30
}
```

### 2. SOAP (Simple Object Access Protocol)
A strict protocol that defines exactly how messages must be formatted and sent based on rigid standards.

* **Flexibility:** Highly rigid; supports **only** XML text formats.
* **Protocol:** Can work with other protocols, but primarily works with HTTP.
* **Debugging:** May require specialized, heavy tools for debugging and testing.
* **Security:** Features the **WS-Security** (Web Services Security) extension, providing advanced authentication, encryption, and data integrity.
* **Speed:** Slower due to heavyweight formats and strict formatting rules.
* **Usage:** Preferred for complex, enterprise-level applications.

#### SOAP Data Example (Heavyweight XML)
```xml
<person>
  <name>Alice</name>
  <age>30</age>
</person>
```

### Why Enterprise Systems Prefer SOAP
Large organizations with complex needs (such as banking or healthcare systems) choose SOAP for specific operational demands:
* **High Security:** Protecting highly sensitive financial or medical records.
* **Reliability:** Ensuring the system works 24/7 without failure.
* **Complex Transactions:** Processing multi-step payments where every action must be tracked and verified.
* **Massive Scale:** Handling thousands of users and independent systems interacting simultaneously.

---

## API Testing Tools
Because architectural styles dictate how messages are exchanged, QA engineers use specific industry-standard tools depending on the system requirement.

### REST Testing Tools
* **Postman:** The most common tool for manual and automated testing of lightweight HTTP requests and JSON data payloads.
* **Insomnia:** A streamlined, lightweight alternative to Postman focused specifically on REST and GraphQL client capabilities.
* **RestAssured:** A popular Java library specifically used for automated testing of REST services.

### SOAP Testing Tools
* **SoapUI:** The industry standard for testing rigid SOAP protocols, heavy XML validation, and complex WS-Security features.
* **Katalon Studio:** An all-in-one automation tool capable of parsing strict SOAP definitions alongside standard web tests.
