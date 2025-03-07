# REST API: POST database profiles

Als je een profiel wilt aanmaken, dien je een HTTP POST request te sturen
naar de volgende URL.

`https://api.copernica.com/v3/database/$id/profiles?access_token=xxxx`

De code `$id` moet je vervangen door de numerieke identifier of de naam van de 
database waar je het profiel in wilt opslaan. De veldwaardes van het profiel
kun je in de body van het HTTP request plaatsen.

Zorg ervoor dat je hier een POST request stuurt en geen PUT request. 
Hoewel deze vaak niet verschillen zou je in dit geval een methode 
aanroepen om meerdere profielen te bewerken, zie de 
[methode om meerdere profielen te bewerken](rest-put-database-profiles).

## Beschikbare parameters

Naast de parameters die je aan de URL meegeeft, moet je ook body data aan het
POST request toevoegen. In de body van het verzoek kun je twee optionele arrays meegeven: 
'fields' bevat de velden voor het profiel en 'interests' de interesses. 
De interesses kunnen als een associatieve array ('voetbal' => 1, 'honkbal' => 0) 
of als een lijst ('voetbal') meegegeven worden. De profielvelden moeten 
meegegeven worden als associatieve array.

Let op! Hier wordt de body data op een andere manier meegegeven dan in 
[versie 1](../restv1/rest-post-database-profiles) van de API.

## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen:

```php
// vereiste scripts
require_once('copernica_rest_api.php');

// verander dit naar je access token
$api = new CopernicaRestAPI("your-access-token", 3);

// de velden voor het nieuwe profiel
$fields = array(
    'voornaam'      =>  'John',
    'achternaam'    =>  'Doe',
    'email'         =>  'johndoe@example.com'
);

// de interesses voor het nieuwe profiel
$interests = array(
    'voetbal'  => 1,
    'honkbal'  => 0
);

// de interesses kun je ook op deze manier specificeren
$interests = array("voetbal");

// de velden en interesses vormen samen de data voor het verzoek
$data = array(
    'fields'    => $fields,
    'interests' => $interests
);

// voer het verzoek uit
$api->post("database/{$databaseID}/profiles", $data);

// retourneer de ID van het aangemaakte profiel als het verzoek succesvol was
```

Dit voorbeeld vereist de [REST API klasse](rest-php).

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [GET database profiles](rest-get-database-profiles)
* [PUT profile fields](rest-put-profile-fields)
* [DELETE profile](rest-delete-profile)
* [PUT profile fields](rest-put-profile-fields)
* [POST profile interests](rest-post-profile-interests)
