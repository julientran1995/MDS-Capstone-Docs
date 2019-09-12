# Single Sign On Data

Single Sign On (SSO) data records all SSO users's remote interaction with UQ internet services (library, blackboard, etc...) including user's geolocation and unique identifier, timestamp or the interaction and types of service.

* *How is this file organised? By certain timeframe or services?*

## Example

      {"_source":{"@timestamp":"2018-10-07T15:05:25.791Z","source":{"geoip":{"city_name":"Middle Park","country_name":"Australia","location":{"lat":-27.556,"lon":152.9222},"region_code":"QLD"}},"user":{"service":"urn:federation:MicrosoftOnline","uid":"20a9a212db45b2c267c67337086ab56f"}}}
      {"_source":{"@timestamp":"2018-10-07T15:05:27.568Z","source":{"geoip":{"city_name":"Saint Lucia","country_name":"Australia","location":{"lat":-27.5,"lon":153},"region_code":"QLD"}},"user":{"service":"portal.my.uq.edu.au","uid":"cacf7f565249a989b50ebc8e6a2a027f"}}}
      {"_source":{"@timestamp":"2018-10-07T15:05:26.399Z","source":{"geoip":{"city_name":"Cherrybrook","country_name":"Australia","location":{"lat":-33.722,"lon":151.0461},"region_code":"NSW"}},"user":{"service":"sso.app.uq.edu.au","uid":"07aee79bc2db6a8574137b387bb191f9"}}}
      {"_source":{"@timestamp":"2018-10-07T15:05:30.736Z","source":{"geoip":{"city_name":"Brisbane","country_name":"Australia","location":{"lat":-27.4595,"lon":153.0638},"region_code":"QLD"}},"user":{"service":"portal.my.uq.edu.au","uid":"af40d297e94f58a568c1f2cff518f5d6"}}}
      {"_source":{"@timestamp":"2018-10-07T15:05:38.413Z","source":{"geoip":{"city_name":"St Lucia","country_name":"Australia","location":"-27.4989228, 153.0137409"}},"user":{"service":"sso","uid":"551ac6b6ba6f368c8697e091dfec64e6"}}}



## Meta data

* File Type: JSONL document of JSON objects
* Size: roughly 1.2GB per day


## Data Structure

      source    # top level
          timestamp     # Y-M-D H-M-S
          source    # geo-location source
              geoip     # IP address
                  city_name     # suburb/city
                  country_name
                  location
                      lat     # latitude
                      lon     # longitude
                  region_code     # state
          user    # user details
              service     # UQ Internet Services
              uid     #unique user id
