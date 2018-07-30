Getting started with NodeCG can be overwhelming.
Here's my own quick guide to doing NodeCG stuff.

Questions, comments, additions are welcome on github as issues and pull requests.

## layout of this guide
{:.no_toc}
* TOC
{:toc}



# let's get set up!

## development environment
* windows 10 x64
* [visual studio code](https://code.visualstudio.com)
* [git for windows cli](https://git-scm.com/downloads) - add it to PATH when it asks
* [nodejs runtime](https://nodejs.org) latest version
* [yarn](https://yarnpkg.com), using the .msi installer

Visual Studio Code is a great, free, lightweight IDE inspired by the likes of Sublime and Atom.
Git is a version control system - NodeCG depends on git, and we'll use it too.
NodeJS is a server that runs Javascript code.
Yarn is a Javascript package manager, an alternative to the `npm` package manager that ships with NodeJS.

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

Go to <http://localhost:9090> and give yourself a little pat on the back.
A successful fresh installation looks like this:

![Success!](assets/screencapture-localhost-9090-dashboard-2018-07-31-02_04_44.png)

Let's stop NodeCG.
Go back to the console and press `Ctrl+C` a few times.
This kills the NodeCG.



# now we code

## our first bundle
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

## our first graphic
Add a `nodecg.graphics` section to our bundle's `package.json`:

```json
"nodecg": {
  "graphics": [
    {
      "file": "first.html",
      "width": 1920,
      "height": 1080
    }
  ]
}
```

```html
<!DOCTYPE html>

<h1>My First Graphic</h1>

<style>
</style>

<script>
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

