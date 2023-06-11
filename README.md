# js_AjaxClient
AjaxClient is a general purpose client side Javascript API class which makes xhr requests to backend or url and then relays response to front end. It is capable of both GET and POST operations.

# Documentation:

## Create A New Object of AjaxClient

### let client = new AjaxClient(boolean)

1. boolean indicates whether to convert inData (data to send to backend/url during POST operation) to urlencoded string before sending.
2. urlencoded string would be like: param1="something"&param2="something"&param3="something". AjaxClient will send content via HTTP protocol thru the url. 
3. boolean will be false if no input is given.

## GET and POST

### ajaxGet(url, callback)

1. This function fetches data from the target URL by making a xhr GET request.
2. parameter "url" is the target URL. "url" must be a string: url="path/to/file". Can be a internet URL, relative file path to a JSON file or a PHP file etc.
3. this function passes the result of the request to callback function via the callback function given via the parameter "callback".
4. "callback" must be a function that accepts a single (ONE) paremeter. Such as: function func (resData){//something...}.

### ajaxPost(url, inData, callback)

1. This function sends "inData" to the target URL and parses response to the callback function.
2. parameter "url" is the target URL. "url" must be a string: url="path/to/file". Can be a internet URL, relative file path to a JSON file or a PHP file etc.
3. parameter "inData" must be a Javascript object like {data1: "something", data2: "something"}. Wrap data you want to send in ONE object.
4. this function passes the result of the request to callback function via the callback function given via the parameter "callback".
5. "callback" must be a function that accepts a single (ONE) paremeter. Such as: function func (resData){//something...}.
6. "inData" would be sent as urlencoded string like : param1="something"&param2="something"&param3="something" if obj2urlencode is set to true while AjaxClient was instantiated.

## Examples

### Example 1: ajaxGet from URL

```
import {AjaxClient} from "../jslib/AjaxClient.js";

//obj2urlencode is false by default
const client = new AjaxClient();

//fetch the geo location information based on user's IP address
//the target URL is an FREE web api which returns geo location based on user's IP address
client.ajaxGet("https://ipapi.co/json/", printGeoInfo);

function printGeoInfo(geoInfo){
  //prints response on the console
  console.log(geoInfo);
}
```

### Example 2: ajaxPost to backend and execute PHP script

```
import {AjaxClient} from "../jslib/AjaxClient.js";

let loginData = {
  userName: "user101",
  password: "123456"
};

//convert loginData to urlencoded string before sending
const client = new AjaxClient(true);

//process_login.php receives data from loginData and accesses database to authenticate login information
//response will indicate whether login is successful
//you could reference: https://github.com/yang530/7seg_display/blob/main/php/process_login.php for an example of process_login.php file 
client.ajaxGet("php/process_login.php", loginData, printResponse);

function printResponse(response){
  //prints response on the console
  console.log(response);
}

```


