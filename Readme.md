- [Golang Course](#golang-course)
  - [Workstation setup](#workstation-setup)
    - [Optional: Windows for Linux subsystem](#optional-windows-for-linux-subsystem)
    - [Linux](#linux)
    - [VSCode](#vscode)
    - [Git](#git)
    - [Github](#github)
    - [Bash](#bash)
    - [Tools](#tools)
      - [asdf](#asdf)
      - [Just - the new make](#just---the-new-make)
    - [Docker](#docker)
    - [sqlite](#sqlite)
    - [Mariadb / Postgresql](#mariadb--postgresql)
  - [Basic SDLC](#basic-sdlc)
    - [Testing](#testing)
    - [CI/CD process](#cicd-process)
  - [Golang](#golang)
    - [Installation](#installation)
    - [Golang Basics](#golang-basics)
      - [Iterating](#iterating)
    - [Golang Concurency](#golang-concurency)
    - [Know your options](#know-your-options)
    - [Databases](#databases)
  - [Web development](#web-development)
    - [Microservices](#microservices)
    - [Ataching the frontend](#ataching-the-frontend)
    - [Sample frontend application](#sample-frontend-application)
  - [Packaging and deploy](#packaging-and-deploy)
  - [Building the CV](#building-the-cv)
  - [Coursed to watch](#coursed-to-watch)

# Golang Course

This is a skeleton map for the summer Golang course.
This roadmap is for a backend developer of microservices.
https://roadmap.sh/golang


## Workstation setup

### Optional: Windows for Linux subsystem

### Linux

- [ ] Enable the OS for Build packages and system libraries

For Ubuntu you will probably need those packages

    sudo apt install
              build-essential \
              zlib1g-dev \
              libbz2-dev \
              libssl-dev \
              libsqlite3-dev \
              sqlite \
              libffi-dev \
              libbson-dev \
              coreutils \
              curl -y



### VSCode

- [ ] Install VSCode
- [ ] Extensions
  - [ ] golang
  - [ ] github - GitLens
  - [ ] https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2

### Git

- [ ]

### Github

- [ ] Create an account in github.
- [ ] Upload avatar!

### Bash

- [ ] Have you read a book for bash?

  - http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html#ss5.1
  - http://www.tablespace.net/papers/shellsheet.html
  - https://github.com/denysdovhan/bash-handbook
  - https://github.com/dylanaraps/pure-bash-bible

Get a fancy prompt with a lot of information https://starship.rs/ 


### Tools

#### asdf

Install the manager

      apt install curl git
      git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.11.3
      . $HOME/.asdf/asdf.sh
      . $HOME/.asdf/completions/asdf.bash

List of plugins

- https://github.com/asdf-vm/asdf-plugins
- https://github.com/amrox/asdf-pyapp
- https://www.opensourceagenda.com/projects/asdf-plugins


Show the currently installed plugins

    asdf current


Set golang as a system/global command

    asdf global golang system


Recommended list of plugins


Nodejs

    asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git

    asdf list all nodejs
    asdf list all nodejs 18
    asdf install nodejs latest
    v17.3.0


Python

    asdf plugin-add python
    asdf list all python
    asdf install python 3.9.13
    asdf install python latest
    asdf local python 3.9.13

    echo "poetry" >> $HOME/.default-python-packages

direnv
This tool is used for managing the environment variables.

    asdf plugin-add direnv
    asdf install direnv latest
    asdf global direnv latest
    eval "$(direnv hook bash)"


golang

    asdf plugin-add golang https://github.com/kennyp/asdf-golang.git
    asdf install golang latest


Usage

On every project and folder that you want to enable some language/tool you create a .tool-versions file.
There you list all the dependencies.

Instead of manually creating the file you can do it with asdf

    asdf local golang latest

File: .tool-versions

    direnv 2.32.3
    golang 1.20.5



#### Just - the new make

Go and install the binary from here https://github.com/casey/just | https://github.com/ggilmore/asdf-just

Examples:

File: justfile

    default:
      @just --choose

    hello-world:
      echo "hi"

    clean-deploy:
      rm -rf tmp/

    sls-deploy region: clean-deploy
        #!/bin/bash
        echo "do we have dns? tf_live_rifiniti_production/us-east-1/route53/dns-records/rifiniti.com/software-development/"
        echo {{region}}
        cd ./clean-deploy
        sls deploy -s production -r {{region}}


    sls-deploy-all: (sls-deploy "us-east-1") (sls-deploy "eu-central-1")

Example usage:

    just sls-deploy us-east-1
    just sls-deploy-all

### Docker

  docker compose

### sqlite

### Mariadb / Postgresql



## Basic SDLC

### Testing

### CI/CD process

Use the github workers and actions
Linting, code quality

## Golang

### Installation

Install from the website
Install with asdf

### Golang Basics

language syntax, structs, "inheritance", composition

Great Course in [Bulgarian language](https://www.youtube.com/watch?v=z57WKerNe9w)
#### Iterating

Example for range

    items := int[]{1,2,3}
    for item := range(items):



Working with jsons

### Golang Concurency

Sample program to do something in parallel. Not the focus of this course.

### Know your options

multiplatform gui libs
game development

### Databases

Work with SQL - models
Work with ORM


## Web development

### Microservices
Simple microservice with own database with docker.

### Ataching the frontend

Choose the web framework

### Sample frontend application

## Packaging and deploy

capistrano ssh-something

## Building the CV

- Get the LinkedIn Skill badges for golang, github, microservices, linux.
- write great introduction letter (optionally use chatgpt)
- create a CV listing all projects

## Coursed to watch

Linux course
