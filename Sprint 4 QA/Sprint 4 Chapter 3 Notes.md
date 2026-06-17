# Chapter 3 Notes: API Documentation & Logs

## Table of Contents
* [API Documentation](#api-documentation)
* [API Documentation Tools](#api-documentation-tools)
  * [1. Swagger](#1-swagger)
  * [2. apiDoc](#2-apidoc)
* [API Logs](#api-logs)
* [Why Logs Matter for QA](#why-logs-matter-for-qa)

---

### API Documentation
API documentation helps developers build apps that connect to an API. Without documentation, it would be difficult to know exactly the endpoints that are available, the type of requests you need to send to them, and the response to expect back.

* **Imperfections**: It is common for API documentation to have gaps or inconsistencies.
* **Urban Grocers**: If information is missing in Swagger, it might be found in apiDoc, or vice versa.
* **Standardization**: Organizations typically use a single tool to maintain their API documentation.

### API Documentation Tools

#### 1. Swagger
* **Color-Coded Methods**: HTTP methods each have a unique color (e.g., `POST` is green, `GET` is blue).
* **Key Components Stated**:
  * Purpose of the request (e.g., view all kits)
  * HTTP method
  * Endpoint added to the URL to run the request
  * Parameters (if any)
  * Request body (if any)
  * Examples of successful and unsuccessful responses

#### 2. apiDoc
* **Automation**: Generated automatically from a file.
* **Key Components Stated**:
  * Purpose of the request (e.g., adding items to kits)
  * HTTP method
  * Endpoint added to the URL to run the request
  * Parameters (if any)
  * Request body (if any)
  * Examples of successful and unsuccessful responses

---

### API Logs
Logs provide a detailed record of everything happening within software systems. This includes applications, operating systems, devices, events, processes, and messages.

* **Contents**: Captures details about actions, errors, changes, or system failures.
* **API Interactions**: Records the detailed account of interactions between a user or system and an API.
* **HTTP Details**: Logs record parameters, headers, and request bodies during HTTP requests.
* **Responses**: Captures the HTTP response and relevant response codes to provide insight into outcomes.
* **Storage**: Logs may be kept in separate text files, special databases inaccessible via API, or monitored via special tools.

### Why Logs Matter for QA
* **Debugging**: Very helpful for debugging, resolving issues, and finding the exact reason an error occurred.
* **Bug Reports**: Used to attach to bug reports as evidence that a bug exists and is not due to user error.
* **Beyond Error Messages**: Critical to understand because the high-level error message is often not enough to identify what exactly happened or why.
