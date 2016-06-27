LaunchVehicles
##############

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/launchvehicles/``

Response
========
  
.. code-block:: json

  {
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchvehicles/"
    },
    "data": [
      {
        "id": 7,
        "code": "NSH",
        "description": "New Shepard",
        "stages": 1,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchvehicles/7/"
        }
      },
      {
        "id": 6,
        "code": "FNH",
        "description": "Falcon Heavy",
        "stages": 3,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchvehicles/6/"
        }
      },
      {
        "id": 5,
        "code": "F92",
        "description": "Falcon 9v1.1 FT",
        "stages": 2,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/launchvehicles/5/"
        }
      }
    ]
  }
  
Response Overview
=================
  
+--------------+-------------+----------------------------------------------+
| Element      | Attribute   | Explanation                                  |
+--------------+-------------+----------------------------------------------+
| data         | id          | Incremental 1-based identifier               |
|              +-------------+----------------------------------------------+
|              | code        | Constant enum identifier                     |
|              +-------------+----------------------------------------------+
|              | description | Plain text description                       |
|              +-------------+----------------------------------------------+
|              | stages      | Number of stages in this vehicle             |
|              +-------------+----------------------------------------------+
|              | **links**   |                                              |
+--------------+-------------+----------------------------------------------+
| links        | self        | The URL that returns this element            |
+--------------+-------------+----------------------------------------------+