# Chapter 4 Notes — Data Formats & Protocols

## Table of Contents
1. [Data Formats Overview](#data-formats-overview)
2. [HTML](#html)
3. [XML](#xml)
   - [XML Tags](#xml-tags)
   - [Attributes in XML](#attributes-in-xml)
   - [Comments in XML](#comments-in-xml)
   - [XML in Postman](#xml-in-postman)
   - [XML Document Structure](#xml-document-structure)
   - [XML Declaration](#xml-declaration)
   - [Namespaces](#namespaces)
   - [XSD](#xsd)
4. [SOAP](#soap)
   - [Writing a SOAP Request](#writing-a-soap-request)
   - [Sending a SOAP Request](#sending-a-soap-request)
5. [WSDL](#wsdl)

---

## Data Formats Overview

There are four fundamental data formats used when sending a request to a server. These formats ensure the server can effectively comprehend the request and properly interpret the response:

- **HTML**
- **Text**
- **XML**
- **JSON**

---

## HTML

- Mainly used for presenting structured content in a web browser
- Designed to present and display data
- Tags are predefined
- Not case sensitive

---

## XML

- Created to be easily read by both humans and machines
- Uses tags to mark up data
- No premade tags — all tags must be created manually
- Primarily used for exchanging structured data between different computer systems
- Used for **storing and transporting data**
- **Case sensitive**
- An XML document is made of elements; each element consists of tags and their contents

### XML Tags

- An element consists of a **start tag** and an **end tag** (opening and closing tags) — both are required
- The start and end tags share the same name; the end tag includes a forward slash

```xml
<color>  <!-- start tag -->
</color> <!-- end tag -->
```

- Tag names can contain letters, numbers, dashes, underscores, or dots
- Case sensitive
- A tag can be **empty** — use a self-closing tag instead of open/close pairs:

```xml
<weight/>  <!-- instead of <weight></weight> -->
```

**Special characters** — if quotes, angle brackets, or ampersands appear in content, use these substitutions:

| Character | Substitute |
|-----------|------------|
| `<`       | `&lt;`     |
| `"`       | `&quot;`   |
| `'`       | `&apos;`   |
| `&`       | `&amp;`    |

```xml
<expression>0&lt;1</expression>
<!-- if quotes are needed - 'Daisy'-->
<organisation>&apos;Daisy&apos;</organisation>
```

---

### Attributes in XML

- Provide additional description of an object
- Most often used to describe object properties (color, size, weight)
- Consist of a name and a value separated by `=`
- Value is placed in quotes
- Can contain letters, numbers, hyphens, underscores, or dots
- Multiple attributes are separated by spaces

```xml
<box color="red">box</box>
<box color="red" size="large">box</box>
```

---

### Comments in XML

- If a tag is commented out, it will be skipped by whatever program reads the file
- Comments are written in brackets: `<!-- comment text -->`

```xml
<!--Product list-->
<products>
    <!--Description of the first product-->
    <product>
        <!--Here's what it's called-->
        <name>Bread</name>
    </product>
    <!--product>
        <name>Butter</name>
    </product-->
</products>
```

---

### XML in Postman

- Sometimes data may not be suitable for JSON
- To **receive** XML: add `Accept` as the key and `application/xml` as the value in the Request Header
- To **send** a POST request in XML format: select `raw` and `XML` in the Request Body

---

### XML Document Structure

Elements can be grouped together using tags:

- An element made up of other elements is a **parent element** (also called a container element)
- Parent elements are made up of **child elements**
- Elements at the same level are called **siblings**

```xml
<address>
    <city>Miami Beach</city>
    <street>Washington Avenue</street>
    <building>4343</building>
</address>
```

- `address` is the parent
- `city`, `street`, and `building` are children and siblings of each other

Parent elements can simultaneously be child elements:

```xml
<school>
    <address>
        <city>Miami Beach</city>
        <street>Washington Avenue</street>
        <building>4343</building>
    </address>
</school>
```

Here `address` is nested within `school` — it is a child of `school` and a parent of `city`, `street`, and `building`.

The **root element** is the most important element — it includes all other elements from beginning to end.

---

### XML Declaration

Each document starts with a declaration that comes before the root element. Also called the **service element**.

Contains the following attributes:

| Attribute    | Description | Required? |
|--------------|-------------|-----------|
| `version`    | Which version of the XML specification is used | ✅ Required |
| `encoding`   | Describes the encoding (defaults to UTF-8 if not defined) | Optional |
| `standalone` | Whether an external document is needed for reading XML (defaults to `no`) | Optional |

> Declarations are obligatory for XML version 1.1. For version 1.0, they are optional.

---

### Namespaces

- Used when a document contains several groups with the same tags
- A namespace indicates that elements belong to one entity

| Part | Description |
|------|-------------|
| `xmlns` | Specifies the namespace (XML Namespace) |
| Prefix | Follows `xmlns` and serves as the namespace's ID |
| Link | A URL or file path to the namespace description in XSD format |

---

### XSD

**XML Schema Definition** — a description of an XML document's structure. Like a blueprint for XML documents.

Defines:
- Parent and child elements
- Tag names
- Tag attributes
- Data types
- Default values
- Element order

> QA engineers may need to verify that an XML document matches its XSD schema — if it doesn't, the program won't be able to read it. Validation tools include MS Visual Studio, XMLPad, or online validators (paste the XML in one field and the XSD in another, then click "Validate").

---

## SOAP

**Simple Object Access Protocol** — a data exchange protocol where the client and server communicate using specific rules.

Key characteristics:
- Both sides know exactly what to expect from each other (format for data, how to send responses)
- Fewer failures and errors, but requires passing more data
- The server accepts and processes messages strictly according to SOAP specifications
- Messages must be in **XML** — the server cannot read data in other formats
- Uses **HTTP/HTTPS** as the data transfer protocol (other protocols like SMTP can also be used)
- If an API is developed using SOAP, it's called a **SOAP service**
- HTTP methods GET, PUT, and DELETE are **not used directly** — SOAP operations are performed via **HTTP POST requests**

### Writing a SOAP Request

Steps:
1. Write the XML
2. Pack the XML into the SOAP request

**Envelope** — the root element. Indicates the message belongs to the SOAP group. Always required.

```xml
<?xml version = "1.0"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV = "http://www.w3.org/2001/12/soap-envelope">
   ...
</SOAP-ENV:Envelope>
```

- All SOAP elements need a namespace, set in the envelope
- `xmlns` indicates a namespace follows, `SOAP-ENV` is the ID, and the URL points to the element description

**Header** — not required. Contains information needed during processing.

**Body** — required. Contains the XML data passed by the client. A request can only have one body.

---

### Sending a SOAP Request

- Response is received in SOAP format

---

## WSDL

**Web Services Description Language** — describes the structure of a SOAP document.

A **web service** is an app with an API available through a network — you send a request and receive a response.

> Example: a flight booking service sends a request to the airline's system. Both communicate through an API over a network, making them both web services.

Written in XML markup. Consists of tags and attributes.

### WSDL Elements

| Element | Description |
|---------|-------------|
| `<definitions>` | Root element — defines the name of the web service and namespaces used |
| `<types>` | Describes data types used in XML elements exchanged between client and service (uses XSD) |
| `<message>` | Describes the structure of request and response messages |
| `<portType>` | Lists all operations the web service offers |
| `<binding>` | Specifies the protocol, message format, and how to call operations |
| `<service>` | Describes the address and port of the web service |

```xml
<wsdl:definitions
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
    xmlns:tns="http://example.com/tns/"
    xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
    name="ServiceApiEndpointService" targetNamespace="http://example.com/">
...
</wsdl:definitions>
```

### Testing with WSDL and SOAP UI

With WSDL, web services can be tested using SOAP:
- Call methods and verify they do what they're supposed to
- Check whether arguments are passed correctly
- Check type descriptions

This is typically done through SOAP testing tools like **SOAP UI** — upload a WSDL document, the service generates a SOAP message, and you compare the actual result with the expected one.