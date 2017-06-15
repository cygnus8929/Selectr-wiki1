## Install with bower

```
bower install mobius1-selectr --save
```

## Install with npm

```
npm install mobius1-selectr --save
```

## Manual Installation

Include the CSS file ...

```html
<link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/selectr/latest/selectr.min.css">
```

... and the JS file...

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/selectr/latest/selectr.min.js"></script>
```

CDN courtesy of [jsDelivr](http://www.jsdelivr.com/)

## Initialisation


#### HTML

Start with a standard select box you want to convert:

```html
<select id="mySelect">
	<option vlaue="value-1">Value 1</option>
	<option vlaue="value-2">Value 2</option>
	<option vlaue="value-3">Value 3</option>
	...
</select>
```

#### Javascript

You can then instantiate Selectr by passing a reference to your select box as the first parameter:

You can either pass a DOM node or a CSS3 selector string:

```javascript
new Selectr(document.getElementById('mySelect'));

// or 

new Selectr('#mySelect');
```

Selectr accepts a second parameter as an object with the options you want to set:

```javascript
new Selectr('#mySelect', {
    searchable: false,
    width: 300
});
```

You can view the available options [here](http://mobius.ovh/docs/selectr/pages/options-2).