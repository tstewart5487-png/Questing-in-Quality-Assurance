# Web Applications Study Notes

## 💻 Core Architecture

### Clients
* **Definition:** Software that communicates with a server and requests the information a user needs.
* **Function:** Converts user actions (like clicking buttons or typing) into messages called **requests** and sends them to the server.

### Servers
* **Definition:** A system that processes client requests and generates a **response**.
* **Hardware:** Usually a powerful computer located separately from the clients (e.g., Google's servers in dedicated data centers).

### Networks
* **Definition:** A system of interconnected devices that allows the client and server to exchange data and communicate.

---

## 🌐 Protocols, Methods, and URLs

### The HTTP(S) Protocol
* **HTTP (HyperText Transfer Protocol):** Traditional standard used for web pages to transfer text, pictures, audio, and video. It is **not secure**.
* **HTTPS (HyperText Transfer Protocol Secure):** Secure version of HTTP that **encrypts** the connection to protect data.

### HTTP Methods
* **Definition:** Instructions embedded within the HTTP protocol that tell the server what action the client expects it to perform.
* **Full Method List:** `GET`, `HEAD`, `POST`, `PUT`, `DELETE`, `CONNECT`, `OPTIONS`, `TRACE`, and `PATCH`.
* **Primary Method:** `GET` is used by the client to retrieve data from the server.

### URL (Uniform Resource Locator)
* **Definition:** The web address that acts like a "GPS for websites."
* **Structure:** Combines several key elements in a specific order:
  * **Scheme/Protocol** (e.g., `https://`)
  * **Domain/Host** (e.g., `example.com`)
  * **Path** (e.g., `/users`)
  * **Query Parameters** (e.g., `?id=123`)

---

## 🛠️ Developer Tools (DevTools)

### Purpose
* Allows you to view how a web application is composed and see what it is doing in real-time.
* Enables testing and modifying application behavior on the fly.

### Key QA Capabilities
* **Inspection:** Check what the app is actually doing versus what it is expected to do.
* **🌐 Network Monitoring:** Monitor network requests to catch hidden bugs in data being sent or received.
* **🎨 UI Validation:** Check UI elements for layout, styling, or rendering issues.
* **⚡ Condition Simulation:** Simulate different environment conditions, such as slow network speeds or varying screen sizes.

---

## 💾 Client-Side Storage Mechanisms


| Feature | Cookies | Cache | Local Storage |
| :--- | :--- | :--- | :--- |
| **Primary Purpose** | Authentication and session management. | Storing static web resources (HTML, CSS, JS, images). | Persistently storing large amounts of data (preferences, app data). |
| **Behavior** | Stores small text files. Client-side storage is safer than server-side, though still vulnerable to breaches. | Automatically loads resources locally to eliminate repeated server downloads. | Retains data indefinitely on the client side. |
| **Data Persistence**| Expires based on setup. | Overwritten as needed or cleared by user. | Can **only** be deleted manually. |
| **Security & Size** | Limited data capacity. | Medium capacity for assets. | Holds more data and is more secure than cookies. |
