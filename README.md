# ocdev
[![Build Status](https://travis-ci.org/redhat-developer/ocdev.svg?branch=master)](https://travis-ci.org/redhat-developer/ocdev) [![codecov](https://codecov.io/gh/redhat-developer/ocdev/branch/master/graph/badge.svg)](https://codecov.io/gh/redhat-developer/ocdev)

## What is ocdev?
OpenShift Command line for Developers

## Pre-requisites
- OpenShift version 3.7.0 and up

To use ocdev you need access to an OpenShift instance and have OpenShift CLI installed on your local machine (`oc` should be in your $PATH).

### OpenShift instance
You can use [Minishift](https://docs.openshift.org/latest/minishift/index.html) to get a local instance of OpenShift. However ocdev can be used with any instance of OpenShift.

### OpenShift CLI
There are different ways to install OpenShift CLI. 
Please follow [OpenShift documentation](https://docs.openshift.org/latest/cli_reference/get_started_cli.html#installing-the-cli).

## Installation
To install `ocdev` on your system, you cat use the fully automated [install.sh](./scripts/install.sh) script.
This script will enable ocdev repository on your system and install ocdev using package manager depending on your system.
Supported systems are Debian, Ubuntu, Fedora, CentOS and macOS. You can find more information about package repositories in 
[Advanced installation guide](./docs/advanced-installation-guide.md)

```
curl -L https://github.com/redhat-developer/ocdev/raw/master/scripts/install.sh | bash
```


If you don't want to add extra package repositories to your system you can just extract  `ocdev` binary from [GitHub releases page](https://github.com/redhat-developer/ocdev/releases) to one of the directories that are in your `$PATH`.

For macOS:

```
sudo curl -L  "https://github.com/redhat-developer/ocdev/releases/download/v0.0.2/ocdev-darwin-amd64.gz" | gzip -d > /usr/local/bin/ocdev; chmod +x /usr/local/bin/ocdev
```

For Linux:
```
sudo curl -L  "https://github.com/redhat-developer/ocdev/releases/download/v0.0.2/ocdev-linux-amd64.gz" | gzip -d > /usr/local/bin/ocdev; chmod +x /usr/local/bin/ocdev
```

You can also download latest master builds from [Bintray](https://dl.bintray.com/ocdev/ocdev/latest/). This is updated every time there is a change in master git branch.



## Concepts
- An **_application_** is, well, your application! It consists of multiple microservices or components, that work individually to build the entire application.
- A **_component_** can be thought of as a microservice. Multiple components will make up an application. A component will have different attributes like storage, etc.
Multiple component types are currently supported, like nodejs, perl, php, python, ruby, etc.

## Getting Started
Developing applications using ocdev is as simple as -
- `ocdev application create <name>`
- `ocdev component create <name>`
- `ocdev component push`

Check out our [Getting Started](docs/getting-started.md) guide and get going!

## CLI Structure
```
ocdev --verbose : OpenShift CLI for Developers                 
    application --short : application                          
        create : create an application                         
        delete --force : delete the given application          
        get --short : get the active application               
        list : lists all the applications                      
        set : Set application as active.                       
    catalog : Catalog related operations                       
        list : List all available component types.             
        search : Search component type in catalog              
    completion : Output shell completion code                  
    component --short : Components of application.             
        create --binary --git --local : Create new component   
        delete --force : Delete existing component             
        get --short : Get currently active component           
        list : List all component in current application       
        set : Set active component.                            
    create --binary --git --local : Create new component       
    list : List all component in current application           
    project --short : project  
        create : create a new project                          
        get --short : get the active project                   
        set --short : set the current active project           
    push --local : Push source code to component               
    storage --component : storage                              
        add --path --size : create storage and mount to component                                                              
        list : list storage attached to a component            
        remove : remove storage from component                 
    url : Expose component to the outside world                
        create : Create a URL for a component                  
        delete : Delete a URL  
        list --application --component : List URLs             
    version : Print the version of ocdev                       
```
*_autogenerated_
