# Bootstrap 4 Toggle

**Bootstrap 4 Toggle** is a bootstrap plugin/widget that converts checkboxes into toggles.
This is a fork from [gitbrent/bootstrap4-toggle](https://github.com/gitbrent/bootstrap4-toggle) with support for jQuery 3.5 without using deprecated features.


# Usage

## Initialize With HTML
Simply add `data-toggle="toggle"` to automatically convert a plain checkbox into a bootstrap 4 toggle.

```html
<input id="chkToggle" type="checkbox" data-toggle="toggle">
```

## Initialize With Code
Toggles can also be initialized via JavaScript code.  

EX: Initialize id `chkToggle` with a single line of JavaScript.
```html
<input id="chkToggle" type="checkbox" checked>
<script>
  $(function(){
    $('#chkToggle').bootstrapToggle();
  });
</script>
```

# API

## Options
* Options can be passed via data attributes or JavaScript
* For data attributes, append the option name to `data-` (ex: `data-on="Enabled"`)

```html
<input type="checkbox" data-toggle="toggle" data-on="Enabled" data-off="Disabled">
<input type="checkbox" id="toggle-two">
<script>
  $(function() {
    $('#toggle-two').bootstrapToggle({
      on: 'Enabled',
      off: 'Disabled'
    });
  })
</script>
```

Name      |Type       |Default    |Description                 |
----------|-----------|----------|----------------------------|
`on`      |string/html|"On"      |Text of the on toggle
`off`     |string/html|"Off"     |Text of the off toggle
`size`    |string     |"normal"  |Size of the toggle. Possible values are: `large`, `normal`, `small`, `mini`.
`onstyle` |string     |"primary" |Style of the on toggle. Possible values are: `primary`,`secondary`,`success`,`danger`,`warning`,`info`,`light`,`dark`
`offstyle`|string     |"light"   |Style of the off toggle. Possible values are: `primary`,`secondary`,`success`,`danger`,`warning`,`info`,`light`,`dark`
`style`   |string     |           |Appends the value to the class attribute of the toggle. This can be used to apply custom styles. Refer to Custom Styles for reference.
`width`   |integer    |*null*     |Sets the width of the toggle. if set to *null*, width will be auto-calculated.
`height`  |integer    |*null*     |Sets the height of the toggle. if set to *null*, height will be auto-calculated.

## Methods
Methods can be used to control toggles directly.

```html
<input id="toggle-demo" type="checkbox" data-toggle="toggle">
```

Method     |Example                                         |Description
-----------|------------------------------------------------|------------------------------------------
initialize | `$('#toggle-demo').bootstrapToggle()`          |Initializes the toggle plugin with options
destroy    | `$('#toggle-demo').bootstrapToggle('destroy')` |Destroys the toggle
on         | `$('#toggle-demo').bootstrapToggle('on')`      |Sets the toggle to 'On' state
off        | `$('#toggle-demo').bootstrapToggle('off')`     |Sets the toggle to 'Off' state
toggle     | `$('#toggle-demo').bootstrapToggle('toggle')`  |Toggles the state of the toggle on/off
enable     | `$('#toggle-demo').bootstrapToggle('enable')`  |Enables the toggle
disable    | `$('#toggle-demo').bootstrapToggle('disable')` |Disables the toggle

# Events

## Event Propagation
Note All events are propagated to and from input element to the toggle.

You should listen to events from the `<input type="checkbox">` directly rather than look for custom events.

```html
<input id="toggle-event" type="checkbox" data-toggle="toggle">
<div id="console-event"></div>
<script>
  $(function() {
    $('#toggle-event').change(function() {
      $('#console-event').html('Toggle: ' + $(this).prop('checked'))
    })
  })
</script>
```

## Stopping Event Propagation
Passing `true` to the on/off methods will enable the silent option to prevent the control from propagating the change event in
cases where you want to update the controls on/off state, but do not want to fire the onChange event.

```html
<input id="toggle-silent" type="checkbox" data-toggle="toggle">
<button class="btn btn-success" onclick="toggleApiOnSilent()" >On by API (silent)</button>
<button class="btn btn-success" onclick="toggleApiOffSilent()">Off by API (silent)</button>
<button class="btn btn-warning" onclick="toggleApiOnNotSilent()">On by API (not silent)</button>
<button class="btn btn-warning" onclick="toggleApiOffNotSilent()">On by API (not silent)</button>
<script>
  function toggleApiOnSilent() {
    $('#toggle-silent').bootstrapToggle('on', true);
  }
  function toggleApiOffSilent() {
    $('#toggle-silent').bootstrapToggle('off', true);
  }
  function toggleApiOnNotSilent() {
    $('#toggle-silent').bootstrapToggle('on');
  }
  function toggleApiOffNotSilent() {
    $('#toggle-silent').bootstrapToggle('off');
  }
</script>
```

## API vs Input
This also means that using the API or Input to trigger events will work both ways.

```html
<input id="toggle-trigger" type="checkbox" data-toggle="toggle">
<button class="btn btn-success" onclick="toggleApiOn()" >On by API</button>
<button class="btn btn-danger"  onclick="toggleApiOff()">Off by API</button>
<button class="btn btn-success" onclick="toggleInpOn()" >On by Input</button>
<button class="btn btn-danger"  onclick="toggleInpOff()">Off by Input</button>
<script>
  function toggleApiOn() {
    $('#toggle-trigger').bootstrapToggle('on')
  }
  function toggleApiOff() {
    $('#toggle-trigger').bootstrapToggle('off')  
  }
  function toggleInpOn() {
    $('#toggle-trigger').prop('checked', true).change()
  }
  function toggleInpOff() {
    $('#toggle-trigger').prop('checked', false).change()
  }
</script>
```
