# HTTP Requests, Responses, and Traffic Tools

## Requests and Responses

HTTP protocol is made up of requests and responses. When reporting a bug, you'll want to confirm it's occurring in the part of the system you're testing — knowing where it occurs lets you report it accurately. Even in black-box testing with no server access, you can peek behind the scenes to see what's going on.

---

### Request

A request has 3 components:

**1. Start Line**

```
GET /qa-engineer.html HTTP/1.1
```

This line shows a request being sent for the `qa-engineer.html` page.

**2. Headers**

```
Host: www.tripleten.com
Accept-Encoding: gzip, deflate
```

Shows the website being requested.

**3. Body (Optional)**

A `GET` request doesn't include a body — we're simply asking for a page. A `POST` request, used to pass data to the server (such as form data), includes a body:

```
Content-Type: application/json

{
  "name": "Lula",
  "email": "lula@urbanscooter.tripleten.com"
}
```

---

### Response

A response is received from the server as a reply to a request. It has several components:

**1. Status Line**

```
HTTP/1.1 200 OK
```

| Part | Example | Description |
|------|---------|-------------|
| Protocol | `HTTP/1.1` | The language used to communicate |
| Status Code | `200` | A number indicating what happened |
| Status Text | `OK` | A human-readable label for that number |

**2. Headers**

```
Content-Type: text/html
```

**3. Body**

```html
<!DOCTYPE html>
<html>
  <head><title>TripleTen</title></head>
  <body><h1>Welcome to Example Website!</h1></body>
</html>
```

---

## Traffic Analyzers and Proxies

### Traffic Analyzer (Packet Sniffer)

A traffic analyzer — also called a **packet sniffer** — passively listens to data (packets) traveling through a network. It doesn't stop or change the data; it just "sniffs" it as it passes by.

- Views and logs data passing through a computer network
- Data is sent across the network in **packets**
- Shows packets containing raw information sent by applications — often in binary code, readable only by the applications themselves

### Proxy

A proxy monitors network traffic at the **application layer**, making data human-readable. It lets you view requests and responses between the server and the client — like stopping a waiter, inspecting the dish, and even changing items before it reaches the customer.

**Why use a proxy as a QA engineer?**

- **Understand how an app functions** — Shows the connection between user actions and the requests that get sent. Useful when project documentation is missing information and you need to find it yourself.
- **Spot bugs** — By viewing raw requests and responses, you can pinpoint where a bug is occurring. These can be attached to bug reports so developers can fix errors faster.
- **Test client-side and server-side scripting separately**

---

## JSON

**JavaScript Object Notation** — a text format used for exchanging information between client and server.

---

## Changing the Server Response with DevTools

The main reason to change a server response is to see what happens when different values are received. You can't change the server itself, but you can change what the app receives.

> **Note:** Responses usually come from the server, but when overridden, they come from your computer.

Understanding what causes an issue helps teams prioritize fixes. To override a server response, you typically need a proxy such as:

- [Fiddler](https://www.telerik.com/fiddler)
- [Charles](https://www.charlesproxy.com/)
- [Burp Suite](https://portswigger.net/burp)
- [Requestly](https://requestly.com/)