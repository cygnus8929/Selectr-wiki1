Sometimes you require a select box's options be loaded dynamically rather than defined in the markup. This is simple with Selectr.

First, initialise Selectr as normal on your select box (can be empty):

```javascript
var selector = new Selectr("#mySelectBox");
```

You can then utilise the `addOption` method to load options in to the container:

```javascript
function fetchData() {
  var request = new XMLHttpRequest();

  request.open("GET", "https://domain.com/ajax/fetch", true);

  request.onload = function() {

    if (request.status >= 200 && request.status < 400) {
      // Parse the response JSON to an object
      var data = JSON.parse(request.responseText);

      // Pass the object to the 'addOption' methed
      selector.addOption(data);
    }
  };

  request.send();
}
```

You can then call the function whenever required, for example, when Selectr has loaded:
```javascript
// Listen for the init event and load the data
selector.on("selectr.init", function() {
  fetchData();
});
```

If you have `pagination` active then Selectr will load all options into it's cache, but will only insert the maximum amount required into the dropdown.