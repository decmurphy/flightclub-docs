LaunchSites
###########

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/launchsites/``

Response
========
  
.. code-block:: json

  {
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchsites/"
    },
    "data": [
      {
        "id": 18,
        "code": "JIUQ",
        "description": "Jiuquan Satellite Launch Center",
        "country": "CH",
        "latitude": 40.9675,
        "longitude": 100.278611,
        "isPolar": false,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchsites/18/"
        }
      }
    ]
  }
  
Response Overview
=================

The launchsites will be returned ordered alphabetically by country, state
(if in the United States), and then description.
  
+--------------+-------------+----------------------------------------------+
| Element      | Attribute   | Explanation                                  |
+--------------+-------------+----------------------------------------------+
| data         | id          | Incremental 1-based identifier               |
|              +-------------+----------------------------------------------+
|              | code        | Constant enum identifier                     |
|              +-------------+----------------------------------------------+
|              | description | Plain text description                       |
|              +-------------+----------------------------------------------+
|              | country     | 2-letter code for country                    |
|              +-------------+----------------------------------------------+
|              | state       | (optional) 2-letter code for state if in USA |
|              +-------------+----------------------------------------------+
|              | latitude    | Launch site latitude                         |
|              +-------------+----------------------------------------------+
|              | longitude   | Launch site longitude                        |
|              +-------------+----------------------------------------------+
|              | **links**   |                                              |
+--------------+-------------+----------------------------------------------+
| links        | self        | The URL that returns this element            |
+--------------+-------------+----------------------------------------------+