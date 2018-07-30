Getting started with NodeCG can be overwhelming.
Here's my own quick guide to doing NodeCG stuff.

## layout of this guide
{:.no_toc}
* TOC
{:toc}

# let's get set up!
## our development environment
* windows 10 x64
* [visual studio code](https://code.visualstudio.com)
* [git for windows cli](https://git-scm.com/downloads) - add it to PATH when it asks
* [nodejs runtime](https://nodejs.org) latest version
* [yarn](https://yarnpkg.com), using the .msi installer

Visual Studio Code is a great, free, lightweight IDE inspired by the likes of Sublime and Atom.
Git is a version control system - NodeCG depends on git, but we'll use it ourselves too.
NodeJS is a server that runs Javascript code.
Yarn is a Javascript package manager, an alternative to the `npm` package manager that ships with NodeJS.

## NodeCG
Open a console window, we've got work to do.

```console
$ yarn global add nodecg-cli
...
success Installed "nodecg-cli@5.0.1" with binaries:
      - nodecg
Done in 13.46s.

$ mkdir nodecg && cd nodecg
D:\nodecg

$ nodecg setup
Finding latest release... done!
Cloning NodeCG... done!
Checking out version v1.1.2... done!
Installing production npm dependencies... done!
Installing production bower dependencies... done!
NodeCG (v1.1.2) installed to D:\nodecg

$ nodecg start
[nodecg] No config found, using defaults.
info: [nodecg/lib/server] Starting NodeCG 1.1.2 (Running on Node.js v9.11.1)
info: [nodecg/lib/server] NodeCG running on http://localhost:9090
```

Go to http://localhost:9090 and give yourself a little pat on the back.

# our first graphic

# our first dashboard

# our first extension
