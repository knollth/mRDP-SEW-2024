# JSON

Erkläre das JSON Datenformat. Wie können JSON Daten in einem C# Programm eingelesen werden?

Über den Google geocode Webservice soll ermittelt werden in welchem Land sich eine Stadt befindet. Der JSON Response sieht wie folgt aus. Implementiere ein C# Programm das die Aufgabenstellung löst.

```
{
   "results" : [
      {
         "address_components" : [
            {
               "long_name" : "Toronto",
               "short_name" : "Toronto",
               "types" : [ "locality", "political" ]
            },
            {
               "long_name" : "Toronto Division",
               "short_name" : "Toronto Division",
               "types" : [ "administrative_area_level_2", "political" ]
            },
            {
               "long_name" : "Ontario",
               "short_name" : "ON",
               "types" : [ "administrative_area_level_1", "political" ]
            },
            {
               "long_name" : "Canada",
               "short_name" : "CA",
               "types" : [ "country", "political" ]
            }
         ],
         "formatted_address" : "Toronto, ON, Canada",
         "geometry" : {
            "location" : {
               "lat" : 46.452469,
               "lng" : -63.379967
            },
         }
      },
   ],
   "status" : "OK"
}
```