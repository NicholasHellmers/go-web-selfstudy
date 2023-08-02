# Chapter 1: Go and web applications

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
* HTTP/2 is a binary protocol unlike HTTP/1 which is text-based.
* HTTP/2 is a multiplexed protocol. This means that multiple requests can be sent to the server at the same time.

## 1.9) Parts of a web app
* A web app does the following:
    1. Takes an HTTP input request drom the client in the form of an HTTP request message.
    2. Processes the HTTP request and perfomrs actions on it.
    3. Generates HTML and returns it in an HTTP response message.
* There are two parts to the web app:
    1. The handlers.
    2. The template engine.

### 1.9.1) Handler
* A *handler* recieves and processes the HTTP request sent by the client. Then, it calls the template engine to generate the HTML and returns it in an HTTP response message for the client.
* In the MVC pattern, the handler is both the controller and the model.
* *Service objects* or *functions* are used to manipulate the models, enabling the handler to be as thin as possible by reusing code.

### 1.9.2) Template engine
* A *template* is a piece of code that can be converted into HTML.
* This is sent back to the client as an HTTP response message.
* Can be partly HTML or none at all.
* The *template engine* generates the HTML from the template and data.
* There are two types of templates:
    * Static or logic-less templates.
        * This simply replaces the variables in the template with the desired data.
        * Examples: Mustache, CTemplate.
    * Active templates.
        * This is a template that has logic in it (conditionals, iterators, variables, etc.).
        * Examples: Java ServerPages (JSP), Active Server Pages (ASP), Embedded Ruby (ERB), etc. PHP started as one but evolved into a its own programming language.

## 1.10) Hello Go
* Intro to Go with an example that outputs "Hello, World!" on the browser.
* This is the code in question:
``` Go
package main

import (
    "fmt"
    "net/http"
)

func handler(writer http.ResponseWriter, request *http.Request) {
    fmt.Fprintf(writer, "Hello World, %s!", request.URL.Path[1:])
}

func main() {
    http.HandleFunc("/", handler)
    http.ListenAndServe(":8080", nil)
}
```
* To run it create a subdirectory within this workspace and name it ***first_webapp***. Then, create a file named ***server.go*** and paste the code above.
* Execute the following command in the terminal:
``` Bash
$ go install first_webapp
```

* This will create an executable file named ***first_webapp*** in the ***bin*** directory of the workspace. This has to be in the ***src*** folder of your GOPATH in order to work.

* The first line declares what program this is. In this case, it is a Go executable program.

* Import declares the types of libraries that you're using on your application.

# Chapter 2: Go ChitChat

## 2.1) Let's ChitChat
* This section talks about how a forum works.

## 2.2) Application Design
* This section talks about the application design of a forum.

<p align="center">
  <img src="./assets/chapter_2/Figure%202.2.png" alt="Figure 2.2" style="height: auto; width:50%;"/>
</p>

* This applications's logic is in the server. The client triggers the requests and grants data to the server. The data that is requested is suggested by the server.

<p align="center">
  <img src="./assets/chapter_2/Figure%202.3.png" alt="Figure 2.3" style="height: auto; width:50%; "/>
</p>

* The format of the request of the application is the following:
``` HTTP
http://<servername>/<handler- name>?<parameters>
```

* ***Server name*** is the name of the ChitChat server.

* ***Handler name*** is the name of the handler that will process the request.

* ***Parameters*** are the parameters that are passed to the handler to handle the queries.

* A ***multiplexer*** is a piece of code that examines the request and directs it to the correct handler.

<p align="center">
  <img src="./assets/chapter_2/Figure%202.4.png" alt="Figure 2.4" style="height: auto; width:50%; "/>
</p>

* When the processing is complete, the handler passes the data to the template engine, which will use templates to generate HTML to be returned to the client.

## 2.3) Data model

* This book uses PostgreSQL as the database for the application.

* This section talks about the data model of the application, ChitChat. It comprises of four data structures which map to a relational db.
  * User: Stores user information.
  * Session: User's current login session.
  * Threads: Forum threads.
  * Post: A post within a thread.

* The app is designed to handle users who are signed in and those who are not. Those who are, can create and modify threads and posts. Those who are not, can only view those threads and posts. This design doesn't have moderators.

<p align="center">
  <img src="./assets/chapter_2/Figure%202.5.png" alt="Figure 2.5" style="height: auto; width:50%; "/>
</p>

## 2.4) Recieving and processing requests

* This section goes over the code that processes the requests.

## 2.4.1) The multiplexer

* The multiplexer is a piece of code that examines the coming request and assigns it the correct handler.

* In Go, to create a muliplexer, you need to use **NewServeMux()** from the **net/http** package. In order to redirect it, one must use the **HandleFunc()**. This may look something like this:
``` Go
mux := http.NewServeMux()
```
``` Go
mux.HandleFunc("/", index)
```

* **HandleFunc** takes in the **name of the URL** as the first parameter, and the **name of the handler** as the second parameter. We don't need to provide parameters to the handler function as it is assumed that it takes in a **ResponseWriter** as the first and a pointer to **Request** as the second parameter.

## 2.4.2) Serving Static Files

* The multiplexer can also serve static files in addition to redirecting to the appropriate handler. This can be done with **FileServe()**, this creates a handler that serves files from a given directory. Use the **StripPrefix** function to remove the prefix from the URL that was given.

``` Go
files := http.FileServer(http.Dir("/public"))
mux.Handle("/static/", http.StripPrefix("/static/", files))
```

* This results in:
  - If given "http://localhost/static/css/bootstrap.min.css". Then the server will look for the file "<'application root'>/css/bootstrap.min.css".
  - If it's found it will serve without processing.

## 2.4.3) Creating the Handler Function