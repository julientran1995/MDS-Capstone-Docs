# Wireless Location Data

Wireless Location data records on-campus's users's interaction with UQ's internet services, including their location (specific location on campus may be recorded), network used, timestamp and user/client type (may not always be recorded).

* *How to handle analytics on data with missing client type or building?*
* *How is this file organised? By certain timeframe or services?*

## Example

      {"_source":{"@timestamp":"2018-10-07T06:59:07.148Z","source":{"geoip":{"location":"-27.494099280701732, 153.01202645423731"}},"user":{"service":"","uid":""}}}
      {"_source":{"@timestamp":"2018-10-07T06:59:09.164Z","source":{"geoip":{"location":"-27.500020889405832, 153.01316354792388"},"location":{"building_comp":"50: Hawken Engineering"}},"user":{"service":"UQ","uid":"184d4a039fc35f5d9a130321dde461a8"},"wireless":{"clientType":"Student"}}}
      {"_source":{"@timestamp":"2018-10-07T06:59:09.214Z","source":{"geoip":{"location":"-27.497107045598334, 153.01483571368803"}},"user":{"service":"eduroam","uid":"178cd57bb81d301537b9c26463e06c2f"},"wireless":{"clientType":"EduExternal"}}}
      {"_source":{"@timestamp":"2018-10-07T06:59:09.238Z","source":{"geoip":{"location":"-27.498909714010093, 153.01365968134354"},"location":{"building_comp":"42: Prentice"}},"user":{"service":"InfraOneX","uid":"6343f6cce0b55a06efba3d3251d154fd"},"wireless":{"clientType":"Infrastructure"}}}
      {"_source":{"@timestamp":"2018-10-07T06:59:09.235Z","source":{"geoip":{"location":"-27.49438405523813, 153.01516208100458"},"location":{"building_comp":"29: Tennis Centre"}},"user":{"service":"UQ","uid":"2ada3c824e7eb2fb7e008cb79a442034"},"wireless":{"clientType":"CommercialVisitor"}}}



## Meta data

* File Type: JSONL document of JSON objects
* Size: roughly 7.8GB per day


## Data Structure

      source    # top level
          timestamp     # Y-M-D H-M-S
          source    # geo-location source
              geoip     # IP address
                  location
                      lat     # latitude
                      lon     # longitude
              location    # campus location or the wireless point
                  building_comp   #building number and name
          user    # user details
              service     # UQ Internet Services
              uid     #unique user id
          wireless    # wireless network details
              clientType    #types of client logged on
