Initialise Selctr as normal:

```javascript
var selector = new Selectr("select");
```

You can then utilise the `addOption` method to load options in the container:

```javascript
function fetchData() {
	var request = new XMLHttpRequest();

	request.open("GET", "https://domain.com/ajax/fetch", true);

	request.onload = function() {

		if (request.status >= 200 && request.status < 400) {
			// Parse the response JSON to and object
			var data = JSON.parse(request.responseText);

			// Pass the oject to the 'addOption' methed
			selector.addOption(data);
		}
	};

	request.send();
}
```

You call the function whenever required, or when Selectr is load:
```javascript
// Listen for the init event and load the data
selector.on("selectr.init", function() {
	fetchData();
});
```