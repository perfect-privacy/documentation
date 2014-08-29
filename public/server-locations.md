# Perfect Privacy Public API: Server Locations
>Document version: **1.0**

## URL
https://www.perfect-privacy.com/api/serverlocations.json

## Server Location Object
Key             | Data Type                       | Notice                                            | Example
--------------- | ------------------------------- | ------------------------------------------------- | -----------------------
city            | string                          | city, english language                            | "London"
city_short      | string                          | 2-letter city short code                          | "lo"
country         | string                          | country, english language                         | "United Kingdom"
country_short   | string                          | 2-letter country short code (ISO 3166-1 alpha-2)  | "gb"
lati            | signed floating point (string)  | latitude                                          | "51.511214"
longi           | signed floating point (string)  | longitude                                         | "-0.119824"

## Example
```json
{
    "london1.perfect-privacy.com": {
        "city": "London",
        "city_short": "lo",
        "country": "United Kingdom",
        "country_short": "gb",
        "lati": "51.511214",
        "longi": "-0.119824"
    },
    "london2.perfect-privacy.com": {
        "city": "London",
        "city_short": "lo",
        "country": "United Kingdom",
        "country_short": "gb",
        "lati": "51.511214",
        "longi": "-0.119824"
    },
    ... more server locations ...
}
```
