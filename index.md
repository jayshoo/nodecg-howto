Getting started with NodeCG can be overwhelming.
Here's my own quick guide to doing NodeCG stuff.

Questions, comments and changes are encouraged via GitHub issues and pull requests.

## layout of this guide
{:.no_toc}
* TOC
{:toc}



# NodeCG fundamentals

## architecture
- nodecg hosts 1 webserver
- nodecg hosts 1 dashboard
- nodecg hosts 0..n replicants
- nodecg hosts 0..n bundles
- bundles host 0..n graphics and panels
- bundles host 0..1 extensions
- graphics, panels, extensions consume NodeCG API

## bundles
A unit of user code.

## the dashboard (and its panels)
This is the web user interface of NodeCG.
Bundles have control panels.
The panels show up on the dashboard.
Each panel is a web page.

## graphics
Graphics go on stream.
They are a web page with a transparent background.
They are displayed by a Browser Source in the streaming software.

## extensions
Extensions are server code from bundles.
Usually this is code that must keep running for a while.
Maybe a connection to twitch chat?
Maybe an interface to a chess AI.

## replicants
Clever code-machines to share data around NodeCG.
If we put text in them from the dashboard, then that text is in the graphic!
And next time we run NodeCG it will load that text from disk.
But replicants can do so much more.



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



# now we code

## our first bundle
We need a folder for our bundle, and a `package.json` for it.

```console
$ cd bundles
D:\nodecg\bundles

$ mkdir toys && cd toys
D:\nodecg\bundles\toys

$ yarn init --yes
warning The yes flag has been set. This will automatically answer yes to all questions.
success Saved package.json
Done in 0.11s.
```

Now we add a `nodecg` section to `package.json`.
NodeCG looks at `compatibleRange` to see if it can run the bundle.
`^1.0.0` allows everything from `1.0.0` onwards...
but rejects everything from `2.0.0` onwards.
We would change this if we depend on a new feature in `1.1.0`.

```json
{
  "name": "toys",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "nodecg": {
    "compatibleRange": "^1.0.0"
  }
}
```

## our first graphic
Add a `nodecg.graphics` section to our bundle's `package.json`.
The `width` and `height` aren't strict, so don't worry.

```json
"nodecg": {
  "compatibleRange": "^1.0.0",
  "graphics": [
    {
      "file": "first.html",
      "width": 1920,
      "height": 1080
    }
  ]
}
```

We need to make `first.html`.
It goes in the `graphics` folder of our bundle.

```html
<!DOCTYPE html>

<h1>My First Graphic</h1>
<div id="value"></div>

<style>
</style>

<script>
  element = document.getElementById('value')
  replicant = nodecg.Replicant('first')
  
  replicant.on('change', newValue => {
    element.innerText = newValue
  })
</script>
```

## our first dashboard panel
Add a `nodecg.dashboardPanels` section to our bundle's `package.json`:

```json
"nodecg": {
  "dashboardPanels": [
    {
      "name": "first",
      "title": "My First Panel",
      "width": 4,
      "headerColor": "#ff9900",
      "file": "first.html"
    }
  ]
}
```

```html
<!DOCTYPE html>

<h1>My First Panel</h1>

<style>
</style>

<script>
</script>
```

## our first extension
This time we don't need to edit our `package.json`!
Just create an `extension` folder with `index.js` inside.

```js
module.exports = nodecg => {
}
```
