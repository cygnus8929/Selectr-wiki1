Selectr comes with a bunch of public methods for you to access Selectr programmatically. Just call the method after instantiating Selectr, like so:

```javascript
var selector = new Selectr(selectBox);

selector.methodName();
```

---

### setValue(`value`)
#### Usage: `single`, `multi`

Set the selected value(s) of the select box. The `value` parameter accepts either a string or an array of strings for multi selects.

```javascript
// for single or multi selects
selector.setValue('value-1');

// or for multi selects only
selector.setValue(['value-1', 'value-2', 'value-3']);
```

NOTE: if you pass a value that is already selected it will be deselected.

---

### getValue(`toObject, toJson`)
#### Usage: `single`, `multi`

Get the current selected value(s) of the select box.

The function will return a single string for a single select box or an array or strings for a multi select.

```javascript
// for single selects
selector.getValue(); // 'value-1'

// or for multi selects
selector.getValue(); // ['value-1', 'value-2', 'value-3']
```

The optional parameter `toObject` will return the selected values as an object, and the optional `toJson` parameter will return a formated JSON string of the object.

```javascript
// as object
selector.getValue(true); // {values:[{value:"value-1",text:"Value 1"},{value:"value-2",text:"Value 2"},{value:"value-3",text:"Value 3"}]}"

// as JSON
selector.getValue(true, true); // "{"values":[{"value":"value-1","text":"Value 1"},{"value":"value-2","text":"Value 2"},{"value":"value-3","text":"Value 3"}]}" 

```

---

### search(`query`)
#### Usage: `single`, `multi`

Search the available options for a string. The `query` parameter accepts a string and returns an `object` of matched options.

```javascript
// search for the string 'foo'
selector.search('foo');
```

---

### addOption(`data`)
#### Usage: `single, multi`

Dynamically add a new options. The function accepts an object or array of objects as it's first parameter. These objects can contain any properties, but must contain the default `value` and `text` properties.

### Add a single option
```javascript
selector.addOption({
    value: "some-value",
    text: "Some Text"
});
```

### Add multiple options
```javascript
selector.addOption([
    {
        value: "some-value-1",
        text: "Some Text 1"
    },
    {
        value: "some-value-2",
        text: "Some Text 2"
    },
    {
        value: "some-value-3",
        text: "Some Text 4"
    }
]);
```

---

### serialize(`toJson`)
#### Usage: `single, multi`

Returns a serialized object of all options. Note that both spellings of the function are accepted, i.e. `serialize` or `serialise`

```javascript
selector.serialize();
```

You can pass an optional boolean parameter to return a JSON string if required.

```javascript
selector.serialize(true);
```

---

### open()
#### Usage: `single`, `multi`

Opens the dropdown.

```javascript
selector.open();
```

---

### close()
#### Usage: `single`, `multi`

Closes the dropdown.

```javascript
selector.close();
```

---

### toggle()
#### Usage: `single`, `multi`

Toggle the dropdown.

```javascript
selector.toggle();
```

---

### clear()
#### Usage: `single`, `multi`

Clear all selected options.

```javascript
selector.clear();
```

---

### reset()
#### Usage: `single`, `multi`

Reset the instance back to it's initial state. Any selected options defined by the `selectedValue` option or in the object passed with the `data` option will be selected again.

This method is called automatically when reseting the parent form.

```javascript
selector.reset();
```

---

### disable()
#### Usage: `single`, `multi`

Disable the current instance. The element will be visible, but inaccessable.

```javascript
selector.disable();
```

As with native select boxes, a disabled instance will not receive focus, tabbing navigation will be skipped and the value(s) will not be submitted with the parent form. [More info](https://www.w3.org/TR/html401/interact/forms.html#disabled).

You can, however, pass an optional `boolean` to this method to disable the instance, but enable the value to be submitted with the parent form.

```javascript
selector.disable(true); // the instance's value(s) will be submitted
```

---

### enable()
#### Usage: `single`, `multi`

Enable the current instance.

```javascript
selector.enable();
```

---