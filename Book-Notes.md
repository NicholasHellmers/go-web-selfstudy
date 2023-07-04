## 1.3) A quick introduction to HTTP
* <u>Definition</u>: HTTP is a stateless, text-based, request-response protocol that uses the client-server computing model.
* A <u>stateless protocol</u> is one each request from the client to the server returns a response form the server to the clinet. It carries no memory of previous requests.
* <u>*Request-response*</u> is a basic way two computers talk to each other. One machine sends the *request*, the other one sends the *response*.
* HTTP sends data in plain text.

## 1.4) The coming of web applications
* CGI and SSI are two technologies that allow web servers to run programs and scripts on the server side.

## 1.5) HTTP request
* The HTTP request consists of a few lines of text in the following order:
  1. Request line
  2. Request header
  3. Blank line
  4. Request body (optional)
* Typycal HTTP request:
``` HTTP
GET /Protocols/rfc2616/rfc2616.html HTTP/1.1
Host: www.w3.org
User-Agent: Mozilla/5.0
 (empty line)
```
* The first line is called the <u>*request line*</u>. It contains the following information:
  * Request method: (GET)
  * Uniform Request Method (URI): (/Protocols/rfc2616/rfc2616.html)
  * The HTTP version (HTTP/1.1) 
* The next two lines are <u>*request headers*</u>.

### 1.5.1) Request methods
* Common HTTP methods: GET, HEAD, POST, PUT, DELETE, TRACE, OPTIONS, CONNECT, PATCH

### 1.5.2) Safe request methods
* Safe methods are those that do not change the state of the server. They are GET, HEAD, OPTIONS, and TRACE.
* POST, PUT, and DELETE are not safe methods. Meaning data at the server is supposed to be changed.

### 1.5.3) Idempotent request methods
* An *idempotent* method are those that don't change the state of the server the second time you call them.
* All safe methods are idempotent.
* PUT and DELETE are also idempotent but not safe.

### 1.5.4) Browser support for request methods
* 
