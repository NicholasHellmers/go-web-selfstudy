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
* Only GET and POST are supported by all browsers (HTML).
* To support PUT and DELETE XMLHttpRequest can be used.

### 1.5.5) Request headers
* <u>*Request Headers*</u> are colon-separated name-value pairs in plain text, terminated by a carriage return (CR) and line feed (LF).
* HTTP request headers are mostly optional.
* The only mandatory header is the Host header field.

## 1.6) HTTP response
* Like an HTTP request, an HTTP response consists of a few of plain text:
  1. Status line
  2. Response header
  3. Blank line
  4. Response body (optional)
* Example:
``` HTTP
200 OK
Date: Sat, 22 Nov 2014 12:58:58 GMT
Server: Apache/2
Last-Modified: Thu, 28 Aug 2014 21:01:33 GMT
Content-Length: 33115
Content-Type: text/html; charset=iso-8859-1
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns='http://www.w3.org/1999/xhtml'> <head><title>Hypertext Transfer Protocol -- HTTP/1.1</title></head><body>…</body></html>
```

### 1.6.1) Response status code
* There are 5 classes of status codes:
  1. 1xx: Informational
  2. 2xx: Success
  3. 3xx: Redirection
  4. 4xx: Client Error
  5. 5xx: Server Error

### 1.6.2) Response headers
* Common response headers:
    * Allow
    * Content-Length
    * Content-Type
    * Date
    * Location
    * Server
    * Set-Cookie
    * WWW-Authenticate

## 1.7) URI
* Berners-Lee introduced the concept of Uniform Resource Identifier (URI), uniform resource name (URN), and uniform resource locator (URL) in 1994.
* URI and URL can be used interchangeably.
* This is the general form of a URI: 
``` URI
<scheme name> : <hierarchical part> [ ? <query> ] [ # <fragment> ]
```
* The scheme name is the name of the URI scheme that defines the rest of the URI structure.
* The hierarchical part contains the identification information and should be hierarchical in structure.
* Only the scheme name and hierarchical part are mandatory.
* Let’s look at an example of an HTTP scheme URI:
``` URI
http://sausheong:password@www.example.com/docs/file?name=sausheong&location=singapore#summary
```

## 1.8) Introduction HTTP/2