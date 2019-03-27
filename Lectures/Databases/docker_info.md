## MySQL/postgres
An example of a postgres project is [here](../intro_web_services/class_roster_server). For SQL databases, we store data across tables and specify relationships across those tables (as discussed in the previous database lecture). If you use MySQL or Postgres in this class, you will not __have__ to use an ORM or schema manager since SQL databases impose their internal schemas. 

## Docker
To install Docker, follow these instructions [for mac](https://docs.docker.com/docker-for-mac/install/) and [for ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and finally if you really have to, for [windows](https://docs.docker.com/docker-for-windows/install/).

Docker allows us to run programs (with all of their dependencies) in a consistent environment called a __container__. You can think of this container as a "virtual machine" that runs on your computer, like a mini linux computer running inside your own (although it's way more efficient than that). You can push and pull containers that have all of the programs and dependencies already setup to a central place called [DockerHub](https://hub.docker.com/). 

Some common docker commands:
* `docker pull mongo` this pulls down the full mongodb database container from DockerHub
* `docker run mongo` this runs the docker container and the program (mongodb) that comes with it.
* `docker run -it mongo bash` this starts up the mongodb container, and opens up `bash` shell inside the container (kind of like ssh-ing into the container.
* `docker exec -it <container_id> bash` -- "ssh" into a currently running container. 

When we run containers, we can __bind__ container ports to our local machine ports and even bind parts of our filesystem into the container. 

In the future, we'll explore Docker further, and chat about how to create your own containers for your software.

### Run MongoDB using Docker
Below is the minimal example of a program that connects to a MongoDB database called `bme590` running on `localhost:27017`. To get a database running using `Docker` (which we will introduce in class) simply run 

```
docker run -v $PWD/db:/data/db -p 27017:27017 mongo
```
which will run the `mongo` container, binding the container's `27017` port to your computer's `27017` and binding the current directory's folder `db` to be the place where data is stored inside the container. 
