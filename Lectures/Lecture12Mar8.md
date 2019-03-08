# Introduction to Web Service Design

Let's start with some html

http://people.duke.edu/~apw2/

Make a simple page

```

<html>
    <head>
        <title>Python is awesome!</title>
    </head>
    <body>
        <h1>Web Server!</h1>
        <p>Congratulations! The HTTP Server is working!</p>
    </body>
</html>

```

Make a new file index.html in a new repository

This is a web page that we want to serve out, now create a web server that will serve this html page.

In order to create a web server in Python 3, you will need to import two modules: http.server and socketserver

save code as server.py

```

import http.server
import socketserver

PORT = 8080
Handler = http.server.SimpleHTTPRequestHandler

with socketserver.TCPServer(("", PORT), Handler) as httpd:
    print("serving at port", PORT)
    httpd.serve_forever()
    
```

Now we have a functional http server

A web server is a process that listens to incoming requests on specific TCP address, dentified by an ip address and a port number

Also needs to be told how to handle incoming requests.

http.server.SimpleHTTPRequestHandler is a simple HTTP request handler that serves files from the current directory and any of its subdirectories

### socketserver.TCPServer class

An instance of TCPServer describes a server that uses the TCP protocol to send and receive messages (http is an application layer protocol on top of TCP).

To instantiate a TCP Server, we need two things:

1- The TCP address (IP address and a port number)

2- The handler

```
socketserver.TCPServer(("", PORT), Handler)
```

the TCP address is passed as a tuple of (ip address, port number)

Passing an empty string as the ip address means that the server will be listening on any network interface (all available IP addresses).

And since PORT stores the value of 8080,  the server will be listening on incoming requests on that port.

For the handler, we are passing the simple handler http.server.SimpleHTTPRequestHandler

```
Handler = http.server.SimpleHTTPRequestHandler
```

finally, serve_forever is a method on the TCPServer instance that starts the server and begins listening and responding to incoming requests.

now, let's start the webserver

```
$ python server.py
serving at port 8080
```

Open your browser and type localhost:8080 in the address bar.
