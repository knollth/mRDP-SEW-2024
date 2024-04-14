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
---
## JSON Datenformat

JSON (JavaScript Object Notation) ist ein Datenformat, das hauptsächlich für den Datenaustausch zwischen Anwendungen verwendet wird. Es ist einfach zu lesen und zu schreiben, sowohl für Menschen als auch für Maschinen.

JSON-Daten werden in Schlüssel/Wert-Paaren geschrieben. Schlüssel und Wert werden durch einen Doppelpunkt in der Mitte getrennt, wobei sich der Schlüssel links und der Wert rechts befindet. Unterschiedliche Schlüssel/Wert-Paare werden durch ein Komma (,) getrennt. Arrays werden mit eckigen Klammern ([ ]) dargestellt. Elemente innerhalb von Arrays werden mit einem Komma getrennt.

## Implementierung