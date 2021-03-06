# ACore CMS

ACore CMS based on wordpress.

## Docker container

If you do not have docker, [install it](https://docs.docker.com/compose/install/).
On a Linux distro, you can install it via package manager, in a debian-based for example you can just run:
```
$ sudo apt install docker docker-composer
```

Well, now you should be able to run it using:
```
$ docker-compose up
```

or using npm:
```
$ npm run docker:start
```

### CLI commands available

```
$ npm run docker:start
```

Run the docekr webservice in foreground mode


```
$ npm run docker:start:d
```

Run the docker webservice in background (deamon)

```
$ npm run docker:shell
```

Run the docker webservice in background and open a bash shell inside the container

```
$ npm run docker:remove
```

Remove all created containers and their volumes

```
$ npm run docker:stop
```

Stop all running containers

```
$ npm run docker:db:export
```

Export the mysql database of the current wordpress installation inside the /data/sql folder (backup)

```
$ npm run docker:db:import
```

Import the sql files under /data/sql folder inside the mysql database of the current wordpress installation (restore backup)

## Configure docker

acore-cms uses our `jsdocker-compose` tool to run docker-compose services, it's an advanced tool that comes with a fully configurable CLI.

You can override some docker-compose options using the " -f" options: [official documentation](https://docs.docker.com/compose/reference/overview/#use--f-to-specify-name-and-path-of-one-or-more-compose-files)

To do it with our scripts you can create an .env.local file inside the root directory of this project. All variables specified inside the .env.local will override the variables existing inside the default .env file, so for instance you can copy and change the following variable:

```
# override extra arguments for docker
DOCKER_EXTRA_ARGS=" -f docker-compose.default.yml"
```

To something like:

```
DOCKER_EXTRA_ARGS=" -f docker-compose.override.yml"
```

Finally you can create your `docker-compose.override.yml` file with your own settings


