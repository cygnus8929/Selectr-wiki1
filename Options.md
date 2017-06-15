## multiple `[bool]`
Use to programmatically set the select box to a multi select box.

---

## searchable `[bool]`
#### Default: `true`
#### Usage: `single`, `multi`

Allow the user to search through the available options. This option is enabled by default.

Searches are case-insensitive and are matched from the first character of the option's text.

---

## allowDeselect `[string]`
#### Default: `false`
#### Usage: `single`

Allow deselecting of a selected option in a `select-one` select box.

---

## clearable `[bool]`
#### Default: `false`
#### Usage: `single`, `multi`

Allow the user to clear the select box.

Will not work on `select-one` select boxes with the `allowDeselect` option disabled.

---

## width `[int, string]`
#### Default: `auto`
#### Usage: `single`, `multi`

Programatically set a custom width of the select box. The default setting `auto` will just fit the container to the parent element's width as with standard select boxes.

---

## placeholder `[string]`
#### Default: `null`
#### Usage: `single`, `multi`

Programatically set a custom placeholder.

This will override the HTML placeholder attribute if one exists.

---

## maxSelections `[int]`
#### Default: `null`
#### Usage: `multi`

Limit the number of selections a user can make. Multi-select only.

---

## taggable `[bool]` <small>(v2.1.0 and above)</small>
#### Default: `false`
#### Usage: `multi`

Enable the tagging feature.

---

## tagSeperators `[array]` <small>(v2.1.0 and above)</small>

Define the seperators used when using the `taggable` option. Pass an array of seperators like so:

```javascript
var selector = new Selectr("#mySelect", {
	taggable: true,
    tagSeperators: [",", "|"]
});
```

The default seperators are the `comma` and `enter` keys.

---


## data `[array]`
#### Default: `undefined`
#### Usage: `single`, `multi`

Programatically define a dataset for Selectr to use.

```markup
<select id="mySelect"></select>
```

```javascript
new Selectr(mySelectBox, {
	data: [
      { value: 'foo', text: 'Foo' },
      { value: 'bar', text: 'Bar' },
      { value: 'baz', text: 'Baz' },
    ]
});
```

You can also pass the selected and disabled properties, like so:

```javascript
new Selectr(mySelectBox, {
	data: [
        { value: 'value-1', text: 'Value 1' },
        { value: 'value-2', text: 'Value 2', selected: true },
        { value: 'value-3', text: 'Value 3', disabled: true },
        { value: 'value-4', text: 'Value 4' },
        { value: 'value-5', text: 'Value 5', selected: true },
        { value: 'value-6', text: 'Value 6' },
        { value: 'value-7', text: 'Value 7', disabled: true },
        { value: 'value-8', text: 'Value 8' },
        { value: 'value-9', text: 'Value 9' },
        { value: 'value-10', text: 'Value 10' }
    ],
    multiple: true
});
```

You can also group the data to emulate the `HTMLOptGroupElement`:

```javascript
new Selectr(mySelectBox, {
	data: [
          {
              text: "Group 1",
              children: [
                  {
                      value: "value-1",
                      text: "Value 1"
                  },
                  {
                      value: "value-2",
                      text: "Value 2"
                  },
                  {
                      value: "value-3",
                      text: "Value 3"
                  },
                  {
                      value: "value-4",
                      text: "Value 4"
                  }
              ]
          },
          {
              text: "Group 2",
              children: [
                  {
                      value: "value-5",
                      text: "Value 5"
                  },
                  {
                      value: "value-6",
                      text: "Value 6"
                  },
                  {
                      value: "value-7",
                      text: "Value 7"
                  },
                  {
                      value: "value-8",
                      text: "Value 8"
                  }
              ]
          }
    ]
});
```

---

## renderOption `[func]`
#### Default: `undefined`
#### Usage: `single`, `multi`

Allows custom formating of the available options.

The function takes the individual HTMLOptionElement as the first parameter and should return the formatted template required.

```html
<select id="mySelectBox">
	<option value="value-1" data-src="avatar1.jpg"> Value 1 </option>
	<option value="value-2" data-src="avatar2.jpg"> Value 2 </option>
	<option value="value-3" data-src="avatar3.jpg"> Value 3 </option>
	<option value="value-4" data-src="avatar4.jpg"> Value 4 </option>
	<option value="value-5" data-src="avatar5.jpg"> Value 5 </option>
	<option value="value-6" data-src="avatar6.jpg"> Value 6 </option>
	<option value="value-7" data-src="avatar7.jpg"> Value 7 </option>
	<option value="value-8" data-src="avatar8.jpg"> Value 8 </option>
</select>
```

```javascript
new Selectr(mySelectBox, {
	renderOption: myRenderFunction
});

function myRenderFunction(option) {
    var template = [
      "<div class='my-template'><img src='", option.dataset.src, "'><span>",
    		option.textContent,
      "</span></div>"
    ];
    return template.join('');
}
```

As of `v2.2.0` you can also use this option if you define your options via the `data` option:
 
```javascript
new Selectr(mySelectBox, {
	data: [{
		value: "value-1",
		text: "Value 1",
		avatar: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/86186/avatar1.jpg"
	}, {
		value: "value-2",
		text: "Value 2",
		disabled: true,
		avatar: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/86186/avatar2.jpg"
	}, {
		value: "value-3",
		text: "Value 3",
		avatar: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/86186/avatar3.jpg"
	}, {
		value: "value-4",
		text: "Value 4",
		avatar: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/86186/avatar4.jpg"
	}],
	renderOption: myDataRenderFunction
});
```

Your function should then utilise the first parameter to access the object:
```javascript
function myDataRenderFunction(data) {
    var template = [
      "<div class='my-template'><img src='", data.avatar, "'><span>",
      	data.text,
      "</span></div>"
    ];
    return template.join('');
}
```

---

## renderSelection `[func]`
#### Default: `null`
#### Usage: `single`, `multi`

Similar to renderOptions, this allows custom formating of the selected option or tag.

The function takes the individual HTMLOptionElement as the first parameter and should return the formatted template required.

As of `v2.2.0` you can also use this option if you define your options via the `data` option. (See [`renderOption`](#renderoption-func))

```html
<select id="mySelectBox">
	<option value="value-1" data-src="avatar1.jpg"> Value 1 </option>
	<option value="value-2" data-src="avatar2.jpg"> Value 2 </option>
	<option value="value-3" data-src="avatar3.jpg"> Value 3 </option>
	<option value="value-4" data-src="avatar4.jpg"> Value 4 </option>
	<option value="value-5" data-src="avatar5.jpg"> Value 5 </option>
	<option value="value-6" data-src="avatar6.jpg"> Value 6 </option>
	<option value="value-7" data-src="avatar7.jpg"> Value 7 </option>
	<option value="value-8" data-src="avatar8.jpg"> Value 8 </option>
</select>
```

```javascript
new Selectr(mySelectBox, {
	renderSelection: myRenderFunction
});

function myRenderFunction(option) {
	var template = ['<div class="my-template"><img src="', option.getAttribute('data-src'), '"><span>', option.textContent.trim(), '</span></div>'];
	return template.join('');
}
```

---

## pagination `[int]`
#### Default: `25`
#### Usage: `single`, `multi`

Allows for the 'lazy-loading' of large datasets. Scrolling or navigating to the bottom of the dropdown will load the next set of items.

Previously this was only possible with options supplied via the `data` options, but, as of `v2.2.0`, pagination can be applied to options already defined in the DOM.

```javascript
new Selectr(mySelectBox, {
	pagination: 25,
});
```

---

## nativeDropdown `[bool]` <small>(v2.1.0 and above)</small>
#### Default: `false`
#### Usage: `single`

Allows the use of the native dropdown instead of Selectr's custom dropdown list.

> Note that this option defaults to `true` on mobile devices.

---

## closeOnScroll `[bool]`
#### Default: `false`
#### Usage: `single`, `multi`

When set to `true` the dropsdown will close during scrolling.

---

## sortSelected `[mixed]`
#### Default: `false`
#### Usage: `multi`

Orders the selected options (tags) by their values.

If you want the tags ordered by their text rather than their values, you can set the `sortSelected` option to  `"text"`

---

## customClass `[string]`
#### Default: `undefined`
#### Usage: `single, multi`

Apply a custom className to the container to better control styling of individual instances.

```javascript
new Selectr(mySelectBox, {
	customClass: 'my-custom-class'
});
```