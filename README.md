# `node-java-chrome-e2e`

> Docker Image with Node.js, Java and Google Chrome for automated e2e testing

This Docker image is created to easily execute automated end-to-end tests with Selenium in a container or in your CI pipeline.

It has Node.js, NPM, Java and Google Chrome installed:

```
$ docker run -it minddocdev/node-java-chrome-e2e
root@c0ff3e:/# node --version
v10.15.3
root@c0ff3e:/# npm --version
6.4.1
root@c0ff3e:/# java -version
openjdk version "1.8.0_171"
OpenJDK Runtime Environment (build 1.8.0_171-8u171-b11-1~bpo8+1-b11)
OpenJDK 64-Bit Server VM (build 25.171-b11, mixed mode)
root@c0ff3e:/# google-chrome --version
Google Chrome 73.0.3683.86
```

[![Build Status on the master branch](https://travis-ci.org/minddocdev/node-java-chrome-e2e.svg?branch=master)](https://travis-ci.org/minddocdev/node-java-chrome-e2e)

## Docker Hub

### `docker pull`

You can pull the image from Docker Hub using the `docker pull minddocdev/node-java-chrome-e2e` command. We are using [automated build set up](https://docs.docker.com/docker-hub/builds/#create-an-automated-build).

```
docker pull minddocdev/node-java-chrome-e2e
```

### `docker run`

To jump into the container's `bash` shell, run `docker run -it minddocdev/node-java-chrome-e2e`.

If you want to load a volume, you can execute:

```
$ docker run --rm --workdir /app --volume "$PWD:/app" --interactive --tty minddocdev/node-java-chrome-e2e /bin/bash
## Or using shorthand flags
$ docker run -w /app -v "$PWD:/app" -it minddocdev/node-java-chrome-e2e /bin/bash
## Install dependencies and run tests with npm
root@c0ff3e:/app# npm i && npm t
```

It's also likely that you don't want to jump into `bash`, because you understand already how things work and you just want to execute your e2e test suite.

To run the tests using one npm script (for example, if you have `npm install` in your `pretest` script), run:

```
docker run --rm -w /app -v "$PWD:/app" -t minddocdev/node-java-chrome-e2e npm test
```

If your end-to-end test suite requires multiple commands being executed, you should use:

```
docker run --rm -v "$PWD:/app" -t node-java-chrome-e2e /bin/bash -c "npm install && npm test && echo 'Yuppiee'"
```

### `docker build`

You can also build the image yourself. Checkout the repository

```
$ git clone https://github.com/mind-doc/node-java-chrome-e2e.git
$ cd node-java-chrome-e2e
$ docker build -t node-java-chrome-e2e .
$ docker images node-java-chrome-e2e
```

# Links

* [Docker Hub `minddocdev/node-java-chrome-e2e`](https://hub.docker.com/r/minddocdev/node-java-chrome-e2e/)
* [GitHub `mind-doc/node-java-chrome-e2e`](https://github.com/minddocdev/node-java-chrome-e2e)
* [Travis CI](https://travis-ci.org/minddocdev/node-java-chrome-e2e)
