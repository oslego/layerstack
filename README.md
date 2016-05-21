# LayerStack

Small JavaScript library that splits an element's multiple backgrounds into separate layers (DOM elements) so that each layer corresponds to one of the original element's backgrounds.

Visualize in 3D.

See an example in `demo.html`.

## Usage

Include both `layerstack.js` and `layerstack.css` into the page, then create an instance of LayerStack with a reference to the DOM element that you want to inspect.

```html
<link href="layerstack.css" rel="stylesheet">
<script src="layerstack.js"></script>
<script>
  var element = document.querySelector('.demo');
  var stack = LayerStack(element);
</script>
```

Move the mouse cursor to expand the layer and rotate stack.

## API

**Work in progress. This is just a prototype.**

### Methods
- `.destroy()`

  Removes all the LayerStack DOM nodes and utility stylesheets from the page. Restores visibility of the original element.

  **Example**
  ```javascript
  stack.destroy();
  ```

  You can pass an optional object literal with options for the destroy action. Possible values:

  ```javascript
  options: {
    immediate: {Boolean} // if true, remove everything ASAP without running animation. Default is false.
  }
  ```

  **Example**
  ```javascript
  stack.destroy({ immediate: true });
  ```

- `.on()`

  Add an event listener for an event triggered by the LayerStack instance. Expects two parameters: an event name as a string and a function to be called after the event triggers.

  ```javascript
  stack.on('afterdestroy', function() {
    /* called after everything has been destroyed */
  })
  ```

### Events

- "afterdestroy"

  Event called after the effects of the `destroy()` method have taken place. Use to invalidate reference to LayerStack instance itself when you want to reuse it again the same page context.

  **Example**
  ```javascript
  stack.on('afterdestroy', function() {
    // invalidate LayerStack reference
    stack = undefined;
  })
  stack.destroy();
  ```
