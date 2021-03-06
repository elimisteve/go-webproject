Go-WebProject
=============

Go-webproject is an opensource web application framework written in The Go Programming Language.

It is not a Go package that you can import elsewhere. It is completely standalone application which 
consists of a native, high performant web server and surrounding framework for application code. 
It is designed to be very easy to start coding with, but still easily extensible, with its flexible modular design. 
Project is actively maintained and it compiles with Go.1 release.


### Features

* html/template package from standard go library is used, for consistency and security reasons.
* template caching is in place.
* (optional) on the fly template reloading without need to restart the service.
* (optional) integrated mux package from gorilla project for advanced routing and easier request handling.
* integrated sessions package from gorilla project for session management.
* extensions through 3rd party modules
* external configuration file for server and app settings.


### References

* Check out http://go-webproject.appspot.com/ for more documentation.
* Check out http://gorilla-web.appspot.com/pkg/gorilla/mux/ for documentation on mux routing API.

### Notes

* When live-templates feature is used, due to current bug in exp/inotify package, when template file is being Watch()ed, if it gets removed and 
replaced with another file of same name, updates to the new file are not tracked. I expect this to be resolved in future.


Installation
------------

### Step 1

* `$ git clone git://github.com/scyth/go-webproject.git`
* `$ cd go-webproject`


### Step 2

Copy the configuration file from examples/config/server.conf to config/server.conf and make appropriate changes for your environment.


### Step 3

Copy sample templates from example/templates/ to your templatePath directory you previously defined.


### Step 4

Start programming your handlers! Copy examples/handlers/handlers.go to src/, edit src/handlers.go and write some stuff based on examples provided.


### Step 5

Compile and run the server, asuming your current working directory is still project root

* `$ make`
* `$ ./runserver -config=config/server.conf`

Open up your browser and see if your code works as expected.


### Step 6 - keeping up with the updates

Go-webproject is distributed via github as a single project, consisting of internal packages and source files to build the final executable. However, Go.v1 introduced 
a go command utility for building and installing packages and executables, and now it's not enough just to `git pull` to start fresh. To make the whole thing more convenient, 
you can run:

* `$ git pull`  - this will get you latest code for building the executable.
* `$ make sync` - this will download the latest code for all the packages and will put it in your $GOPATH.
* `$ make`      - will reinstall all the packages, and will rebuild the executable.


Writing 3rd party modules
-------------------------

See: http://go-webproject.appspot.com/pkg/gwp/gwp_module.html
