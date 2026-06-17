# Chapter 2 Notes: Making a GET Request with Postman

## 📋 Table of Contents
1. [Introduction to Postman](#-introduction to postman)
2. [Adding Parameters to Requests](#-adding-parameters-to-requests)
    * [Path Parameters](#1-path-parameters)
    * [Query Parameters](#2-query-parameters)
    * [Dynamic URLs in Postman](#-dynamic-urls-in-postman)
3. [Making POST Requests](#-making-post-requests)
    * [Request Body vs. GET Requests](#request-body-vs-get-requests)
    * [Writing the Request Body](#%EF%B8%8F-writing-the-request-body)
    * [QA Verification Checklist](#-qa-verification-checklist)
4. [Making PUT and DELETE Requests](#-making-put-and-delete-requests)
5. [The CRUD Framework](#-the-crud-framework)
6. [Authorizing Requests](#-authorizing-requests)
    * [Bearer Tokens](#bearer-tokens)
7. [Working with cURL](#-working-with-curl)
    * [Example cURL Command](#example-curl-command)
    * [Breakdown of the Command](#breakdown-of-the-command)
    * [Converting Postman Requests to cURL](#-converting-postman-requests-to-curl)
    * [Converting cURL Requests to Postman](#-converting-curl-requests-to-postman)

---

## 🚀 Introduction to Postman
[Postman](https://www.postman.com/) is a comprehensive API development environment and testing tool.
* Allows you to query and test APIs.
* Makes it easy to analyze the results of requests.
* Organizes queries into **Collections**.
* Allows you to export prepared requests and share them.

> **What is an Endpoint?**  
> An endpoint is a specific path where a system can send requests to access or send data.

---

## 🛠️ Adding Parameters to Requests
Parameters provide additional information that helps the server process requests more specifically, allowing you to build complex queries.

### 1. Path Parameters
* Attached directly to a URL.
* Point to a specific resource.
* **Ordering:** Will always come before query parameters because they are part of the URL path.

### 2. Query Parameters
* Used to pass additional data.
* Appended to the end of the URL.
* Separated from the URL path by a `?`.
* Set using key-value pairs separated by `=`.
* Multiple parameters are separated using `&`.
* **URL Encoding:** `%20` is used to represent a space in URLs.

### ⚡ Dynamic URLs in Postman
Postman features an **Environment** tool. This allows you to set a variable and dynamically insert it into different requests.

---

## 📥 Making POST Requests
Generally speaking, `POST` requests send data to the server to **create or update** something in a database.

### Request Body vs. GET Requests
* **GET Requests:** Ask the server to fetch information from the database without altering anything. They do not have a request body.
* **POST Requests:** Used to make changes to a database, requiring a **Request Body** to tell the server what those changes should be.

### ✍️ Writing the Request Body
1. Open Postman and navigate to the **"Body"** tab.
2. Set the data type to **"raw"**.
3. Choose **JSON** from the dropdown menu.

💡 **Why do we choose the JSON format?**  
Most RESTful endpoints (like those in Urban Grocers) imply using JSON. While you can usually find a template for the request body in the API documentation (like Swagger or apiDoc), documentation is sometimes incomplete.

#### Example Request Body (Creating a Kit)
```json
{
  "name": "My first set",
  "cardId": 1
}
```

#### Example Response Body (`201 Created`)
The `201 Created` status code means the request succeeded and a new resource was created.
```json
{
  "name": "My first set",
  "card": {
    "id": 1,
    "name": "For the situation"
  },
  "productsList": null,
  "id": 7,
  "productsCount": 0
}
```

### 🧑‍💻 QA Verification Checklist
A successful response code does not always mean the action executed correctly in the database. To verify changes:
1. Retrieve the database table containing all the kits and check if your new entry is there.
2. Make a `GET` request that returns a list of kits inside the card.
3. **Tip:** Always save your `POST` requests in Postman to save time if you need to re-run them later (e.g., if the server crashes).

---

## 🔄 Making PUT and DELETE Requests
* **PUT:** Used to update or replace an existing resource on the server (e.g., updating the names of items).
* **DELETE:** Used to delete a resource from the server.

### Verifying Database Changes
To make sure a `PUT` or `DELETE` change is reflected, retrieve the resources again. For example, run a `GET` request to see if a specific kit name has changed or if an ID has been removed.

---

## 🧱 The CRUD Framework
CRUD is a generalized framework for interacting with data or resources across various systems, platforms, and technologies. **HTTP methods used in RESTful APIs are a direct implementation of CRUD:**

| CRUD Action | HTTP Method | Description |
| :--- | :--- | :--- |
| **C**reate | `POST` | Creates a new resource |
| **R**ead | `GET` | Retrieves a resource |
| **U**pdate | `PUT` | Replaces an existing resource |
| **D**elete | `DELETE` | Deletes a resource |

⚠️ **Interview Tip:** Questions about the CRUD framework frequently come up in technical interviews. Be prepared to explain its definition and elaborate on different implementations you know (APIs, databases, file systems).

---

## 🔐 Authorizing Requests

| Status Code | Meaning | Description |
| :--- | :--- | :--- |
| **401 Unauthorized** | Invalid Credentials | The system does not know who you are. |
| **403 Forbidden** | Wrong Level of Access | The system knows who you are, but you do not have permission. |

> 🔑 **Authentication vs. Authorization**  
> * **Authentication:** Verifies your identity (Who you are).  
> * **Authorization:** Verifies your access and permissions (What you are allowed to do). Authorization happens *after* successful authentication.

### Bearer Tokens
* Unique to each user.
* Kept confidential and never shared.
* Set to expire after a specific time period.
* Sent inside the `Authorization` header so the server can verify the user's identity.
* **Request Headers:** Provide metadata about the request (content type, expected response type, authentication details).

---

## 💻 Working with cURL
`cURL` (Client URL) is a command-line tool and library used for transferring data to and from a server using various protocols, including HTTP and HTTPS. It is available across Linux, macOS, and Windows.

### Example cURL Command
```bash
curl --location --request POST 'https://tripleten-services.com' \
--header 'Content-Type: application/json' \
--data-raw '{"ids": [1, 22]}'
```

### Breakdown of the Command:
* `curl`: Invokes the cURL command-line tool.
* `--location`: Instructs cURL to follow redirects if a resource has moved.
* `--request POST`: Defines the HTTP method (`POST`) and the targeted URL path.
* `--header`: Passes request headers. In this case, `Content-Type: application/json` signals that the incoming data is formatted as JSON.
* `--data-raw`: Holds the raw request body data (passing product IDs `1` and `22`).

### 🔄 Converting Postman Requests to cURL
1. Open your request pane in Postman.
2. Click the **`</>` (Code snippet)** icon on the right-side panel.
3. Open the dropdown menu and select **cURL**.

### 🔄 Converting cURL Requests to Postman
If you copy a cURL command from a developer forum or your browser's Developer Tools network tab, you can parse it into Postman automatically using these steps:

#### Method 1: The Import Button (Recommended)
1. Open Postman and navigate to your workspace.
2. Click the **"Import"** button in the top-left section of the sidebar.
3. Paste your raw cURL text block directly into the text field.
4. Postman will automatically parse the headers, JSON request body, and HTTP methods. Click **"Import"** to generate the runnable Postman request.

#### Method 2: Direct URL Bar Paste
1. Create a new request in a Postman collection.
2. Simply paste the entire cURL text command straight into the **address/URL text box**.
3. Postman will instantly auto-extract the URL path, parameters, data body, and headers for you.
