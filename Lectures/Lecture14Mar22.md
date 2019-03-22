# Interacting with a web service

Review general info flow:
https://github.com/dward2/BME547/blob/master/Resources/WebServices/server_client_diagram.md


Look at specific example - ideal weight calculator
https://github.com/dward2/BME547/blob/master/Resources/WebServices/server_client_interactions.md

code is available at 

https://github.com/dward2/BME547/blob/master/Resources/WebServices/iwc_client.py
https://github.com/dward2/BME547/blob/master/Resources/WebServices/iwc_server.py

web server
https://github.com/dward2/BME547/blob/master/Resources/WebServices/flask_web_server.md


## How to use more than one screen remotely

Let's get this running on our VM

First, set up a new repository in git hub - called mine web-app-design

```
git init
git add .
git commit -m "first commit"
```
Copy URL of repository on github
```
git remote add origin <URL>
git remote -v
git push origin master
```

Now open a terminal window to the vm and clone repository
```
git clone <URL>
```
Need to set up virtual env again
First install pip (can take some time)
```
sudo apt install python3-pip
```
Verify installation with
```
python3 -m pip version
```
Should be 9.0.1

Now install virtualenv
```
python3 -m pip install --user virtualenv
```

Screen

https://github.com/dward2/BME547/blob/master/Resources/WebServices/screen.md





## Deploying Flask Servers in Production
When we run `flask` applications using the `FLASK_APP=server.py flask run` (or `python server.py`) command, we are using Flask's development server to serve requests for our application. The flask development server is useful for debugging and for development but lacks efficiencies and the ability to have process-level load balancing (more on this later) that we might want in production when serving our app to the world. 

### gunicorn deployment

We will be using the `gunicorn` tool to serve our `flask` application logic in production. The `flask` decorators we use to specify our routing and application logic expose a consistent API (called `wsgi`) that allows us to switch out the flask development server with another server like `gunicorn` that will receive HTTP requests and route them efficiently to our application logic (as specified by our routes/decorators). 

An example application that we may want to serve can be found in the [gunicorn_example](gunicorn_example) folder. Go there, activate an environment, and install the requirements (`pip install -r requirements.txt`). This will install the `gunicorn` dependency. 

To run that sample application simply run

```sh
gunicorn --bind 127.0.0.1:5000 main:app
```

The `main:app` comes from the fact that our `flask` application is in the module `main` (`main.py`) and that the top level identifier for the flask application is called `app` (see line 2 of `main.py`). 

#### Public facing deployments
When you `bind` `127.0.0.1` the loopback address, your server will __only__ process requests that originate from your machine. This means that if I want to send a request to your server from my machine, I cannot do so. To allow public computers to send requests to your server, you need to bind the special address `0.0.0.0` as follows:

```sh
gunicorn --bind 0.0.0.0:5000 main:app
```

#### Load balancing
`gunicorn` can spin up multiple "worker" processes that allow for some additional effiencies from asynchronous processing of requests. What this means is that multiple requests can be processed at the same time on the same machine instead of requiring that each request fully complete before processing the next one on the queue. You can specify the number of workers as follows:

```sh
gunicorn --bind 127.0.0.1:5000 --workers 4 main:app
```

##sending emails

https://github.com/dward2/BME547/blob/master/Resources/WebServices/sendgrid.md



## Mini-project
* Push your web service from last class to a github repository `flask_getting_started` under your github user
* Clone your repository to your VM
* Deploy it using gunicorn in a `screen`
* Write a client program (`client.py`) using the `requests` library (see the [previous lecture](../intro_web_services/Requests.ipynb)) that calls every API written on your web server and outputs the results to `STDOUT` (your terminal). You should be sending requests to an address that looks something like `vcm-3461.vm.duke.edu:5000`. 
* Commit this client program into your `flask_getting_started` repository (even though it is not needed for the server side of this project).
