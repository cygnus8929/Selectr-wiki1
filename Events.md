Selectr fires it's own events which you can listen for by utilising the `.on()` method:

```javascript
var selector = new Selectr(mySelect);

selector.on('selectr.XXXX', function() {
	// Do something when selector.XXXX fires
});
```

# `selectr.init`
Fires when Selectr is fully rendered and ready for use.

```javascript
selector.on('selectr.init', function() {
	// Selectr is ready
});
```

# `selectr.select`
Fires when an option is selected. The `option` argument contains the HTMLSelectElement that was selected.

```javascript
selector.on('selectr.select', function(option) {
	
});
```

# `selectr.deselect`
Fires when an option is deselected. The `option` argument contains the HTMLSelectElement that was deselected.

```javascript
selector.on('selectr.deselect', function(option) {
	
});
```


# `selectr.change`
Fires when an option's state is changed. The `option` argument contains the HTMLSelectElement that was changed.

```javascript
selector.on('selectr.change', function(option) {
	
});
```

# `selectr.open`
Fires when the dropdown is opened.

```javascript
selector.on('selectr.open', function() {
	
});
```

# `selectr.close`
Fires when the dropdown is closed.

```javascript
selector.on('selectr.close', function() {
	
});
```

# `selectr.clear`
Fires when the options are cleared.

```javascript
selector.on('selectr.clear', function() {
	
});
```

# `selectr.reset`
Fires when the instance has been reset.

```javascript
selector.on('selectr.reset', function() {
	
});
```

# `selectr.paginate`
Fires when a new batch of options is loaded. Only available when the `data` option is used.


```javascript
selector.on('selectr.paginate', function(data) {

});
```

The `data` argument returns an `object` of the following format:

```javascript
	{
      items: // the number of options loaded (int)
      total: // total options (int)
      page: // current page number (int)
      pages: // total pages (int)
    }
```