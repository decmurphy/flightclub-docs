Engines
#######

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/engines/``

Response
========
  
.. code-block:: json

    {
      "links": {
        "self": "https://www.flightclub.io:8443/FlightClub/api/v1/engines/"
      },
      "data": [
        {
          "id": 1,
          "name": "BE3",
          "mass": 500.0,
          "ispSL": 450.0,
          "ispVac": 450.0,
          "thrustSL": 490000.0,
          "thrustVac": 490000.0,
          "throttleCapability": 0.2,
          "links": {
            "self": "https://www.flightclub.io:8443/FlightClub/api/v1/engines/1/"
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
|              | mass               | Mass of engine (kg)                               |
|              +--------------------+---------------------------------------------------+
|              | ispSL              | Specific Impulse at sea-level (seconds)           |
|              +--------------------+---------------------------------------------------+
|              | ispVac             | Specific Impulse in vacuum (seconds)              |
|              +--------------------+---------------------------------------------------+
|              | thrustSL           | Thrust at sea-level (Newtons)                     |
|              +--------------------+---------------------------------------------------+
|              | thrustVac          | Thrust in vacuum (Newtons)                        |
|              +--------------------+---------------------------------------------------+
|              | throttleCapability | Floating point number indicating deepest throttle |
|              |                    | the engine is capable of (e.g 0.4 = 40%)          |
|              +--------------------+---------------------------------------------------+
|              | **links**          |                                                   |
+--------------+--------------------+---------------------------------------------------+
| links        | self               | The URL that returns this element                 |
+--------------+--------------------+---------------------------------------------------+