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

Make a simple html change and then reload...

localhost is a host name that means this computer. It is used to access the network services that are running on the host via the loopback network interface.

And since the web server is listening on any interface, it is also listening on the loopback interface.

what IP address corresponds to localhost? 127.0.0.1

Can replace 127.0.0.1 and get same result

You can actually start a web server with python without even having to write any scripts.

call command line from terminal 

```
python -m http.server 8080
```

By default, this server will be listening on all interfaces and on port 8080.

If you want to listen to a specific interface, do the following:

```
python -m http.server 8080 --bind 127.0.0.1
```

So why write a script when you can just invoke the server easily from the terminal?

Using SimpleHTTPRequestHandler. Want to create custom services which can't do from the terminal.


## Web service design

Cloud is essential to modern products

# Application Programming Interfaces (APIs)

Example service: Toaster


Toaster -- how do we interact?
toast(num_seconds)
reset() -- resets toaster to idle, ejects toast
get_state()

```
STATE_IDLE = "IDLE"
STATE_TOAST = "TOASTING"
    
class Toaster:
    def __init__(self):
        self.toast_state = STATE_IDLE
        self.temp = 20

    def toast(self, num_seconds):
        self.toast_state = STATE_TOAST
        self.temp = 90
        wait(num_seconds)
        self.reset()
        
   def reset(self):
        self.toast_state = STATE_IDLE
        self.temp = 20
```

#RESTful APIs:  Call functions in the cloude
Library on computer
    import toast.Toaster
    t.toast(10)
    
Process on remote machine
    POST myvm.com/toast {10}
    
Advantage is web service can interact with files on server, such as a database without local copy

Commands you can use include GET POST PUT DEL

Let's use a more sophisticated HTTP library: requests

```
pip install requests
```

Try an example call

```
# importing the requests library 
import requests 
  
# api-endpoint 
URL = "https://maps.googleapis.com/maps/api/geocode/json"
  
# location given here 
location = "Duke University"
key1 = "XXXXX"

# defining a params dict for the parameters to be sent to the API 
PARAMS = {'address':location,'key':key1} 
  
# sending get request and saving the response as response object 
r = requests.get(url = URL, params = PARAMS) 
  
# extracting data in json format 
data = r.json()
print (data)
  
  
# extracting latitude, longitude and formatted address  
# of the first matching location 
latitude = data['results'][0]['geometry']['location']['lat'] 
longitude = data['results'][0]['geometry']['location']['lng'] 
formatted_address = data['results'][0]['formatted_address'] 
  
# printing the output 
print("Latitude:%s\nLongitude:%s\nFormatted Address:%s"
      %(latitude, longitude,formatted_address)) 
```

You will need to obtain your own API key from google.  
I will share this process, if you would like.




