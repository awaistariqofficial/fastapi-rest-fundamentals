# How Do Web Services Work?

Web services and REST APIs power most of the apps and websites we use every day. They let different applications talk to each other and share data over a network — usually the internet.

## API vs. Web Service

An **API** (Application Programming Interface) is a general term for any way software communicates with other software. A **web service** is a specific *type* of API that uses web technologies — like HTTP — to exchange data over a network.

> Every web service is an API, but not every API is a web service.

**REST APIs** are the most common type of web service. They follow a specific set of rules for how data is requested and returned. This repo focuses on web services at a high level; REST specifically deserves (and gets) its own deep dive.

## What Is a Web Service?

Think of a web service as a **software-to-software bridge**. It has no user interface and isn't meant to be used directly by people — it exists purely to exchange data between applications.

## Core Characteristics

For a system to qualify as a web service, it typically has to be:

| Characteristic | What It Means |
|---|---|
| **Server-hosted** | Runs online like a website, but exposes data or functionality instead of visual pages |
| **Machine-to-machine** | Built for apps to consume programmatically, not for humans to view directly |
| **Language-agnostic** | Can be written in any language (Java, C#, Python, etc.) and still be consumed by apps written in different languages |
| **Platform-agnostic** | The OS or platform it runs on doesn't matter — a Linux-hosted service can talk to a Windows client, and vice versa |
| **Standards-based** | Uses standard web protocols — HTTP/HTTPS for data transfer, FTP for files, SMTP for email |

## Types of Web Services

The two most well-known approaches are **REST** and **SOAP**, though others exist, like **XML-RPC**.

### REST (Representational State Transfer)

REST is by far the most widely used approach today — simple, flexible, and a natural fit for the web.

REST APIs expose **resources**, typically represented as URL paths like `/users` or `/users/20`. When a client requests a resource, the server returns a **representation** of it — most often in JSON, but sometimes XML or plain text.

Clients choose the format they want using the `Accept` HTTP header:

```bash
Accept: application/json
```

```bash
Accept: application/xml
```

**Example JSON response:**

```json
{
  "id": 20,
  "name": "John Doe",
  "email": "john@example.com",
  "role": "admin",
  "createdAt": "2025-09-22T10:30:00Z"
}
```

**Same resource in XML:**

```xml
<user>
  <id>20</id>
  <name>John Doe</name>
  <email>john@example.com</email>
  <role>admin</role>
  <createdAt>2025-09-22T10:30:00Z</createdAt>
</user>
```

### SOAP (Simple Object Access Protocol)

SOAP only uses XML and is common in enterprise systems that need stricter standards and security guarantees.

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
   <soapenv:Body>
      <getUser>
         <userId>20</userId>
      </getUser>
   </soapenv:Body>
</soapenv:Envelope>
```

### XML-RPC

Encodes requests and responses in XML. Lightweight, but less flexible than REST.

### UDDI

Not a data-exchange protocol itself — **UDDI (Universal Description, Discovery, and Integration)** is an XML-based directory where businesses can list, discover, and describe available web services.

## Quick Comparison

| | REST | SOAP | XML-RPC |
|---|---|---|---|
| Data format | JSON, XML, plain text | XML only | XML only |
| Flexibility | High | Lower (strict standard) | Low |
| Typical use case | Modern web/mobile apps | Enterprise systems | Legacy/simple RPC calls |

---

*Up next: a deeper dive into how REST APIs work — methods, status codes, and resource design.*
