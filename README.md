# California Privacy Wizard: the game of CCPA opt-outs (and epic wizard battles)


## About

California Privacy Wizard is an epic game of wizard
battles that you play by tagging people on Twitter.

You get new spells by opting out of tracking under
the California Consumer Privacy Act (CCPA), a new law
that protects your personal information from being
traded and sold by database marketers.


## Components

This project has three components: a browser
extension, a database-backed web site, and a Twitter
bot.

 * Browser extension: detects when you have
   successfully completed a quest, and then allows you to
   proceed to the web site to collect your new spell.

 * Web site: tracks your spells and standings.

 * Twitter bot: uses your activity on Twitter to resolve
   battles and apprenticeships.


## Getting started

### On Linux

Install Docker from the package manager and start it
with the service manager.  For Fedora:

```
sudo dnf install docker
sudo systemctl start docker
```

Test that you can connect to the Docker daemon with:

```
docker ps
```

If you get an error, you may need to add yourself to
the `docker` group and restart Docker.

```
sudo groupadd docker && sudo gpasswd -a ${USER} docker && sudo systemctl restart docker
newgrp docker
```


### On Mac OS

[Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/).
(You do not need to make a Docker Hub account, just start Docker.)


## run tests

Run the tests in a container.

	./test.sh

(Docker must be running and you must be able to connect to it.)


## Use the web application in a demo environment

This script will attempt to copy data from the live
site, then start a local copy in a container.

	./web.sh

Visit the site at: http://localhost:5000/

Your changes in the `src` directory will show up in
the container, and Flask is configured to auto-reload
when you modify anything.


## clean up Docker containers and images

This script is only for development systems where you
aren't using Docker for other things.  **Don't run this
script on a production system.**

It keeps the base Debian images and images with extra
system packages installed (because these images take
a while to build and don't change often) and removes
all the other images.

./cleanup.sh


# Dependencies

**PostgreSQL:** Widely used RDBMS.

**Python 3:** Language runtime.

**Python packages**

 * Authlib: OAuth support.

 * psycopg2: Widely used adapter for PostgreSQL.

 * flask: Full-featured but relatively simple web development framework.

 * loginpass: Wrapper for OAuth


# Third parties

**Twitter:** Because Twitter game.


# References

[Authlib: Python Authentication](https://docs.authlib.org/en/latest/index.html)

[Flask, A Python Microframework](http://flask.pocoo.org/)

[The Flask Mega-Tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)

[Getting started with Docker (on Fedora Linux)](https://developer.fedoraproject.org/tools/docker/docker-installation.html)

[psycopg2](https://pypi.org/project/psycopg2/)

[PostgreSQL: Documentation](https://www.postgresql.org/docs/)

