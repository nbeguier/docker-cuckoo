![cuckoo-logo](https://raw.githubusercontent.com/blacktop/docker-cuckoo/master/docs/img/logo.png) Dockerfile
=========================================================================================================

[![CircleCI](https://circleci.com/gh/blacktop/docker-cuckoo.png?style=shield)](https://circleci.com/gh/blacktop/docker-cuckoo) [![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org) [![Docker Stars](https://img.shields.io/docker/stars/blacktop/cuckoo.svg)](https://hub.docker.com/r/blacktop/cuckoo/) [![Docker Pulls](https://img.shields.io/docker/pulls/blacktop/cuckoo.svg)](https://hub.docker.com/r/blacktop/cuckoo/) [![Docker Image](https://img.shields.io/badge/docker image-174.8 MB-blue.svg)](https://hub.docker.com/r/blacktop/bro/)

This repository contains a **Dockerfile** of [Cuckoo Sandbox](http://www.cuckoosandbox.org/).

**Table of Contents**

-	[cuckoo Dockerfile](#-dockerfile)
	-	[Dependencies](#dependencies)
	-	[Image Tags](#image-tags)
	-	[Installation](#installation)
	-	[To Run on OSX](#to-run-on-osx)
	-	[Getting Started](#getting-started)
	-	[Documentation](#documentation)
		-	[Usage](#usage)
		-	[Tips and Tricks](#tips-and-tricks)
	-	[Issues](#issues)
	-	[Credits](#credits)
	-	[Todo](#todo)
	-	[License](#license)

### Dependencies

-	[blacktop/yara:3.4](https://hub.docker.com/r/blacktop/yara/)
-	[blacktop/volatility:2.5](https://hub.docker.com/r/blacktop/volatility/)

### Image Tags

```bash
REPOSITORY             TAG                 VIRTUAL SIZE
blacktop/cuckoo        latest              366 MB
blacktop/cuckoo        alpine              267 MB
blacktop/cuckoo        2.0                 334 MB
blacktop/cuckoo        1.2                 445 MB
```

> **latest** and **alpine** TAG contain all of cuckoosandbox/community

### Installation

1.	Install [Docker](https://docs.docker.com).
2.	Install [docker-compose](https://docs.docker.com/compose/install/)
3.	Download [trusted build](https://hub.docker.com/r/blacktop/cuckoo/) from public [Docker Registry](https://hub.docker.com/): `docker pull blacktop/cuckoo`

### To Run on OSX

-	Install [Homebrew](http://brew.sh)

```bash
$ brew tap caskroom/cask
$ brew cask install virtualbox
$ brew install docker
$ brew install docker-machine
$ docker-machine create --driver virtualbox default
$ eval $(docker-machine env)
```

### Getting Started

```bash
$ curl -sL https://raw.githubusercontent.com/blacktop/docker-cuckoo/master/docker-compose.yml > docker-compose.yml
$ docker-compose up -d
```

Now navigate to `$(docker-machine ip)`

### Documentation

#### Usage

> If you want to customize the cuckoo configuration before launching you can link the **conf** folder into the container like so:

```bash
$ docker run -d --name mongo mongo
$ docker run -d -v $(pwd)/conf:/cuckoo/conf:ro --link mongo -p 80:80 blacktop/cuckoo
```

Open a web browser and navigate to :

```bash
$(docker-machine ip)
```

![cuckoo-submit](https://raw.githubusercontent.com/blacktop/docker-cuckoo/master/docs/img/submit.png)

#### Tips and Tricks

As a convenience you can add the **docker-machine** IP to your **/etc/hosts** file:

```bash
$ echo $(docker-machine ip) dockerhost | sudo tee -a /etc/hosts
```

Now you can navigate to [http://dockerhost](http://dockerhost) from your host

![cuckoo-dashboard](https://raw.githubusercontent.com/blacktop/docker-cuckoo/master/docs/img/dashboard.png)

### Issues

Find a bug? Want more features? Find something missing in the documentation? Let me know! Please don't hesitate to [file an issue](https://github.com/blacktop/docker-cuckoo/issues/new) and I'll get right on it.

> NOTE: I am now using the precompiled bro package to decrease the docker image size, if that caused a loss in functionality you depend on please let me know.

### Credits

### Todo

-	[x] Install/Run Cuckoo Sandbox
-	[x] Break mongo out into a separate container using docker-compose
-	[x] Fix blacktop/yara and blacktop/volatility so I can use them as a base images for this image
-	[ ] Create docker-entryporint.sh to use same container as daemon or web app or api or utility, etc
-	[ ] Figure out how to link to a analysis Windows VM (would be great if it was running in another container)

### License

MIT Copyright (c) 2015-2016 **blacktop**
