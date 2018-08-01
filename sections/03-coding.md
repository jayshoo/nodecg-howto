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
