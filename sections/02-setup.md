# let's get set up!

## development environment
Windows 10.

[Visual Studio Code](https://code.visualstudio.com) is a good, free, fast editor.
It uses a lot of ideas from Atom and Sublime Text.

[Git (for windows cli)](https://git-scm.com/downloads) is a version control system.
NodeCG depends on git, and we'll use it too.
Add it to `PATH` when it asks.

[NodeJS](https://nodejs.org) is a server that runs Javascript code.
We use the latest version.

[Yarn](https://yarnpkg.com) is a Javascript package manager.
This useful tool finds and installs libraries we depend on.
We use Yarn instead of `npm` which comes with NodeJS.

## NodeCG
Open a console window, we've got work to do.

```console
$ yarn global add bower
...
success Installed "bower@..." with binaries:
      - bower
Done in 12.34s.

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

Go to <http://localhost:9090> and be proud.
Your brand new NodeCG looks like this:

![Success!](assets/screencapture-localhost-9090-dashboard-2018-07-31-02_04_44.png)

Let's stop NodeCG now.
Go to the console and press `Ctrl+C` a few times.
This kills the NodeCG.
