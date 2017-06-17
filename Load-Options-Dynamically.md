```javascript
var selector = new Selectr("select");

selector.on("selectr.init", function() {
	fetchData();
});

function fetchData() {
	var request = new XMLHttpRequest();

	request.open("GET", "https://s3-us-west-2.amazonaws.com/s.cdpn.io/86186/data.large.json", true);

	request.onload = function() {
		if (request.status >= 200 && request.status < 400) {
			selector.addOption(JSON.parse(request.responseText));
		}
	};

	request.send();
}
```