# REST API: PUT collection

Method to change the properties of a collection. This method can be used by 
sending an HTTP PUT request to the following URL:

`https://api.copernica.com/v3/collection/$id?access_token=xxxx`

The `$id` should be replaced with the ID of the collection that you want to 
edit.

## Available data

The following properties can be adjusted by placing their new values 
in the message body of the HTTP PUT command:

* **name**: the new name of the collection

## PHP example

The following PHP scripts demonstrates how to call the API method:

```php
// dependencies
require_once('copernica-rest-api.php');

// change this into your access token
$api = new CopernicaRestAPI("your-access-token", 3);

// data to be sent to the api
$data = array(
    'name'  =>  'new-collection-name'
);
    
// do the call
$api->put("collection/{$collectionID}", $data);
```

The example above requires the [CopernicaRestApi class](rest-php).

## More information

* [Overview of all API calls](rest-api)
* [GET database collections](rest-get-database-collections)
