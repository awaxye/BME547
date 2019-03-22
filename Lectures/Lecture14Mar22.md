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
python3 -m pip --version
```
Should be 9.0.1

Now install virtualenv
```
python3 -m pip install --user virtualenv
```
Now set up virtual env
```
python3 -m virtualenv env
```
and activate
```
source env/bin/activate
```
Don't forget to install dependencies
```
pip install -r requirements.txt
```

Now we can run server app
```
python3 iwc_server.py
```
Switch windows 
```
ctrl-a "
```
then execute code for client
```
python3 iwc_client.py
```

Screen

https://github.com/dward2/BME547/blob/master/Resources/WebServices/screen.md





## Deploying Flask Servers in Production
When we run `flask` applications using the `FLASK_APP=server.py flask run` (or `python server.py`) command, we are using Flask's development server to serve requests for our application. The flask development server is useful for debugging and for development but lacks efficiencies and the ability to have process-level load balancing (more on this later) that we might want in production when serving our app to the world. 



## sending emails

https://github.com/dward2/BME547/blob/master/Resources/WebServices/sendgrid.md



## Mini-project
* Push your web service from last class to a github repository `flask_getting_started` under your github user
* Clone your repository to your VM
* Deploy it in a `screen`
* Write a client program (`client.py`) using the `requests` library (see the [previous lecture](../intro_web_services/Requests.ipynb)) that calls every API written on your web server and prints the results to your terminal. You should be sending requests to an address that looks something like `vcm-xxxx.vm.duke.edu:5000`. 
* Commit this client program into your `flask_getting_started` repository (even though it is not needed for the server side of this project).
