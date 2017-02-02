Stages
######

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/stages/``

Response
========
  
.. code-block:: json

  {
    "links": {
        "self": "https://www.flightclub.io:8443/FlightClub/api/v1/stages/"
    },
    "data": [
      {
        "id": 1,
        "name": "Falcon 1 Stage 1",
        "radius": 0.83,
        "length": 15,
        "dryMass": 1296,
        "fuelCapacity": 21092,
        "maxAccel": 6,
        "propMass": 21092,
        "minimumFuel": 100,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/stages/1/"
        }
      }
    ]
  }
  
Response Overview
=================
  
+--------------+--------------------+---------------------------------------------------+
| Element      | Attribute          | Explanation                                       |
+--------------+--------------------+---------------------------------------------------+
| data         | id                 | Incremental 1-based identifier                    |
|              +--------------------+---------------------------------------------------+
|              | name               | Plain text description                            |
|              +--------------------+---------------------------------------------------+
|              | radius             | Radius (m)                                        |
|              +--------------------+---------------------------------------------------+
|              | length             | Length (m)                                        |
|              +--------------------+---------------------------------------------------+
|              | dryMass            | Un-fuelled mass of stage (without engines) (kg)   |
|              +--------------------+---------------------------------------------------+
|              | fuelCapacity       | Maximum possible mass of fuel (kg)                |
|              +--------------------+---------------------------------------------------+
|              | maxAccel           | Maximum capable acceleration (g's)                |
|              +--------------------+---------------------------------------------------+
|              | propMass           | Actual mass of fuel. Cannot exceed `fuelCapacity` |
|              +--------------------+---------------------------------------------------+
|              | minimumFuel        | Mass of fuel at which engines cut off             |
|              +--------------------+---------------------------------------------------+
|              | **links**          |                                                   |
+--------------+--------------------+---------------------------------------------------+
| links        | self               | The URL that returns this element                 |
+--------------+--------------------+---------------------------------------------------+