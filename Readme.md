- [Golang Course](#golang-course)
  - [Workstation setup](#workstation-setup)
    - [Optional: Windows for Linux subsystem](#optional-windows-for-linux-subsystem)
    - [Linux](#linux)
    - [VSCode](#vscode)
    - [Git](#git)
    - [Github](#github)
    - [Bash](#bash)
      - [Fork bomb](#fork-bomb)
    - [Tools](#tools)
      - [asdf](#asdf)
      - [Just - the new make](#just---the-new-make)
    - [Docker](#docker)
    - [sqlite](#sqlite)
  - [Basic SDLC](#basic-sdlc)
    - [Testing](#testing)
    - [CI/CD process](#cicd-process)
  - [Golang](#golang)
    - [Installation](#installation)
    - [Golang Basics](#golang-basics)
      - [Iterating](#iterating)
      - [Working with structs](#working-with-structs)
      - [Interfaces](#interfaces)
      - [Working with json \& files](#working-with-json--files)
      - [Build a blockchain app](#build-a-blockchain-app)
    - [Golang Concurency](#golang-concurency)
      - [Simple](#simple)
      - [Practical Concurency](#practical-concurency)
      - [BDD](#bdd)
    - [Containers](#containers)
      - [Postgresql](#postgresql)
  - [Web development](#web-development)
    - [Expore GIN](#expore-gin)
    - [Learn SQL](#learn-sql)
    - [Learn about Forms](#learn-about-forms)
    - [Databases](#databases)
      - [Postgresql](#postgresql-1)
    - [Microservices](#microservices)
    - [Ataching the frontend](#ataching-the-frontend)
    - [Know your options](#know-your-options)
    - [Sample frontend application](#sample-frontend-application)
  - [Packaging and deploy](#packaging-and-deploy)
  - [Building the CV](#building-the-cv)
  - [Resources: Coursed to watch \& Books to Read](#resources-coursed-to-watch--books-to-read)

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

#### Fork bomb

With this code you can test later the cgroups in docker by limiting the maximum number of processes for a given container. The example is from the "Containers From Scratch • Liz Rice • GOTO 2018"

    :(){ :|:& };:

Explanation:

    : defines a shell function called : (colon).
    (){ ... } is the function definition syntax in Bash.
    : calls the function recursively.
    | pipes the output of the function (which is itself) to another invocation of the function.
    & runs the function in the background.
    ; separates commands, and : at the end is the final invocation of the function to start the fork bomb.

When you run this code, it creates an ever-increasing number of processes, leading to a system freeze if not stopped.

Important Note: Fork bombs are dangerous and can potentially crash your system or make it unresponsive. They should only be used for educational purposes in a controlled environment and never in a real-world scenario or on a production system. Running such code on a live system can cause data loss and disrupt other users' activities. Always use caution and test code like this in isolated environments.


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

Install docker from the docker official website. Install both  docker and docker compose.
Make sure you add your user into the docker group.

    groups

if you don't see the docker at your own groups, reboot the machine.

### sqlite


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

Create a function called "removeDuplicates" that takes a slice of integers as input and returns a new slice with duplicate values removed. The order of the elements in the resulting slice should be maintained.

Example Output:
Input: [1 2 2 3 4 4 4 5]
Output: [1 2 3 4 5]

Create a function called "countOccurrences" that takes a slice of strings as input and returns a map where the keys are the unique strings from the slice, and the values are the number of occurrences of each string in the slice.

Input: ["apple" "banana" "apple" "orange" "banana" "banana"]
Output: map[apple:2 banana:3 orange:1]

Create a function called "mergeMaps" that takes two maps with string keys and integer values as input and returns a new map that contains the combined key-value pairs from both input maps. If a key exists in both input maps, the value in the resulting map should be the sum of the corresponding values from the input maps.

Input Map 1: map[apple:2 banana:3]
Input Map 2: map[banana:4 orange:1]
Output: map[apple:2 banana:7 orange:1]

Write a main function that demonstrates the usage of the above functions. Create sample input data and call each function with appropriate arguments. Print the results to the console.

Each function should have also unit tests.

#### Working with structs

Define a struct type called "Rectangle" to represent a rectangle. The struct should have the following fields:

- Width (float64): representing the width of the rectangle.
- Height (float64): representing the height of the rectangle.

Create a method called "Area" for the Rectangle struct that calculates and returns the area of the rectangle.

Create a method called "Perimeter" for the Rectangle struct that calculates and returns the perimeter of the rectangle.

Define a struct type called "Circle" to represent a circle. The struct should have the following fields:
    Radius (float64): representing the radius of the circle.

Create a method called "Area" for the Circle struct that calculates and returns the area of the circle.

Create a method called "Circumference" for the Circle struct that calculates and returns the circumference of the circle.

Write a main function that demonstrates the usage of the Rectangle and Circle structs. Create instances of both structs, initialize their fields with appropriate values, and call the "Area" and "Perimeter" methods for the Rectangle struct and the "Area" and "Circumference" methods for the Circle struct. Print the results to the console.

Note:

Use the built-in "math" package for mathematical calculations.
The formula for calculating the area of a rectangle is: area = width * height.
The formula for calculating the perimeter of a rectangle is: perimeter = 2 * (width + height).
The formula for calculating the area of a circle is: area = π * radius^2.
The formula for calculating the circumference of a circle is: circumference = 2 * π * radius.
You can assume the value of π to be 3.14159.

Example Output:
Rectangle
Width: 5.0
Height: 3.0
Area: 15.0
Perimeter: 16.0

Circle
Radius: 2.5
Area: 19.6349375
Circumference: 15.70796


#### Interfaces

Define an interface called "Shape" with the following methods:

- Area() float64: returns the area of the shape.
- Perimeter() float64: returns the perimeter of the shape.

Create two struct types, "Rectangle" and "Circle," that implement the "Shape" interface.

Implement the "Area" and "Perimeter" methods for the Rectangle struct based on its width and height.

Implement the "Area" and "Perimeter" methods for the Circle struct based on its radius.

Write a function called "PrintShapeDetails" that takes a Shape interface as input and prints the area and perimeter of the shape.

Write a main function that demonstrates the usage of the "Shape" interface and the "PrintShapeDetails" function. Create instances of both Rectangle and Circle, and pass them to the "PrintShapeDetails" function. Ensure that the function correctly prints the area and perimeter of each shape.

Example Output:
Rectangle
Width: 5.0
Height: 3.0
Area: 15.0
Perimeter: 16.0

Circle
Radius: 2.5
Area: 19.6349375
Circumference: 15.70796


#### Working with json & files

Define a struct called "Person" with the following fields:

- Name (string): representing the person's name.
- Age (int): representing the person's age.
- Email (string): representing the person's email address.

Create a function called "encodeJSON" that takes a Person struct as input and returns the JSON representation of the struct as a byte slice.

Create a function called "decodeJSON" that takes a byte slice (containing JSON data) as input and returns a Person struct.

Write a main function that demonstrates the usage of the "encodeJSON" and "decodeJSON" functions. Create an instance of the Person struct, encode it to JSON, and then decode it back to a struct. Print the decoded struct's fields to the console.

Example:
(Output)
{Name: "John Doe", Age: 25, Email: "johndoe@example.com"}

Decoded Person struct:
Name: John Doe
Age: 25
Email: johndoe@example.com


#### Build a blockchain app

The blockchain specification is encoded in a bitcoin transaction - check [here](https://jsfiddle.net/yjdzg37s/)

Building Blockchain in Go

- [Part 1: Basic Prototype](https://jeiwan.net/posts/building-blockchain-in-go-part-1/)
- [Part 2: Proof of Work](https://jeiwan.net/posts/building-blockchain-in-go-part-2/)
- [Part 3: Persistence and CLI](https://jeiwan.net/posts/building-blockchain-in-go-part-3/)
- [Part 4: Transactions 1](https://jeiwan.net/posts/building-blockchain-in-go-part-4/)
- [Part 5: Address](https://jeiwan.net/posts/building-blockchain-in-go-part-5/)
- [Part 6: Transactions 2](https://jeiwan.net/posts/building-blockchain-in-go-part-6/)
- [Part 7: Network](https://jeiwan.net/posts/building-blockchain-in-go-part-7/)


### Golang Concurency

Sample program to do something in parallel. Not the focus of this course.

#### Simple

Create a function called "printMessage" that takes a string as input and prints it to the console.

In the main function, create a goroutine that invokes the "printMessage" function with the argument "Hello, World!".

After starting the goroutine, print the message "Goroutine started!" to the console from the main function.

Use a delay or wait mechanism to ensure that the goroutine has enough time to execute before the main function terminates.

Verify that the output displays "Goroutine started!" before the message "Hello, World!".

Example Output:
Goroutine started!
Hello, World!

#### Practical Concurency

Define a function called "processFile" that takes a filename (string) as input and simulates some processing on the file. For this example, you can simply print the filename and a message indicating that processing is being done.

In the main function, create a slice of filenames (at least 5 filenames) that represent files to be processed concurrently.

Use a loop to iterate through the slice of filenames.

For each filename, launch a goroutine that calls the "processFile" function with the respective filename as an argument.

Use a delay or wait mechanism (such as time.Sleep()) to ensure that all goroutines have enough time to complete their processing before the main function terminates.

Example Output:
Assuming the filenames in the slice are ["file1.txt", "file2.txt", "file3.txt", "file4.txt", "file5.txt"], the output could be:

Processing file: file1.txt
Processing file: file2.txt
Processing file: file3.txt
Processing file: file4.txt
Processing file: file5.txt

Note:

You can modify the "processFile" function to include more meaningful processing, such as reading the contents of the file, performing calculations, or any other desired operations.
The actual execution order and interleaving of the messages may vary due to the concurrent nature of goroutines.



#### BDD
Explain BDD, difference between TDD and BDD

Try godog

https://semaphoreci.com/community/tutorials/how-to-use-godog-for-behavior-driven-development-in-go

Make it working in Github Actions - your CI/CD server.

From now on, put your projects in CI/CD

### Containers

Explain cgroups, containers, images and image repositories.

[Tutorial for docker containers](https://www.youtube.com/watch?v=RqTEHSBrYFw)
[Build containers from go](https://www.youtube.com/watch?v=8fi7uSYlOdc)

Run the one of our previous projects into docker
Run the  of our previous projects into docker



#### Postgresql

We will run postgres from a containers.

https://hub.docker.com/_/postgres



## Web development


Show developer tools

Learn DNS - https://tryhackme.com/room/dnsindetail
Learn HTTP - https://tryhackme.com/room/httpindetail
Content Discovery - https://tryhackme.com/room/contentdiscovery

Explain OSI model - https://www.imperva.com/learn/application-security/osi-model/


### Expore GIN

REST Servers in Go

- [Part 1 - standard library](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-1-standard-library/)
- [Part 2 - using a router package](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-2-using-a-router-package/)
- [Part 3 - using a web framework](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-3-using-a-web-framework/)
- [Part 4 - using OpenAPI and Swagger](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-4-using-openapi-and-swagger/)
Learn how to generate code via OpenAPI
- [Part 5 - middleware](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-5-middleware/)
- [Part 6 - authentication](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-6-authentication/)
- Optional: [Part 7 - GraphQL](https://eli.thegreenplace.net/2021/rest-servers-in-go-part-7-graphql/)


### Learn SQL

[SQL in 100 seconds](https://www.youtube.com/watch?v=zsjvFFKOm3c)

What is database and schema.
Classic SQL - CRUD
[Modern SQL](https://modern-sql.com/)
Database design,  [normalization forms](https://www.guru99.com/database-normalization.html)

You should know how grouping work and doing aggregations.
You should know the difference between [joins](https://sqlbolt.com/lesson/select_queries_with_joins), outer/left/inner/...and...there is one more new :)

You could be asked to iterate recursevly on SQL https://learnsql.com/blog/do-it-in-sql-recursive-tree-traversal/

### Learn about Forms

Build Web Application with Golang

https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/

Take the parts for working with forms

  https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/04.0.html
  https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/04.1.html

  Try SQLIte - https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/05.3.html

### Databases

#### Postgresql

Start the postgres server from the docker conatiner and do

Work with SQL - models:

  https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/05.4.html


Work with ORM

  https://astaxie.gitbooks.io/build-web-application-with-golang/content/en/05.5.html


### Microservices

Simple microservice with own database with docker.

### Ataching the frontend

Choose the web framework

https://github.com/astaxie/beego


### Know your options

multiplatform gui libs
game development


### Sample frontend application

## Packaging and deploy

capistrano ssh-something

## Building the CV

- Get the LinkedIn Skill badges for golang, github, microservices, linux.
- write great introduction letter (optionally use chatgpt)
- create a CV listing all projects

## Resources: Coursed to watch & Books to Read

Easy to read: Head First Design Patterns or the original "Design Patterns: Elements of Reusable Object-Oriented"
Linux course

Learn security https://tryhackme.com/dashboard

[Learn Projects by example](https://github.com/practical-tutorials/project-based-learning#go)
