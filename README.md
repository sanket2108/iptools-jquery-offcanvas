# iptools-jquery-offcanvas [![Build Status](https://api.travis-ci.org/interactive-pioneers/iptools-jquery-offcanvas.svg)](https://travis-ci.org/interactive-pioneers/iptools-jquery-offcanvas) [![Bower version](https://badge.fury.io/bo/iptools-jquery-offcanvas.svg)](http://badge.fury.io/bo/iptools-jquery-offcanvas)

Simple CSS3 animated offcanvas.

## Related

- [native js version](https://github.com/interactive-pioneers/iptools-offcanvas)

## Features

- Displays content inside an offcanvas from the top, right, bottom or left.
- Multiple instances at once.
- Static, instance is open on page load.
- CSS3 transitions and animations.

## Options

All options are optional.

Name                   | type       | default value                 | values                                     | description
:----------------------|:-----------|:------------------------------|:-------------------------------------------|:-----------------------------------
`baseClass`            | `string`   | `offcanvas`                   | valid css class string                     | base css class
`type`                 | `string`   | `left`                        | `top`, `right`, `bottom`, `left`           | canvas position
`single`               | `boolean`  | `true`                        |                                            | single mode, closes all other canvases
`closeOnClickOutside`  | `boolean`  | `false`                       |                                            | close canvas on click outside
`static`               | `boolean`  | `false`                       |                                            | open after initialization
`staticCloseCondition` | `function` | `function() { return true; }` | a function returning either true or false  | close condition for static canvas

## Methods

Method        | Parameter | Return    | Description
:-------------|:----------|:----------|:-----------
`getSettings` |           | `object`  | retrieve settings
`isActive`    |           | `boolean` | returns if canvas is active (open)
`toggle`      | `boolean` |           | not required. open (true), close (false) or toggle (leave empty)
`destroy`     |           |           | destroy offcanvas

## Events

Event pattern: `{eventName}.{elementId}@iptOffCanvas`

Event                             | Element        | Description
:---------------------------------|:---------------|:-----------
`initialized.custom@iptOffCanvas` | this.$element  | Emitted when canvas is ready to use.
`opened.custom@iptOffCanvas`      | this.$element  | Emitted when the canvas opens.
`closed.custom@iptOffCanvas`      | this.$element  | Emitted when the canvas closes.

## Requirements

- jQuery >=1.11.3 <4

## Example

```html
<button data-offcanvas-open="custom">open</button>
<button data-offcanvas-close="custom">close</button>
<button data-offcanvas-toggle="custom">toggle</button>

<section id="custom" class="offcanvas" style="padding:50px;background-color:rgba(0,0,0,0.5);">
  <p>content</p>
  <button data-offcanvas-close="custom">X</button>
</section>

<link rel="stylesheet" href="dist/iptools-jquery-offcanvas.css" type="text/css">
<script src="dist/iptools-jquery-offcanvas.min.js"></script>
<script type="text/javascript">
  $(document).ready(function() {

    // bind
    $('#custom').iptOffCanvas({
      baseClass: 'offcanvas',
      closeOnClickOutside: false,
      single: true,
      static: false,
      staticCloseCondition: function() { return true; },
      type: 'right'
    });

    // retrieve settings
    var settings = $('#custom').data(pluginName).getSettings();

    // check if active (open)
    var isActive = $('#custom').data(pluginName).isActive();

    // open, close or toggle
    $('#custom').data(pluginName).toggle(true); // true for open, false to close, leave empty to toggle

    // destroy canvas
    $('#custom').data(pluginName).destroy();

    // example event listener
    $('#custom').on('iptOffCanvas.opened', function() {
      console.log('canvas opened');
    });

  });
</script>
```

http://www.jqueryscript.net/menu/Minimal-Overlaying-Off-canvas-Plugin-With-jQuery-Iptools-Offcanvas.html

## Contributions

### Bug reports, suggestions

- File all your issues, feature requests [here](https://github.com/interactive-pioneers/iptools-jquery-offcanvas/issues)
- If filing a bug report, follow the convention of _Steps to reproduce_ / _What happens?_ / _What should happen?_
- __If you're a developer, write a failing test instead of a bug report__ and send a Pull Request

### Code

1. Fork it ( https://github.com/[my-github-username]/iptools-jquery-offcanvas/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Install dependencies (`npm i`)
4. Develop your feature by concepts of [TDD](http://en.wikipedia.org/wiki/Test-driven_development), see [Tips](#tips)
5. Commit your changes (`git commit -am 'Add some feature'`)
6. Push to the branch (`git push origin my-new-feature`)
7. Create a new Pull Request

### Tips

Following tasks are there to help with development:

- `grunt watch` listens to source, live reloads browser
- `grunt qa` run QA task that includes tests and JSHint
- `grunt build` minify source to dist/

## Licence

Copyright © 2015 Interactive Pioneers GmbH. Licenced under [GPLv3](LICENSE).
