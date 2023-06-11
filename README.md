# js_AjaxClient
AjaxClient is general purpose client side API class which makes xhr requests to backend or url and then relays response to front end. It is capable of both GET and POST operations.

# Documentation:

## Create A New Object of AjaxClient

### let client = new AjaxClient(boolean)

1. boolean indicates whether to convert inData (data to send to backend during POST operation) to urlencoded string before sending.
2. urlencoded string would be like: param1="something"&param2="something"&param3="something". AjaxClient will send content via HTTP protocol thru the url. 
3. boolean will be false if no input is given.

