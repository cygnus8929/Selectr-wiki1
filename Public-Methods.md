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

### search(`query`, `anchor`)
#### Usage: `single`, `multi`

Search the available options for a string.  Search matches against the display text for each option, _not_ option values.  The results are returned as an array of objects.

The `query` parameter accepts a string to search for.  (If you leave the `query` argument empty, `search()` will use the value of the select box's search input.)

The `anchor` parameter is boolean (true/false) and toggles searching from the beginning of display text (e.g., searching for "foo" would match "foobar" but not "barfoo").  The default behavior is to match anywhere in the string.

```javascript
// search for the string 'foo' anywhere in option text
selector.search('foo');

// search for the string 'foo', but only when it is at the beginning of the option text
selector.search('foo', true);

// trigger a search using the value of the selector's search input (if any)
selector.search();
```

Update by [@adrian-enspired](https://github.com/adrian-enspired)

---

---

### add(`data`, `duplicateCheck`)
#### Usage: `single, multi`

Dynamically add a new options. The function accepts an object or array of objects as it's first parameter. These objects can contain any properties, but must contain the default `value` and `text` properties.

The `duplicateCheck` argument is a boolean and when set to `true` will check to see if any of the new values passed in the first argument already exist. If they do the method will skip over them.

### Add a single option
```javascript
selector.add({
    value: "some-value",
    text: "Some Text"
});
```

### Add multiple options
```javascript
selector.add([
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

>NOTE: Prior to `v2.3.4`, this method was called `addOption`. Make sure you update your code to reflect the API changes if you're using `v2.3.4` or above.

>NOTE: If you have a fairly large dataset present (100s or 1000s) and are adding another fairly large dataset, then calling this method with the `checkDuplicate` parameter set to `true` can be CPU intensive.

---

### remove(`data`)
#### Usage: `single, multi`

Remove an option or options.

Options can be removed via their indexes or their values. To remove an option via it's index you must pass an `integer` and to remove an option via it's value you must pass a `string`. The `data` parameter can be either an `integer`, a `string` or an `array` of strings / integers.

#### Examples

```javascript
// Remove the first option via it's index
selector.remove(0);

// Remove an option via it's value
selector.remove("value-3");

// Remove the first, third and fifth option via their indexes
selector.remove([0,2,4]);

// Remove multiple options via both indexes and values
selector.remove([0, "value-2", "value-4", 8, 12]);

```

Be careful passing numbers as the wrong option could be removed. If your values are numbers and you're removing via a value than make sure to pass a `string` rather than an `integer`:

```html
<select>
    <option value="1">Value 1</option>
    <option value="2">Value 2</option>
    <option value="3">Value 3</option>
    <option value="4">Value 4</option>
</select>
```

```javascript
// Removes the third option instead of the second
selector.remove(2);

// Correctly removes the second option
selector.remove("2");
```

---

### removeAll()
#### Usage: `single, multi`

Remove all options.

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