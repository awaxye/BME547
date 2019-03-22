### gunicorn deployment

We will be using the `gunicorn` tool to serve our `flask` application logic in production. The `flask` decorators we use to specify our routing and application logic expose a consistent API (called `wsgi`) that allows us to switch out the flask development server with another server like `gunicorn` that will receive HTTP requests and route them efficiently to our application logic (as specified by our routes/decorators). 

An example application that we may want to serve can be found in the [gunicorn_example](gunicorn_example) folder. Go there, activate an environment, and install the requirements (`pip install -r requirements.txt`). This will install the `gunicorn` dependency. 

To run that sample application simply run

```sh
gunicorn --bind 127.0.0.1:5000 iwc_server:app
```

The `main:app` comes from the fact that our `flask` application is in the module `main` (`main.py`) and that the top level identifier for the flask application is called `app` (see line 2 of `main.py`). 

#### Public facing deployments
When you `bind` `127.0.0.1` the loopback address, your server will __only__ process requests that originate from your machine. This means that if I want to send a request to your server from my machine, I cannot do so. To allow public computers to send requests to your server, you need to bind the special address `0.0.0.0` as follows:

```sh
gunicorn --bind 0.0.0.0:5000 iwc_server:app
```

#### Load balancing
`gunicorn` can spin up multiple "worker" processes that allow for some additional effiencies from asynchronous processing of requests. What this means is that multiple requests can be processed at the same time on the same machine instead of requiring that each request fully complete before processing the next one on the queue. You can specify the number of workers as follows:

```sh
gunicorn --bind 127.0.0.1:5000 --workers 4 iwc_server:app
```
