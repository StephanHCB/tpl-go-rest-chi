# tpl-go-rest-chi

A template for scaffolding a go microservice using the [chi](https://github.com/go-chi/chi) framework.

Uses [go-generator-lib](https://github.com/StephanHCB/go-generator-lib) for templating, command line
interface is [go-generator-cli](https://github.com/StephanHCB/go-generator-cli)

## First time preparations

We are assuming that you have cloned this repository in the current directory, but you are NOT inside it:

```
BASEDIR=$(pwd)
git clone https://github.com/StephanHCB/tpl-go-rest-chi.git
```

Outside of this repository, clone [go-generator-cli](https://github.com/StephanHCB/go-generator-cli), 
and build the generator command line program:

```
cd $BASEDIR
git clone https://github.com/StephanHCB/go-generator-cli.git
cd go-generator-cli
go build main.go args.go
mv -f main ../generator
mv -f main.exe ../generator.exe
cd ..
```

Now you have a binary called generator (or generator.exe) in your BASEDIR.

## Preparing for a new service

Create an empty directory named after the service you wish to create, let's say `example-rendered-service`.
Then ask the generator to write a render spec file with all variables set to their defaults:

```
cd $BASEDIR
mkdir example-rendered-service
./generator --generator=tpl-go-rest-chi --target=example-rendered-service --create
```

This will create a file called `generated-main.yaml` filled with defaults for some variables.

Edit it in your favourite text editor to adapt the service name and the github url 
(or wherever you'd like go to clone it from).

Now would be a good time to enter the service directory, do a git init, 
and commit the render spec.

## Rendering the service

```
cd $BASEDIR
./generator --generator=tpl-go-rest-chi --target=example-rendered-service --render
``` 

Now would be a good time to enter the service directory, and commit all the generated files to git.
This way you will be able to see differences when re-generating.
