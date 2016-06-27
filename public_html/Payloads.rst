Payloads
#################

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/payloads/``

Response
========
  
.. code-block:: json

  {
    "data": [
      {
        "id": 3,
        "code": "SATL",
        "description": "Satellite",
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/payloads/3/"
        }
      }
    ],
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/payloads/"
    }
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
|              | **links**   |                                              |
+--------------+-------------+----------------------------------------------+
| links        | self        | The URL that returns this element            |
+--------------+-------------+----------------------------------------------+