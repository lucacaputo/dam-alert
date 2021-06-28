# DAM Alert

## Usage
1. import the script and css
    ```html
    <link rel="stylesheet" href="dam-alert.css">
    <script src="dam-alert.js">
    ```
2. trigger popups using
    ```javascript
    Alert.firePopup(options, event?)
    .then(response => {
        //response contains the result (confirm, deny, ecc...)
        console.log(response);
    })
    .catch(error => {
        //error occured
        console.log(error);
    });
    ```
      * every popup has a saparate state and once closed is removed completely from the DOM
      * the event parameter is optional, but if it is fired by user interaction either pass it to the function or call ```event.stopPropagation()``` before firing the popup
      * if the event is fired by the page (eg. ```window``` load event or ```document``` ready event) then you don't need to pass the event or stopping its propagation
      * requires lineawesome 1.3 if icons are used
      * the object returned after the alert dismiss looks like this:
        ```javascript
            {
                isConfirmed: boolean,
                isDenied: boolean,
                dismissMode: 'confirmButton' | 'denyButton' | 'backdrop'
            }
        ```

## Options

| property | default value | effect | required | type
| -------- | ------------- | ------ | -------- | -----
|```title``` | ```''``` | sets popup's title | yes | ```string```
|```text```| ```null```| sets popup's text | no | ```string```
| ```confirmButtonText``` | ```'Ok'``` | sets the confirm button text | no | ```string```
| ```showDenyButton```| ```false```| shows the deny button | no | ```boolean```
| ```denyButtonText```| ```'Cancella'```| sets text on the deny button | no | ```string```
| ```icon``` | ```null``` | sets the popup's icon | no | ```'success' \| 'warning' \| 'error' \| 'info'```
| ```customClass``` | ```null``` | adds a custom class to the popup outer wrapper | no | ```string```
| ```onOpen``` | ```null``` | function that fires after popup opening animation | no | ```() => void```
| ```onClose``` | ```null``` | function that fires after popup closing animation | no | ```() => void```